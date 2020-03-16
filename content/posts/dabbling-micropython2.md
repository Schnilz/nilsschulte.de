---
title: "Scripts and Stuff"
date: 2020-03-16T14:00:00+01:00
draft: false
summary: more on micropython
---

My university exams for this semester are mostly done by now. And with all the corona-virus-measures the new semester doesn't start for another month. Hopefully I will finish some of those procrastinated projects of mine ;)

Anyways. [Micropython](https://micropython.org/) is still on my Radar (I even used it in one university assignment and it really shined there).
Here is a small script which uploads all files to the controller (when web-REPL is enables of course):

```bash
#!/bin/bash
md5files=$(cat .uploaded)

IP=192.168.222.31
if [ "$#" != 0 ]; then
	IP="$1"
fi

for i in $(ls *.py)
do
   if [[ $md5files != *"$(md5sum $i | cut -d' ' -f1)"* ]]; then
       echo $(md5sum $i)
       webrepl_cli.py -p asdf $i $IP:/$i
       md5files=$(echo $md5files | sed 's|:\([^:]*\)'"$i"'||g'):$(md5sum "$i")
       echo "$md5files" > .uploaded
   fi
done
```

The script saves the md5 hashes of the uploaded files in a file called `.uploaded` so unchanged files don't get constantly uploaded again. The script doesn't check if the upload is successful, so only run the script when the upload is going to work ;)
It uses the `webrepl_cli.py` script from the official micropython [github page](https://github.com/micropython/webrepl).
As you can see my script is hacked together and i should probably feel bad for making it public here, but it works and im going to update it if i feel the need to[^1].

[^1]: which means if i have to `rm .uploaded` too often when the uploaded didn't work.
