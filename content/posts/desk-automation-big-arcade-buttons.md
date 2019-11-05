---
title: "Big shiny arcade buttons"
date: 2019-11-05T08:20:43+01:00
draft: true
summary: Adding buttons to my "smart desk"
images: [/static/img/buttons-aus.jpg, /static/img/buttons-switches.jpg]
---
Last [post]({{< ref "/posts/desk-automation.md" >}}) i teased the next upgrade of my smart desk project which are some big arcade buttons to control the light even when my network is down. Well... 

I finished that part over the last few days:

{{< figure src="/img/buttons-aus.jpg">}}

The buttons i did choose for the desk are thous big arcade buttons[^1] as they produce this satisfying click when pressed. They come with an integrated LED and resistor, but -as they are not supposed to be driven by a 3.3 volt microcontroller- they need 12 volt supplied to be fully lit up. For the controller i use a normal USB power supply so i tried to power the LEDs with 5 volts.  That made them bright enough so i went with that...
To up the 3.3V logic level from the GPIOs of the controller to 5V i just used a normal 2N2222 NPN-Transistor[^2]. Soldered together the switches + transistor + some cables the "thing" looks something like this:
{{< figure src="/img/buttons-switches.jpg">}}


[^1]: You can find them easily when you search ebay or any other site that sells electronics from china
[^2]: [Sparkfun](https://learn.sparkfun.com/tutorials/transistors/applications-i-switches) describes the basic circuit quite good