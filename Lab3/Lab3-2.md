### 2.กดปุ่มที่1เพิ่มความเร็วมอเตอร์ และกดปุ่มที่2 ลดความเร็วมอเตอร์ ผ่านแต่เทสใหม่ดีกว่า
```ruby
#include <Arduino.h>
const int SPEED_UP= 0;
const int SPEED_DOWN= 1;
const int SPEED = 2;
int state;

int motorSpeed = 50;  // ความเร็วเริ่มต้นของมอเตอร์


void setup() {
  Serial.begin(115200);
  state = SPEED;
  
  pinMode(D5, INPUT);
  pinMode(D6, INPUT);
  pinMode(D0, OUTPUT);
  pinMode(D1, OUTPUT);
}

void loop() {
  switch (state) {
    
    case SPEED:
      Serial.println("ความเร็วปัจจุบัน: " + String(motorSpeed));
      if (digitalRead(D5) == 1) {
        state = SPEED_UP;
      } else if (digitalRead(D6) == 1) {
        state = SPEED_DOWN;
      }
      analogWrite(D0, motorSpeed);
      analogWrite(D1, 0);
      break; 

    case SPEED_UP:
      if (motorSpeed < 100) {
        motorSpeed = motorSpeed + 10; 
      
      }
      Serial.println("เพิ่มความเร็ว: " + String(motorSpeed));
      state = SPEED;
      delay(500);
      break;

    case SPEED_DOWN:
      if (motorSpeed > 0) {
        motorSpeed = motorSpeed-10;  
      }
      Serial.println("ลดความเร็ว: " + String(motorSpeed));
      state = SPEED;
      delay(500);
      break;

  }
}
```