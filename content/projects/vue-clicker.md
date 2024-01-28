+++
title = 'vue-clicker'
description = "Coockie clicker clone, where you make Vue apps insead of cookies!"
date = 2024-01-23T18:17:21+01:00
draft = false
tags = ["web", "game"] # cli, gui, tui, web, game
tech = ["vue", "javascript"] # tech used for the project
weight = 29
notable = true
github = "https://github.com/tunalad/vue-clicker"
live = "https://tunalad.github.io/vue-clicker/"
+++

A [Coockie Clicker](https://orteil.dashnet.org/cookieclicker) clone written with Vue, where you make Vue apps insead of cookies!

![/images/vue-clicker/deep-in-game.png](/images/vue-clicker/deep-in-game.png)

## 1. Cookie Clicker

Cookie Clicker is a game about making an absurd amount of cookies. You start by clicking the cookie yourself, then you start purchasing cookie makers (grandmas, farms, factories) and upgrades, speeding up the process of making cookies. There is a lot more to this game, but the core of the game are the buildings and upgrades for them.

This clone isn't as complicated as the original game, at the moment I have just implemented the cookie makers.

And instead of making cookies, we're making Vue projects! So for the buildings, instead of grandmas, farms and factories, you buy developers that use different operating systems (Windows, Mac, Ubuntu, Arch users).

## 2. Auto-clickers

There's three different states autoclicking can be in: early game, mid game, and "slow mode". All of these modes affect `setInterval` function, changing it's speed or incrementation value.

```js
function startAutoclicker(cps) {
    if (state.autoClick <= 0) return;

    let speed = 0;
    let increment = 1;

    // ...
    if (state.tabbedIn) {
        if (cps < 100) speed = 1000 / cps;
        // ...
    }
    // ...
}
```

### 2.1 Early game

Early game has the simplest implementation. Game always increments by 1 and calculates `speed` based on what CPS (clicks per second) we have, `speed` being the delay we give `setInterval`.

I will just mention the timing and incrementing stuff in this post. For more details, check out the whole file [here](https://github.com/tunalad/vue-clicker/blob/master/src/store.js).

### 2.2 Mid game

Mid game happens when we do more than 100CPS. We cap the `speed` 10 and calculate the incrementation value. We take the current CPS, multiply it to our `speed` and divide by 1 second.

```js
function startAutoclicker(cps) {
    // ...
    if (state.tabbedIn) {
        if (cps < 100) speed = 1000 / cps;
        else {
            increment = calcClicks(cps, 10);
            speed = 10;
        }
    } else { ... }
    // ...
}
```

Sadly this implementation can also return decymal numbers, which makes ugly numbers and breaks the accuracy of the clicks made. But at that point the game is going pretty fast, so it's not really something that players can notice.

### 2.3 "Slow mode"

This mode kicks in whenever we focus away from the game, either by alt-tabbing or opening the console. What happens is, we slow down the incrementation to 5 seconds, and use the same function we use for mid game state. We calculate based on our CPS how many clicks would happen in the span of those 5 seconds.

```js
function calcClicks(cps, ms) {
    return cps * (ms / 1000);
}

// ...

function startAutoclicker(cps) {
    // ...
    if (state.tabbedIn) { ... }
    else {
        console.log("Slow state started due to window not being focused.");
        increment = calcClicks(cps, 5000);
        speed = 5000;
    }
    // ...
}
```

I did also plan on implementing something like an "away mode", where we calculate the time between the last save and the time we came back to the game. So if you leave the game for like 5 days, we increment the clicks based on that time. Tho I think this feature is a little bit over the top for something people won't spend more than 10 minutes on it I guess. Plus the problem with dealing with big numbers isn't what I feel like dealing for this project

## 3. State saving

All the data related stuff I mentioned so far is stored insite a simple state manager. Clicks count, amount of buildings we have, etc.
I took the lazy approach and just threw everything inside the `localStorate` and called it a day.

Besides the save button at the top of the screen, game auto-saves every 5 minutes. Game also saves whenever you buy a new clicker. "Slow mode", every time it increments, it will also save the state
