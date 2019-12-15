---
title: "Dabbling with micropython"
date: 2019-11-18T12:10:00+01:00
draft: false
summary: i wanted to know what all that fuss is about so i fianlly put micropython on the ESP32 ... 
---

[micropython](https://micropython.org/) is python for microcontroller. When i first heard about it i wasn't really sure what to think about it as python is a really high level language and now that should run on a microcontroller ? no way, that has to be a slow mess...

Turns out its not :D
I mean it is, but for most of (my) projects you really don't need the speed anyways. Also the prog-mem of the ESP32 is so big it doesn't really matter that more than one quarter of it is now occupied with code that doesn't do anything at first. Now that i covered the bad sides of uPython i'll tell you about the really big strengths and advantages it has over c and c++ for microcontroller programming:

**Read–eval–print loop**
(or REPL for short)

With that you get an interactive console (with tab-autocompletion!) over the serial port and you can prototype without ever needing to wait hours and hours[^1] for code to compile and upload. And you can focus on the electronic and not on some stupid dependency error. Its just like you know it from pythons console with a (sometimes annoying) difference: you only get to press the up arrow 7 times[^2] to get previously typed commands as the history is saved on the uC itself. Not sure why that's done that way, i would have saved the history in the REPL calling device (but maybe im missing something)... so maybe i'll make a PR if its bothering me enough, even if i never have written any Javascript in my life before ;)

This is a short post but maybe i could inspire you to try out micropython on your own in the future if you haven't already.

The projects im currently working on are some Christmas presents (involving a uC with micropython, obviously) so stay tunes for that.

[^1]: it's minutes at max most of the time, but still ;)
[^2]: i think its changeable but the downloadable uPython binary has 7 as a default
