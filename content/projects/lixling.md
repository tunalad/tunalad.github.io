+++
title = 'lixling'
description = "Minimal plugin manager for Lite XL text editor."
date = 2023-11-10T22:24:24+01:00
tags = ["gui"]
tech = ["lua", "lite-xl"]
weight = 40
notable = true
github = "https://github.com/tunalad/lixling"
+++

**Lixling**: A minimalistic plugin manager for [Lite XL](https://lite-xl.com/), inspired by [vim-plug](https://github.com/junegunn/vim-plug).

The goal of this project was to create a small and straightforward plugin manager for Lite XL, free from dependencies on external Lua modules or programs (except for git), ensuring seamless integration with the text editor.

## 1. Usage

### 1.2 Commands

Let's start by unraveling the commands:

| Command          | Description               |
| ---------------- | ------------------------- |
| Lixling: Install | Installs listed plugins   |
| Lixling: Update  | Updates listed plugins    |
| Lixling: Upgrade | Updates Lixling itself    |
| Lixling: Clear   | "Exiles" unlisted plugins |

Here's a quick breakdown:

-   **Install**: Installs the plugins defined in the configuration.
-   **Update**: Pulls the latest version of the listed plugins.
-   **Upgrade**: Updates Lixling itself; might become obsolete in the future as Lixling evolves into a more traditional Lite XL plugin.
-   **Clear**: Examines the plugins directory, compares it with the configuration, and "exiles" any extra files not defined, moving them to the "exiled" directory.

### 1.1 Configuration

To initialize Lixling, add the following to your Lite XL config file:

```lua
local lixling = require("lixling")

lixling.plugins({
    -- Your plugins go here
})
```

For the basics of configuration, let's cover defining a plugin and whitelisting a file:

```lua
local lixling = require("lixling")

lixling.plugins({
    -- Define a plugin to be downloaded (e.g., minimap)
    ["minimap"] = "https://raw.githubusercontent.com/lite-xl/lite-xl-plugins/master/plugins/minimap.lua",

    -- Whitelist a plugin to prevent it from being exiled
    ["some-plugin"] = "",
})
```

In the above configuration, we've defined a plugin called "minimap" with a raw URL for download. Running the install command will download and place this file in the plugins directory, requiring a Lite XL reload. Whitelisting is demonstrated with "some-plugin," ensuring it won't be exiled when the clear command is executed.

For more advanced options, such as specifying branches, renaming downloaded files, and post-download commands, check out the [repo's README](https://github.com/tunalad/lixling#readme).
