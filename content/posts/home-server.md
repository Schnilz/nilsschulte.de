---
title: "Building a home-server"
date: 2020-06-17
draft: false
summary:  "Building a personal home server ..."
images: [/static/img/server.jpg]
---

In my ongoing effort to decrease my dependence on other people’s computers, 
I finally pulled the trigger and build myself a home-server.
That way I can move all my personal data from the so-called cloud to my home.

The server is build out of my old desktop computer, 
which saw little to no usage after I bought myself a new notebook to be more portable for uni. 
All hardware but the case and power supply is repurposed from my old computer.
I also could have used the case but since the server would be placed in my bedroom[^1] I wanted something silent without fans, 
so I opted for something passively cooled like the FC-10 Alpha case plus matching power supply from Streacom.
It’s not cheap but seeing the end result it’s probably worth it, as the case keeps it’s promise of making the PC fully silent.
The maximum power the i5-6600K processor from Intel dissipates as heat is roughly 100 watts so lightly higher 
than the Case specified but I have not encountered any cooling-problems after the month of home-server-usage.
The whole build draws about 30 watts of power which equates to about 0,72 kWh per day.
Living in germany this equals about 18 cents per day or 5.60 EUR per month of Power used.
This is similar to most small cloud storage offerings with the benefit of actually owning your personal data 
yourself and being able to just add storage with the one-time cost of a new drive.


When reading up on home-servers and how to build them one topic always has to come up: backups.
Backups prevent otherwise inevitable data loss.
So what is my backup-strategy? I use btrfs-Raid1 on my drives, 
which means having two hard drives mirrored[^2].
This covers hardware failures… but not software failures which would could just write bad data twice to the drives.
That’s why there is a third backup on an external hard drive which is not plugged in all the time so 
when there is software failure or something that kills the drives in the server 
there is a backup from the past that still contains the intact data.
There is potential to upgrade this to a backup-server at another place but that’s something I’ll leave for future me to try out.

![Server](/img/server.jpg#center)

For the operating system I opted for Archlinux as I’m most familiar with this Linux-distribution.
The actual applications are all run in containers and are started by multiple docker-compose files.
There is a nextcloud instance and a gitea one. In the future i'll maybe look into synapse/matrix and set up some notification channel
This was the first time messing with software-containerization and docker in particular.
It turned out to be way easier than I imagined.
The compose files are organized in a git repo, 
as its not ready for general usage I didn’t put it online yet[^3], 
but when i got the time and motivation to finish it I will upload it and post a link to my (selfhosted) repo.

[^1]: One room apartments <3
[^2]: which means storing everything twice on physically different drives and cutting the total capacity in half sadly
[^3]: the passwords are all over the docker-compose files. I'll have to look into docker secrets or .env files so im able to delete them from the yaml's.
