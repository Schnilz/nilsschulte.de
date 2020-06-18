---
title: "Building a animated RGB-LED thingy"
date: 2019-12-01T16:53:22+01:00
draft: false
summary:  "Quick and dirty diy-christmas present(s) ..."
images: ["/static/img/led-cricle-rainbow.png"]
---

This year for Christmas i set myself the challenge to not buy anything new to give away as presents.
Better for the environment and forces me to get creative[^1] with the stuff i already have lying around.
I ended up designing something with my 3D-Printer. The filament technically did lie around... not sure if that counts though ;)


Anyways, this is what i came up with:

![rainbow anim](/img/led-cricle-rainbow.png#center)

It's a 3D-Printed enclosure with some paper glued to as a diffuser for 23 RGB-LEDs. The brains is an ESP32 running micropython (which i praised in my last [post]({{< ref "/posts/dabbling-micropython.md" >}})).
Right now it just plays 2 "animations" which you can switch between with a button on the bottom side of the case. A second button changes the brightness.
That's all for the functionality at the moment. *BUT* when there is the inevitable break between meals on Christmas i plan to create some more nice animations and try to expose a REST-Interface to be able to change animation and brightness over the network.

I put the design files[^2], the code and some basic instructions on [github](https://github.com/schnilz/led-circle). So feel free to make your own or suggest some changes ;)


[^1]: at least that is what i thought ;) ... My gf isn't really impressed with  RGB-LEDs anymore  ^^
[^2]: all created with FreeCAD <3 (im still learning that software so the design is probably really badly made); stl files are available also
