+++
title = 'nsp'
description = "New Serbian Translation Bible on the CLI (+ BibleGateway scrapped)"
date = 2023-11-30T18:52:53+01:00
tags = ["cli"]
tech = ["python", "beautiful-soup"]
weight = 90
notable = false
github = "https://github.com/tunalad/nsp"
+++

A command-line tool for searching and reading the Bible in the new Serbian translation.

Fork of Luke Smith's [kjv fork](https://github.com/LukeSmithxyz/kjv.git) with some changes made for setting up other translations.

Repository also comes with a web scraper that scraps the whole bible from BibleGateway's website, which is what I used to get the NSP bible.

```sh
    usage: nsp [flags] [reference...]

      -l      list books
      -r      random verse
      -W      no line wrap
      -h      show help

      Reference types:
          <Book>
              Individual book
          <Book>:<Chapter>
              Individual chapter of a book
          <Book>:<Chapter>:<Verse>[,<Verse>]...
              Individual verse(s) of a specific chapter of a book
          <Book>:<Chapter>-<Chapter>
              Range of chapters in a book
          <Book>:<Chapter>:<Verse>-<Verse>
              Range of verses in a book chapter
          <Book>:<Chapter>:<Verse>-<Chapter>:<Verse>
              Range of chapters and verses in a book

          /<Search>
              All verses that match a pattern
          <Book>/<Search>
              All verses in a book that match a pattern
          <Book>:<Chapter>/<Search>
              All verses in a chapter of a book that match a pattern
```
