กำหนดให้ทำระบบแจ้งเตือนเมื่ออุณภูมิสูงเกิน 30 องศา โดยใช้ function node เป็นตัวกำหนดเงื่อไขการทำงาน

```ruby
[
    {
        "id": "36bae79f28adf1a5",
        "type": "tab",
        "label": "บท8",
        "disabled": false,
        "info": "",
        "env": []
    },
    {
        "id": "399737ba10f12d75",
        "type": "ui_chart",
        "z": "36bae79f28adf1a5",
        "name": "",
        "group": "c551eaa1ae24df22",
        "order": 1,
        "width": 0,
        "height": 0,
        "label": "Temperature Graph",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "",
        "dot": false,
        "ymin": "",
        "ymax": "",
        "removeOlder": 1,
        "removeOlderPoints": "",
        "removeOlderUnit": "60",
        "cutout": 0,
        "useOneColor": false,
        "useUTC": false,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "outputs": 1,
        "useDifferentColor": false,
        "className": "",
        "x": 978.0000076293945,
        "y": 616.9999694824219,
        "wires": [
            []
        ]
    },
    {
        "id": "69bf6c57508a48af",
        "type": "ui_chart",
        "z": "36bae79f28adf1a5",
        "name": "",
        "group": "11a858d05f83445d",
        "order": 1,
        "width": 0,
        "height": 0,
        "label": "Humidity Graph",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "",
        "dot": false,
        "ymin": "",
        "ymax": "",
        "removeOlder": 1,
        "removeOlderPoints": "",
        "removeOlderUnit": "60",
        "cutout": 0,
        "useOneColor": false,
        "useUTC": false,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "outputs": 1,
        "useDifferentColor": false,
        "className": "",
        "x": 968.0000076293945,
        "y": 796.9999694824219,
        "wires": [
            []
        ]
    },
    {
        "id": "5200d2ffaa91685e",
        "type": "firebase-in",
        "z": "36bae79f28adf1a5",
        "name": "",
        "constraint": {},
        "database": "ca5028033c5a512e",
        "listenerType": "value",
        "outputType": "string",
        "path": "/Sensor/Humidity",
        "useConstraint": false,
        "x": 668.0000076293945,
        "y": 836.9999694824219,
        "wires": [
            [
                "69bf6c57508a48af",
                "58f9c593bf02f57e",
                "feaca22f2f033fe8"
            ]
        ]
    },
    {
        "id": "33b9c55adf1ae297",
        "type": "firebase-in",
        "z": "36bae79f28adf1a5",
        "name": "",
        "constraint": {},
        "database": "ca5028033c5a512e",
        "listenerType": "value",
        "outputType": "string",
        "path": "/Sensor/Temperature",
        "useConstraint": false,
        "x": 688.0000305175781,
        "y": 649.9999771118164,
        "wires": [
            [
                "399737ba10f12d75",
                "2cd21726f7d76211",
                "8d49f440698308f8",
                "3e5a87fd289684a5"
            ]
        ]
    },
    {
        "id": "42e1bf234262fd1c",
        "type": "comment",
        "z": "36bae79f28adf1a5",
        "name": "ดึงค่าอุณหภูมิจาก Firebase",
        "info": "",
        "x": 698.0000076293945,
        "y": 616.9999694824219,
        "wires": []
    },
    {
        "id": "e7ab453c26bbd9a4",
        "type": "comment",
        "z": "36bae79f28adf1a5",
        "name": "ดึงค่าความชื้นจาก Firebase",
        "info": "",
        "x": 698.0000076293945,
        "y": 796.9999694824219,
        "wires": []
    },
    {
        "id": "5445bd7376d3d5c2",
        "type": "comment",
        "z": "36bae79f28adf1a5",
        "name": "แสดงกราฟความชื้น",
        "info": "",
        "x": 978.0000076293945,
        "y": 756.9999694824219,
        "wires": []
    },
    {
        "id": "9664f4759b726e48",
        "type": "comment",
        "z": "36bae79f28adf1a5",
        "name": "แสดงกราฟอุณหภูมิ",
        "info": "",
        "x": 968.0000076293945,
        "y": 576.9999694824219,
        "wires": []
    },
    {
        "id": "4edadcf3e75fe23a",
        "type": "comment",
        "z": "36bae79f28adf1a5",
        "name": "แสดงค่าอุณหภูมิ",
        "info": "",
        "x": 968.0000076293945,
        "y": 656.9999694824219,
        "wires": []
    },
    {
        "id": "a107581114ed8125",
        "type": "comment",
        "z": "36bae79f28adf1a5",
        "name": "แสดงค่าความชื้น",
        "info": "",
        "x": 968.0000076293945,
        "y": 856.9999694824219,
        "wires": []
    },
    {
        "id": "58f9c593bf02f57e",
        "type": "ui_text",
        "z": "36bae79f28adf1a5",
        "group": "11a858d05f83445d",
        "order": 2,
        "width": 0,
        "height": 0,
        "name": "",
        "label": "Humidity Value",
        "format": "{{msg.payload}} %",
        "layout": "col-center",
        "className": "",
        "x": 968.0000076293945,
        "y": 896.9999694824219,
        "wires": []
    },
    {
        "id": "2cd21726f7d76211",
        "type": "ui_text",
        "z": "36bae79f28adf1a5",
        "group": "c551eaa1ae24df22",
        "order": 2,
        "width": 0,
        "height": 0,
        "name": "",
        "label": "Temperature Value",
        "format": "{{msg.payload}} C",
        "layout": "col-center",
        "className": "",
        "x": 978.0000076293945,
        "y": 696.9999694824219,
        "wires": []
    },
    {
        "id": "feaca22f2f033fe8",
        "type": "ui_gauge",
        "z": "36bae79f28adf1a5",
        "name": "",
        "group": "11a858d05f83445d",
        "order": 2,
        "width": 0,
        "height": 0,
        "gtype": "gage",
        "title": "gauge",
        "label": "units",
        "format": "{{value}}",
        "min": 0,
        "max": "100",
        "colors": [
            "#00b500",
            "#e6e600",
            "#ca3838"
        ],
        "seg1": "",
        "seg2": "",
        "diff": false,
        "className": "",
        "x": 939.2000198364258,
        "y": 940.9999694824219,
        "wires": []
    },
    {
        "id": "8d49f440698308f8",
        "type": "ui_gauge",
        "z": "36bae79f28adf1a5",
        "name": "",
        "group": "c551eaa1ae24df22",
        "order": 2,
        "width": 0,
        "height": 0,
        "gtype": "gage",
        "title": "gauge",
        "label": "units",
        "format": "{{value}}",
        "min": 0,
        "max": "50",
        "colors": [
            "#00b500",
            "#e6e600",
            "#ca3838"
        ],
        "seg1": "",
        "seg2": "",
        "diff": false,
        "className": "",
        "x": 957.8000221252441,
        "y": 533.0124950408936,
        "wires": []
    },
    {
        "id": "9e7e22c1ed30d12d",
        "type": "ui_audio",
        "z": "36bae79f28adf1a5",
        "name": "",
        "group": "c551eaa1ae24df22",
        "voice": "Microsoft David - English (United States)",
        "always": "",
        "x": 960,
        "y": 480,
        "wires": []
    },
    {
        "id": "d270c7740f6998c8",
        "type": "ui_toast",
        "z": "36bae79f28adf1a5",
        "position": "top left",
        "displayTime": "",
        "highlight": "red",
        "sendall": true,
        "outputs": 0,
        "ok": "OK",
        "cancel": "",
        "raw": false,
        "className": "",
        "topic": "",
        "name": "",
        "x": 990,
        "y": 400,
        "wires": []
    },
    {
        "id": "3e5a87fd289684a5",
        "type": "function",
        "z": "36bae79f28adf1a5",
        "name": "function 1",
        "func": " if(msg.payload>30){\n\n        msg.payload=\"Warning High Temperature\"\nreturn msg;}\n\n",
        "outputs": 1,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 780,
        "y": 380,
        "wires": [
            [
                "9e7e22c1ed30d12d",
                "d270c7740f6998c8"
            ]
        ]
    },
    {
        "id": "c551eaa1ae24df22",
        "type": "ui_group",
        "name": "Temperature Dashboard",
        "tab": "1cfc07c67ad3c0b9",
        "order": 1,
        "disp": true,
        "width": "6",
        "collapse": false,
        "className": ""
    },
    {
        "id": "11a858d05f83445d",
        "type": "ui_group",
        "name": "Humidity Dashboard",
        "tab": "1cfc07c67ad3c0b9",
        "order": 2,
        "disp": true,
        "width": "6",
        "collapse": false,
        "className": ""
    },
    {
        "id": "ca5028033c5a512e",
        "type": "database-config",
        "name": "My Database",
        "authType": "email",
        "claims": {},
        "createUser": false,
        "useClaims": false
    },
    {
        "id": "1cfc07c67ad3c0b9",
        "type": "ui_tab",
        "name": "Home",
        "icon": "dashboard",
        "disabled": false,
        "hidden": false
    }
]

```