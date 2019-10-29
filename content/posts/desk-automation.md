---
title: "Automating my desk lamp"
date: 2019-10-28T21:11:15+02:00
draft: false
summary: Let the computer turn on the lamp...
images: [/static/img/lamp-relay-esp.png]
---
Automation makes the life easier. At least thats what it should do...
In my case im not sure it actually did simplify my life as a few years later i own way more stuff and tools to build said automation than my small dorm room can handle.

Most of the stuff i build is now living on my desk. Among other things that includes my "smart" desk lamp[^1], which is just a normal IKEA lamp[^2] with the power cord cut, a 2-Channel relay from ebay and an ESP32 (which is a microcontroler with WIFI). Thous things in combination allow me to turn the lamp on when its getting dark and off when i'm finally lying in bed, which would normally be way out of reach of the light switch.

{{< figure src="/img/lamp-relay-esp.png" title="Relay wiring">}}

When you read instructions how to do this most of them say to just cut one mains wire. The circuit will work but as the EU-Plug is reversible that could mean only the neutral wire gets disconnected (depending on the orientation). Normally that doesn't matter as you can't touch it, but for example when you change the light bulb (and the lamp is off) there still could be live voltage in the lamp.

This was my first time messing with mains wiring and i had a ton of respect. I 3D-printed a nice case for the relay and the wiring so that even if i wanted to i couldn't touch the wiring. And cause im paranoid i put that in another electrical case just for good measure.


For the software i used [ESPHome](https://esphome.io/) which is a nice open source firmware for the ESP32 (and ESP8266). You define a YAML file with all the functionality you want to have and have esphome generate all the actual c++ code (and flash it also). My config for the lamp looks like this:
```yaml
esphome:
  name: schreibtisch
  platform: ESP32
  board: nodemcu-32s

wifi:
  ssid: "               "
  password: "                       "
  use_address: "192.168.222.20"

  ap:
    ssid: "Schreibtisch Fallback Hotspot"
    password: "           "

ota:
  safe_mode: True
  password: "               "


switch:
  - platform: gpio
    pin: 
      number: 33
      inverted: True
    name: "Schreibtischlampe"
    id: relay1

web_server:
  port: 80
  auth:
    username: "<usr>"
    password: "<pw>"

logger:
```
After the first flashing of the ESP you can update the firmware over the air which is quite nice.
As you can see i defined a webserver which enables a REST-Api on the device.
To turn on the lamp on/off i can just type call a easy script which uses curl to make the request:
```bash
#/bin/sh!
curl -u <usr>:<pw>  -X POST http://192.168.222.20/switch/schreibtischlampe/toggle
```

This setup already works but its actually not that good to only be able to control the lamp via a network connection. If thats down i can't turn on the light to fix[^3] the network connection which is bad cause then i cant turn on the light...

To escape that vicious circle of darkness i plan to add some nice tactile arcade buttons to my desk. Stay tuned for that!

[^1]: It can't play chess or drive a car but at least it connects to a router ;)
[^2]: A black [FORSÅ](https://www.ikea.com/de/de/p/forsa-arbeitsleuchte-schwarz-00146776/) to be exact
[^3]: And by that i mean restart the router under my desk


