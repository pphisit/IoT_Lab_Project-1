#include <ESP8266WiFi.h>
#include <PubSubClient.h>

#define WIFI_STA_NAME "P" //ชื่อ wifi
#define WIFI_STA_PASS "11223344A" //รหัส wifi
#define MQTT_SERVER "203.158.245.180" //Server Domain Name หรือ IP Address
#define MQTT_PORT 1883 //Port MQTT Broker

//ข้อมูลผู้ใช้ ที่ใช้กับ Server
#define MQTT_USERNAME "admincpe"
#define MQTT_PASSWORD "cpe2541"
#define MQTT_NAME "LED_ON_OFF"

//ชื่อ Topic
#define MQTT_TOPIC "switch_control"


WiFiClient client;
PubSubClient mqtt(client);

//กำหนด state ต่างๆ
const int CHECK_CONNECT = 0;
const int SWITCH_MESSAGE = 1;
const int ON = 2;
const int OFF = 3;
int switch1Pin = D2; // กำหนดหมายเลขขาที่ต่อสวิตช์ 1
int switch2Pin = D3; // กำหนดหมายเลขขาที่ต่อสวิตช์ 2

int state;

void setup()
{
    pinMode(switch1Pin, INPUT);
    pinMode(switch2Pin, INPUT);

    state = CHECK_CONNECT;
    Serial.begin(115200);

    WiFi.mode(WIFI_STA); //กำหนดเป็นโหมด Station (WIFI_STA)
    WiFi.begin(WIFI_STA_NAME, WIFI_STA_PASS); //กำหนดค่าเริ่มต้น WiFi

    //Connect WiFi
    Serial.println("Connecting to WiFi..");
    for(int i = 0; i<20; i++){
        Serial.print(".");
        delay(500);
    }
    if(WiFi.status() == WL_CONNECTED) {
        Serial.println("Connected to WiFi");
    }else{
        Serial.println("Fail to Connected WiFi");
    }

    //Connect MQTT Broker
    mqtt.setServer(MQTT_SERVER, MQTT_PORT); 
}

void loop()
{
 switch (state)
 {
 case CHECK_CONNECT: //check MQTT connected
    
        Serial.print("Attempting MQTT connection...");
        if(mqtt.connect(MQTT_NAME, MQTT_USERNAME, MQTT_PASSWORD))
        {
            Serial.println("MQTT Connected.");
            state = SWITCH_MESSAGE;
        }else{
            Serial.println("MQTT Fail Connected.");
            state = CHECK_CONNECT;
        }
    
    break;

 case SWITCH_MESSAGE: 
    //mqtt.connect(MQTT_NAME, MQTT_USERNAME, MQTT_PASSWORD);
    if(digitalRead(switch1Pin)==HIGH) // พิมพ์ ON เพื่อสั่งเปิด LED
    {
        while (digitalRead(switch1Pin)==HIGH)
        {
        }
        state = ON;
        
    }
    if(digitalRead(switch2Pin)== HIGH) // พิมพ์ OFF เพื่อสั่งปิด LED
    {
         while (digitalRead(switch2Pin)==HIGH)
        {
        }       
        state = OFF;
    }else{
        Serial.println("Waiting for Switch");
    }
    break;
 
 case ON:        
        mqtt.publish(MQTT_TOPIC, "ON");
        Serial.println("Success, Switch 1 ON");
        state = SWITCH_MESSAGE;
    break;
  case OFF:
        mqtt.publish(MQTT_TOPIC, "OFF");
        Serial.println("Success, Switch 2 OFF");
        state = SWITCH_MESSAGE;
    break;
}
}