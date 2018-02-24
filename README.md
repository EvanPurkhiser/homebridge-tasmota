# homebridge-tasmota

HomeBridge optimized for work with Itead Sonoff and Electrodragon Relay Board
hardware and firmware
[Sonoff-Tasmota](https://github.com/arendst/Sonoff-Tasmota) via MQTT. It acts
as a switch or outlet (depending of configuration).

Very heavily based off of
[@MacWyznawca](https://github.com/MacWyznawca/homebridge-mqtt-switch-tasmota)'s
work.

This fork is essentially a ES6 rewrite with the same functionality.

### Installation

```
yarn global add homebridge-mqtt-switch-tasmota
```

### Configuration

You'll want to add the accessory into your homebridge as such. Many of these
configuration options are not required and have sane defaults.

Sample HomeBridge Configuration (complete)
--------------------
```json
{
    "bridge": {
        "name": "Homebridge",
        "username": "CC:22:3D:E3:CE:30",
        "port": 51826,
        "pin": "031-45-154"
    },
    "platforms": [],
    "accessories": [
        {
            "accessory": "mqtt-switch-tasmota",
            "switchType": "switch",

            "name": "Kitchen Lamp",

            "url": "mqtt://mqtt-broker",
            "username": "mqtt-username",
            "password": "mqtt-password",

            "topics": {
                "statusGet": "stat/sonoff/RESULT",
                "statusSet": "cmnd/sonoff/POWER",
                "stateGet": "tele/sonoff/STATE"
            },

            "activityTopic": "tele/sonoff/LWT",
            "activityParameter": "Online",

            "startCmd": "cmnd/sonoff/TelePeriod",
            "startParameter": "60",

            "manufacturer": "ITEAD",
            "model": "Sonoff",
            "serialNumberMAC": ""
        }
    ]
}
```

A more minimal configuration for the accessory might look something like this:

```json
{
    "accessory": "mqtt-switch-tasmota",
    "switchType": "switch",

    "name": "Kitchen Lamp",
    "url": "mqtt://mqtt-broker",

    "topics": {
        "statusGet": "stat/sonoff/RESULT",
        "statusSet": "cmnd/sonoff/POWER",
    },
```
