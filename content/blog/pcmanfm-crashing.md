+++
title = 'File managers crashing when at $HOME'
date = 2023-11-20T02:47:19+01:00
draft = true
+++

## Problem

So for some time (like two days now maybe, jornalctl shows first errors of this on 18th of November '23), I had a problem opening file managers. It would crash if I tried to go to my home directory.

One day I was trying a bunch of stuff to try and fix this, though no results. I had some problems with xdg-desktop-portals a month or two earlier, though it might have been some dbus stuff, gtk itself maybe, etc.

Note, I didn't yet know that it was crashing in the home directory only, I though it would just crash for whatever reason.

## Hints

A couple of minutes ago, as of writing this, I was trying out other file managers in hope of just somehow fixing itself. I do have a ROX file manager, which I use for drag and drop funcionalities (instead of dragon-drop). I did want to open once more pcmanfm to set up the bookmars, because I though it was it, so I had to install it again.

While installing, I've noticed this at the end

```bash
...
:: Running post-transaction hooks...
(1/3) Arming ConditionNeedsUpdate...
(2/3) Updating the MIME type database...
Error in type 'application/x-core' (in /usr/share/mime/packages/freedesktop.org.xml): Error in <match> element: Mask is longer than value.
Error in type 'image/jp2' (in /usr/share/mime/packages/freedesktop.org.xml): Error in <match> element: Mask is longer than value.
Error in type 'image/jpx' (in /usr/share/mime/packages/freedesktop.org.xml): Error in <match> element: Mask is longer than value.
Error in type 'image/jpm' (in /usr/share/mime/packages/freedesktop.org.xml): Error in <match> element: Mask is longer than value.
Error in type 'video/mj2' (in /usr/share/mime/packages/freedesktop.org.xml): Error in <match> element: Mask is longer than value.
Error in type 'image/vnd.adobe.photoshop' (in /usr/share/mime/packages/freedesktop.org.xml): Error in <match> element: Mask is longer than value.
(3/3) Updating the desktop file MIME type cache...
...
```

I don't know if it was throwing these errors before when installing pcmanfm, but I knew what was the problem now

## Solution

All you had to do is to remove `~/.local/share/mime/mime.cache` file. This is the fix...
