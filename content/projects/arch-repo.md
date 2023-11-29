+++
title = 'arch-repo'
description = "My Arch Linux repository"
date = 2023-11-20T23:26:21+01:00
draft = false
tags = ["cli"] # cli, gui, tui, web
tech = [""] # tech used for the project
weight = 100
notable = false
github = "https://github.com/tunalad/arch-repo"
live = "https://tunalad.github.io/arch-repo/"
+++

Not necessarily a project, but something that I want to share here.

I have my own Arch Linux repository, where I put tools that I wrote, tools that I forked and made changes and older versions of some tools.

List of the packages can be found [here.](https://tunalad.github.io/arch-repo/)

To add this repository to your own system, add this to your `/etc/pacman.conf`

```bash
[tunalad]
SigLevel = Optional DatabaseOptional
Server = https://tunalad.github.io/arch-repo/$arch
```
