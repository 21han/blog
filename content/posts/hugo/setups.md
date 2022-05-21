---
title: "Hugo 1 - Getting Started"
date: 2022-05-15
draft: false
weight: 100
tags: ['hugo']
TocOpen: true
ShowPostNavLinks: true
---

## Getting Started

The
[Official Doc](https://adityatelange.github.io/hugo-PaperMod/posts/papermod/papermod-installation/)
is easy to follow. Make sure to not alter anything in `./themes` folder unless you are deliberately making
changes to the theme submodule.

## Start Server

> `hugo server` will avoid writing the rendered and served content to disk, preferring to store it in memory.
> 
> By default hugo will also watch your files for any changes you make and automatically rebuild the site. It will then live reload any open browser pages and push the latest content to them. As most Hugo sites are built in a fraction of a second, you will be able to save and see your changes nearly instantly.


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

## Write a new post

To test creating a new post, try below:
```bash
hugo new posts/<optional-folder-name>/<post-name>.md
```

Generally, use the following **Hugo** command:

```bash
hugo new [path] [flags]
```

### Options

```text
  -b, --baseURL string         hostname (and path) to the root, e.g. https://spf13.com/
  -D, --buildDrafts            include content marked as draft
  -E, --buildExpired           include expired content
  -F, --buildFuture            include content with publishdate in the future
      --cacheDir string        filesystem path to cache directory. Defaults: $TMPDIR/hugo_cache/
      --cleanDestinationDir    remove files from destination not found in static directories
  -c, --contentDir string      filesystem path to content directory
  -d, --destination string     filesystem path to write files to
      --disableKinds strings   disable different kind of pages (home, RSS etc.)
      --editor string          edit new content with this editor, if provided
      --enableGitInfo          add Git revision, date, author, and CODEOWNERS info to the pages
      --forceSyncStatic        copy all files when static is changed.
      --gc                     enable to run some cleanup tasks (remove unused cache files) after the build
  -h, --help                   help for new
      --ignoreCache            ignores the cache directory
  -k, --kind string            content type to create
  -l, --layoutDir string       filesystem path to layout directory
      --minify                 minify any supported output format (HTML, XML etc.)
      --noChmod                don't sync permission mode of files
      --noTimes                don't sync modification time of files
      --panicOnWarning         panic on first WARNING log
      --poll string            set this to a poll interval, e.g --poll 700ms, to use a poll based approach to watch for file system changes
      --printI18nWarnings      print missing translations
      --printMemoryUsage       print memory usage to screen at intervals
      --printPathWarnings      print warnings on duplicate target paths etc.
      --printUnusedTemplates   print warnings on unused templates.
      --templateMetrics        display metrics about template executions
      --templateMetricsHints   calculate some improvement hints when combined with --templateMetrics
  -t, --theme strings          themes to use (located in /themes/THEMENAME/)
      --trace file             write trace to file (not useful in general)
```


## Version Control

Yes, GitHub 👍


