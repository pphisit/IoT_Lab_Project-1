จากข้อ 2 ให้เพิ่ม audio out node อ่านออกเสียงค่าอุณหภูมิ

```ruby
[
    {
        "id": "50ddc515eef199a3",
        "type": "firebase-in",
        "z": "dc457c6f1b613044",
        "name": "",
        "constraint": {},
        "database": "acc072ae6bd90de3",
        "listenerType": "value",
        "outputType": "string",
        "path": "/Sensor/Temperature",
        "useConstraint": false,
        "x": 688.0000305175781,
        "y": 649.9999771118164,
        "wires": [
            [
                "02f7ed67b7d8c44c",
                "2c049dcc3a184ca6",
                "1952cb2492d2ecaa",
                "aed11e55e4dec7df"
            ]
        ]
    },
    {
        "id": "acc072ae6bd90de3",
        "type": "database-config",
        "name": "Peerapat Sariman",
        "authType": "email",
        "claims": {},
        "createUser": false,
        "useClaims": false
    }
]


```