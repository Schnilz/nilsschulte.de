---
title: "Building a animated RGB-LED Thingy"
date: 2019-12-01T16:53:22+01:00
draft: false
summary:  "quick and dirty diy-christmas present(s)"
images: ["/static/img/led-cricle-rainbow.png"]
---

This year for chrismas i set myself the challange to not buy anything new to give away as presents.
Better for the enviroment and forces me to get creative[^1] with the stuff i already have lying around.
I ended up desgning something with my 3D-Printer and the fillament techincaly did lie around... not sure if that count tho ;)


Anyways this is what i came up with:

![rainbow anim](/img/led-cricle-rainbow.png#center)

Its a 3D-Printed enclosure with some paper glued to as a diffuser for LED lights. The Brains is an ESP32 running micropython (which i praised in my last [post]({{< ref "/posts/dabbling-micropython.md" >}})).
Right now it just plays 2 "animations" which you can switch with a button on the bottom side of the case. A secound button changes the brightness.
Thats all for the functionality at the moment. *BUT* when there is the inevitable beak between meals on christmas i plan to build some more nice animations and try to expose a REST-Interface to be able to change animation and brighntess over the network.

I put the design files[^2], the code and some basic instructions on [github](https://github.com/schnilz/led-circle). So feel to make your own ;)


[^1]: at least that is what i thought ;) ... My GF isnt realy impressed with  RGB-LEDs anymore  ^^
[^2]: all created with FreeCAD <3 (im still learning that software so the design is probably realy badly made)
