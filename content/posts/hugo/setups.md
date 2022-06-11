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

To follow a DRY (Don't Repeat Yourself) principle, please refer to the
[Official Doc](https://adityatelange.github.io/hugo-PaperMod/posts/papermod/papermod-installation/)
for the most basic set-ups. Make sure to not alter anything in the `./themes` folder unless you are deliberately making
changes to the theme submodule, which is recommended if you plan to propose a change to the selected theme.

## Understanding Hugo

When I first started using Hugo, one of the most convenient features is that Hugo automatically refreshes the page that you
have just edited, making it easy to check your edit. Naturally, I was curious how Hugo achieved this feature, so I looked
at its source code, and found the `livereload.go`'s code chunk below.


```go
// source: https://github.com/gohugoio/hugo/blob/master/livereload/livereload.go#L132-L141

func refreshPathForPort(s string, port int) {
	// Tell livereload a file has changed - will force a hard refresh if not CSS or an image
	urlPath := filepath.ToSlash(s)
	portStr := ""
	if port > 0 {
		portStr = fmt.Sprintf(`, "overrideURL": %d`, port)
	}
	msg := fmt.Sprintf(`{"command":"reload","path":%q,"originalPath":"","liveCSS":true,"liveImg":true%s}`, urlPath, portStr)
	wsHub.broadcast <- []byte(msg)
}
```

Basically, this is achieved using a local WebSocket connection from here. This is all based on the wonderful [Gorilla 
Websocket Package](https://github.com/gorilla/websocket)

```go
// source: https://github.com/gohugoio/hugo/blob/master/livereload/connection.go

type connection struct {
	// The websocket connection.
	ws *websocket.Conn

	// Buffered channel of outbound messages.
	send chan []byte

	// There is a potential data race, especially visible with large files.
	// This is protected by synchronisation of the send channel's close.
	closer sync.Once
}
```

### What makes Hugo so secure?


#### Overview

Just because Hugo is an SSG doesn't guarantee it is secure. There are numerous other SSGs out there, but Hugo differs from
others because of its usage of **virtual file system** and **strict default security policy** to ensure runtime security.

The most hardcore way to secure the runtime is to **sandbox** it. What this means is that Hugo uses [spf13/afero](https://github.com/spf13/afero)
as its File System abstraction layer, and no third-party components can mount files outside the root.


#### Security Policy
```go
source: https://github.com/gohugoio/hugo/blob/master/config/security/securityConfig.go

// Config is the top level security config.
type Config struct {
	// Restricts access to os.Exec.
	Exec Exec `json:"exec"`

	// Restricts access to certain template funcs.
	Funcs Funcs `json:"funcs"`

	// Restricts access to resources.Get, getJSON, getCSV.
	HTTP HTTP `json:"http"`

	// Allow inline shortcodes
	EnableInlineShortcodes bool `json:"enableInlineShortcodes"`
}
```

For example, in the code chunk above, Hugo's built-in security policy is to restrict access to `os.Exec`, certain
template functions that aren't completed trusted.


#### Dependency Security

Because all dependencies are managed by [Modules](https://github.com/golang/go/wiki/Modules). Hugo takes advantages
of its `go.sum` which basically checks if your downloaded binary matches the expected cryptographic checksums of the 
version. More readings on this can be found [here](https://github.com/golang/go/wiki/Modules)


### Understanding content structure

```
❯ tree -d ./ 
./
├── content  # 🏠 this is where to place your markdown content
│   └── posts
│       ├── hugo  # I like to group my posts into folders to organize contents
│       └── meditation
├── layouts  # Hugo layouts either live here or inside the template
│   └── partials  # I include any override/project-only layouts here to enhance what's not already in the template 
├── public  # don't worry about this folder if you are using my deployment set-up
├── resources  # where resources is stored
│   └── _gen
│       ├── assets
├── static  # static files directory
└── themes  # the theme you are using. e.g. here I am using the PaperMod theme. 
    └── PaperMod
        ├── assets
        │   ├── css
        │   │   ├── common
        │   │   ├── core
        │   │   ├── extended
        │   │   └── hljs
        │   └── js
        ├── i18n
        ├── images
        └── layouts
            ├── _default
            │   └── _markup
            ├── partials
            │   └── templates
            └── shortcodes

29 directories

```

## See Also

- [Everything Hugo]({{< ref "posts/hugo/hugo.md" >}})
    - [Set up a Hugo website in 5 minutes?]({{< ref "posts/hugo/setups.md" >}})
    - [Deploy your Hugo website using the latest AWS tools?]({{< ref "posts/hugo/deploy.md" >}})
    - [Add a comment widget to your website to received feedbacks?]({{< ref "posts/hugo/comments.md" >}})
    - [How does Google Analytics work and how to add one to your website?]({{< ref "posts/hugo/google_analytics.md" >}})
    


