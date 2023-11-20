+++
title = 'NeFT'
description = "Create files from pre-defined templates."
date = 2023-11-09T22:02:51+01:00
tags = ["tui", "cli"]
tech = ["python"]
weight = 20
notable = true
github = "https://github.com/tunalad/"
+++

NeFT (**Ne**w **F**rom **T**emplate) is a simple command-line tool that allows you to create new files using pre-made templates.

I developed this tool during my transition to a more CLI based workflow when I found myself missing the convenience of the `Create New` option in GUI file managers.

## 1. Usage

NeFT offers various options, allowing you to customize your file creation experience. You can choose to draw icons, display the full file path, and sort files in the menu based on your preferences. Additionally, NeFT provides other functionalities like enabling loop mode, specifying a configuration file path, and setting the output location.

```sh
NeFT - New From Template - Create files from pre-defined templates.

options:
  -h, --help            show this help message and exit
  -i, --icons           draw icons in the menu
  -l, --loop            enable loop mode
  -f, --full-path       draw the whole file path
  -xdg, --use-xdg-path  include xdg-user-dir templates path
  -c PATH, --config PATH
                        configuration file path
  -s SORT_TYPE, --sort SORT_TYPE
                        sort files by name or extension
  -r, --reverse         reverse the sorting order
  -o PATH, --output PATH
                        output path
```

## 2. Configuration

Pretty much all the options we have mentioned above can be set inside the YAML configuration file, avoiding the need to pass them when running the tool. However, we have a couple of config-exclusive options like paths.

By default, NeFT looks at the `$HOME/Templates` directory for templates. Recognizing that many users prefer a clutter-free `$HOME`, where unnecessary files and folders are kept to a minimum, the tool allows for defining custom paths in the configuration file. This flexibility enables a tidy and organized setup tailored to individual preferences.

```yaml
# example config file
# none of these are required
# but "paths" are recommended

paths: # defining paths (not required if using use_xdg_path)
    - "~/Templates/"
    - "~/.local/share/templates/"

icons: true # draw icons
full_path: false # print the whole path
loop: false # loop mode
use_xdg_path: false # include xdg-user-dir templates path
sort: "name" # sort files by "name" or "extension"
reverse: true # reverse the sorting order
```

## 3. Explaining "loop mode" and the xdg option

"Loop mode" in NeFT simplifies the process of creating multiple files by continuously prompting for the generation of files from templates. When we pass this option, NeFT will repeatedly ask for the creation of additional files, allowing for a straightforward and efficient workflow. To exit the loop, press ESC. This option is useful when you need to create multiple files in succession.

The `xdg` options feature incorporates the path of `xdg-user-dir TEMPLATES`. Prior to making NeFT publicly available, it was hardcoded to look at `~/Templates`. However, I realized that it would be more intuitive to align with the actual xdg templates path (as this is the default path by the above mentioned command). In the process of refining this tool, I considered incorporating new file options that are typically available when right-clicking within a file manager (New Folder or Empty File). Though, I also considered that users might prefer not to include these files in the menu, so I decided to allow users to define their own paths, defining the in the [config file](#configuration).
