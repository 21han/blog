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


{{<gist 21han 6ffd77c3e3a3370ce49eece9e34f8691 livereload_1.go>}}

Basically, this is achieved using a local WebSocket connection from here. This is all based on the wonderful [Gorilla 
Websocket Package](https://github.com/gorilla/websocket)

{{<gist 21han 6ffd77c3e3a3370ce49eece9e34f8691 livereload_2.go>}}


### What makes Hugo so secure?


#### Overview

Just because Hugo is an SSG doesn't guarantee it is secure. There are numerous other SSGs out there, but Hugo differs from
others because of its usage of **virtual file system** and **strict default security policy** to ensure runtime security.

The most hardcore way to secure the runtime is to **sandbox** it. What this means is that Hugo uses [spf13/afero](https://github.com/spf13/afero)
as its File System abstraction layer, and no third-party components can mount files outside the root.


#### Security Policy

{{<gist 21han 6ffd77c3e3a3370ce49eece9e34f8691 securityConfig.go>}}


For example, in the code chunk above, Hugo's built-in security policy is to restrict access to `os.Exec`, certain
template functions that aren't completed trusted.


#### Dependency Security

Because all dependencies are managed by [Modules](https://github.com/golang/go/wiki/Modules). Hugo takes advantages
of its `go.sum` which basically checks if your downloaded binary matches the expected cryptographic checksums of the 
version. More readings on this can be found [here](https://github.com/golang/go/wiki/Modules)


### Understanding content structure

{{<gist 21han 6ffd77c3e3a3370ce49eece9e34f8691 tree.txt>}}


## See Also

- [Everything Hugo]({{< ref "posts/hugo/hugo.md" >}})
    - [Set up a Hugo website in 5 minutes?]({{< ref "posts/hugo/setups.md" >}})
    - [Deploy your Hugo website using the latest AWS tools?]({{< ref "posts/hugo/deploy.md" >}})
    - [Add a comment widget to your website to received feedbacks?]({{< ref "posts/hugo/comments.md" >}})
    - [How does Google Analytics work and how to add one to your website?]({{< ref "posts/hugo/google_analytics.md" >}})
    


