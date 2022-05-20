---
title: "Go Hugo"
date: 2022-05-15T18:42:28-04:00
draft: false
tags: ['hugo']
TocOpen: true
ShowPostNavLinks: true
---

## Get Started

The
[Official Doc](https://adityatelange.github.io/hugo-PaperMod/posts/papermod/papermod-installation/)
is easy to follow. Make sure to not alter anything in `./themes` folder unless you are deliberately making
changes to the theme.

## Start Server

```
# the --navigateToChanged has been particularly useful to quickly see changes
hugo server --navigateToChanged -D
```

## Folder Structure

```text
❯ tree -d ./    
./
├── content
│   └── posts
│       └── hugo  # I created a folder for each topic that I want to write about
├── layouts
├── public
├── resources
│   └── _gen
│       ├── assets
│       └── images
├── static
```

## Version Control

Yes, GitHub 👍


