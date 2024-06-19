+++
title = 'vue-minesweeper'
description = "Just your average Minesweeper clone"
date = 2024-05-18T19:42:55+02:00
draft = false
tags = ["web", "game"] # cli, gui, tui, web, game
tech = ["vue", "javascript"] # tech used for the project
weight = 28
notable = true
github = "https://github.com/tunalad/vue-minesweeper"
live = "https://tunalad.github.io/vue-minesweeper"
+++

A minesweeper clone, inspired by [Minesweeper.Online](https://minesweeper.online) version of the game.

![State of the page when we first open the page up](/images/vue-minesweeper/game-easy.png)

![Game won](/images/vue-minesweeper/game-win.png)
![Game lost](/images/vue-minesweeper/game-loss.png)

Those first two screenshots were on easy mode (9x9, with 10 bombs). Medium difficutly is 16x16 with 40 bombs, and hard is 16x30 with 99 bombs. These difficuties are all based on the minesweeper game mentioned above.

![Board on medium difficutly](/images/vue-minesweeper/game-medium.png)
![Board on hard difficutly](/images/vue-minesweeper/game-hard.png)

And just like the minesweeper clone I mentioned earlier, I have also included a "custom difficutly" mode. Although I have slightly different way of calculating the maximum and minimum number of mines. 


I don't know what formula is used on `Minesweeper.Online`, so I decided to just go with `X*Y/pi` (and we round that number down). It makes our clone easier, but the number of mines isn't too drastic. `11x11` board on `Minesweeper.Online` will limit you to 46 mines max, while our solution gives us `38.51549622823867125607` (that we just round up to 38)

![Board on custom 10x30 difficutly](/images/vue-minesweeper/game-custom.png)

So yeah, that's about it
