+++
title = 'helloworld-rs-tag-scrapper'
description = "Scrap tags from a search term on HelloWorld.rs, then get a graph."
date = 2023-11-10T23:23:56+01:00
draft = false
tags = ["cli"] # cli, gui, tui, web
tech = ["python"] # tech used for the project
weight = 70
github = "https://github.com/tunalad/"
+++

A tool that, based on your input, will give you what tags are being used on the helloworld.rs.

For example, inputing python and selecting your seniority (or none), it will look through all the ads and fetch the tags from them.

![searching python, selecting no seniority, displaying top 15 results](/images/hwrs-tag-scrapper/search.png)

After that, it will create a graph with the count of found items.

![graph example](/images/hwrs-tag-scrapper/graph.png)

Alsongside with pdf-splitter, this project was also made for the SCS (Specialized Computer Systems) course
