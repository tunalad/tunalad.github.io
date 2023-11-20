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
