+++
title = 'vue-floppy-sim'
description = "Web app for testing if your files can fit onto a floppy disk."
date = 2023-11-10T23:19:51+01:00
draft = false
tags = ["web"] # cli, gui, tui, web
tech = ["vue", "javascript"] # tech used for the project
weight = 50
github = "https://github.com/tunalad/vue-floppy-sim"
live = "https://tunalad.github.io/vue-floppy-sim/"
+++

This web app was born from a music project that I planned. Idea was to create an album using [Sonic Pi]() and put it onto a floppy disk. So we just take the Sonic Pi code we wrote, and put it on a floppy disk. I also very much wanted to use some samples, so I would have to manage how many samples I can fit on there. And this is pretty much what the tool was meant to help with.

![empty page](/images/vue-floppy-sim/empty.png)

So the idea is, you select on what type of floppy you want to put the files on, and just see what can fit on the floppy disk

![some files](/images/vue-floppy-sim/filled.png)

When a single file is too big, or collection of files are too much for the floppy, text will get red, warning you that they can't fit

![some files](/images/vue-floppy-sim/one-overflow.png)
![some files](/images/vue-floppy-sim/filled-overflow.png)

And that's pretty much it, you can add and remove files from the list and just watch for some text getting red
