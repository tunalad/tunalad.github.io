+++
title = 'vue-kanban'
description = "Trello inspired task management web app."
date = 2023-11-10T21:23:32+01:00
tags = ["web"]
tech = ["vue", "node", "javascript", "sqlite"]
weight = 10
notable = true
github = "https://github.com/tunalad/vue-kanban"
live = "https://tunalad.github.io/vue-kanban/"
+++

Trello-inspired task management web app. A full stack web app that I built as my graduation project, and a tool that I personally use sometimes.

Besides creating a kanban board app, I wanted to make an actual FOSS alternative to the paid task management apps. So this app can be used by multiple people for actual projects, and they will all get updated when changes to the board are made.

Although it's not completely finishes or styled properly, I am planning to make a separate repository in the future. There I'll try to polish everything up, and add some more sensible features. Plan is to also have an option to let users define server URLs, instead of being stuck at localhost only (as it is now).

Unlike for when I was graduating, I will try to be brief and won't show everything this app has to offer. I will first go about showing around the board part itself, then the dashboard.

## 1. Usage

At the moment you are **required** to download the server app, since the app is looking only at the `localhost:1337` server. Server app is also made with `node + express + sqlite` so you can also build it from the source code pretty quickly.

### 1.1 Boards

As any kanban board does, we can create lists and cards for it.

![board with lists and cards](/images/vue-kanban/board-filled.png)

Clicking on cards we have a bunch of options for it, like renaming them, writing a description for them, applying labels, etc.

![card example](/images/vue-kanban/cropped/card.png)

As for the labels, it's the colored bar cards have. It helps with differentiating them, like what they are exactly related to

![labels list](/images/vue-kanban/cropped/labelman.png)

Editing and creating labels is also pretty simple as passing a title and picking a color for them

![labels editing](/images/vue-kanban/cropped/labelman-edit.png)

### 1.2 Dashboard

Dashboard is pretty much just a list of previously accessed boards, and buttons for creating new boards and finding boards

![dashboard](/images/vue-kanban/cropped/dashboard.png)

Creating a new board will require you to come up with a name and a password for it.

![creating a board](/images/vue-kanban/cropped/new-board.png)

"Find board" button will give you a list of all avaliable boards found on the server. Result can be sorted by it's id or title. Result can be also filtered with the search bar above

![finding a board](/images/vue-kanban/cropped/find-board.png)

Either way, when we try to access a board we haven't accessed yet, we will be asked for a password

![board password](/images/vue-kanban/cropped/password.png)

## 2. Backend explanation

For this section I will just mention in short lines what the server app does. If interested in code, check out the github liked above.

### 2.1 Database

Idea for the database is pretty simple, `board` has `list` and `list` has `card`. There's also stuff like `label` and `card_label`, but those features aren't required for the kanbal app.

![database diagram](/images/vue-kanban/db-dark.png)

All database management stuff is done via module I wrote. It's pretty much like a wrapper for sqlite library, written to have a syntax similar to MongoDB's (so creating classes and calling functions from those classes).

### 2.2 Node + Express app

These technologies aren't necessarily used because I like them, but used primarily because it's javascript. Javascript isn't something that I often use outside of writing Font-end web apps, so I felt like this would be a good way to push me and use it a little more.

This app is structured into multiple files. So instead of writing everything into a single file, I've just made a server initialization file, connected initialized the database, and split routes into their own files. By doing that, I can just write code for one route, then copy it and change some minor stuff related to that table.

### 2.3 Routes

As mentioned above, routes are split into multiple files.

These routes can be split into 3 sections:

-   Simple

    -   these routes just do whatever they have to the database and call it a day.
    -   Example: getting data about a board. We just get the data from the database and return it to the user
    -   Routes: `GET /board/:id`, `DELETE /board/:id`, `DELETE /label/:id`

-   Complex
    -   they're just like simple ones, but they do something extra to the data.
    -   Example: unlocking a board. We pass to the route what table we want to open and what password it has, route checks if everything is correct and returns data accordingly
    -   Routes: `POST /board/:id/unlock`, `POST` routes for `board`, `list`, `card` and `label`, `DELETE` and `PATCH` routes for `list` and `card` tables
-   Routes that return everything about the table
    -   these routes utilise a function that get everything related to the board, packages them in a specific way, and gives it to the route to do whatever it has to.
    -   Routes: `GET /board/:id/full`, `GET /board/:id/live`
    -   Example: watching if the table's data changed. SSE route watches for the data, and updates all users that are connected to the table.
    -   Routes: `GET /board/:id/full`, `GET /board/:id/live`
