+++
title = 'qthon'
description = "Quake 1 WAD editor"
date = 2024-06-12T20:02:28+02:00
draft = false
tags = ["gui"] # cli, gui, tui, web, game
tech = ["python", "qt"] # tech used for the project
weight = -1
notable = true
github = "https://github.com/tunalad/qthon"
live = ""
+++

![qthon logo](/images/qthon/qthon.png)

A Quake 1 WAD editor inspired and replacement for [TexMex](https://developer.valvesoftware.com/wiki/TexMex) editor.

This tool is still in development and not completely finished, but it shouldn't look too different in the future.

I will talk about this app as if you're looking for a tool that you want to use, so I won't really cover the code part of the tool (so I won't mention stuff how the history state is being handled).

I will also go about writing this article like how we would go about using this tool in the production by working one of my maps.

![qthon viewing start.wad](/images/qthon/qthon-start-wad.png)

## Usage

So when you start the tool, you get an empty list of items.

![empty qthon](/images/qthon/qthon-empty.png)

You can open or import a WAD file or an image. I will open `monitor.wad` and work with it. It's for a map that I'm using to take screenshots for one of my music projects.

![qthon viewing monitor.wad](/images/qthon/qthon-monitor.png)

Now, I want to also include a poster or a drawing on my map. For that we will use this piece:

![Gladiola Garden; poems of outdoors and indoors for second grade readers Pl.26 (1940)](/images/qthon/artwork.png)

Importing images that don't really fit the WAD texture sizes will get their size fixed automatically. Image I've imported is `800x1016`, so it will get resized to the maximum quake supports (that being `512x512`). Since the height is greater, it will be limited to `512` pixels, while the width to `400`. Qthon is trying to keep the aspect ratio.

![image imported and dithered](/images/qthon/import-dithered.png)

Due to limited color palette in Quake, images get converted to 256 colors. So if you imported a super high quality image, it will get ruined because of that.

![quake palette image](/images/qthon/quake-palette.png)

Let's try to use the texture in the map.

![trenchbroom screenshot](/images/qthon/trenchbroom-screenshot1.png)

As we can see, the texture is MASSIVE.

Since we're trying to create like a poster for a room, we have to resize the image to fit our needs. In this case `48x64` should be ideal.

![resizing example](/images/qthon/resizing.png)
![resized texture](/images/qthon/resized-texture.png)

Let's update the map and see it in the game.

![resized texture in game](/images/qthon/resized-ingame.png)

Now, the map is dark, there's little to no light. But as we can see, some pixels are glowing here. Those pixels are called "fullbrights". That's the two last rows of colors on the palette I've shown earlier. They're used for stuff like fire, or for stuff that we still want visible in the dark like health crates

Since we don't need those fullbright pixels on our poster, I want them removed. We can remove them with the "defullbright" option. All this does is apply the quake palette to the texture, just without the fullbright pixels. This will give us a 2nd copy of the texture without fullbright pixels, it name ending with `-dfb`.

![defullbright example](/images/qthon/dfb-example.png)

If you don't need the texture with fullbright pixels, you can just remove it and remove the `-dfb` from the name

![renaming example](/images/qthon/renaming-texture.png)

Since we just deleted the old texture and renamed the new one the same thing, we can just reload the WAD in trenchbroom. Let's check out the poster in game again.

![defullbright texture on the map](/images/qthon/trenchbroom-screenshot2.png)

(map has interactive lights, so I decided to just take the screenshot without any light going on)

And this about covers the most commong stuff functionalities you'll do.

## Some other stuff we haven't covered:

Due to how I wanter to preset this tool, we didn't cover everything the tool has. And I don't really want to show everything, I feel like the tool is pretty intuitive. But either way, here's two more cool things this tool can do:

### 1. Flipping and mirroring textures

![flipping and mirroring](/images/qthon/flip-mirror.png)

### 2. Animated preview

There are two kinds of animated textures quake has, animated textures and liquids (both shown in the gif below):

![animated preview](/images/qthon/recording-20240617211102.gif)
