---
title: "Hugo 3 - comments?"
date: 2022-05-17
draft: false
weight: 102
tags: ['hugo', 'widget', 'utterances']
TocOpen: true
ShowPostNavLinks: true
---

## Why comments?

Just to add some interactive features.

## What's out there?

Here is a [list of comment services](https://gohugo.io/content-management/comments/). 
I chose [utterances](https://github.com/utterance/utterances) because
it is free and no ads/tracking, but most importantly because it is a comment widget built on **GitHub Issues**.

Since I am a heavy GitHub user, [utterances](https://github.com/utterance/utterances) naturally becomes my first choice.


## 3 minutes integration

It takes no time to add [utterances](https://github.com/utterance/utterances) to my site. 

1. Make sure that your repo is public.
2. Install the [Utterances GitHub App](https://github.com/apps/utterances)
3. Fill this [form](https://utteranc.es/) to generate the HTML script.
4. By now, you should have something like this
    ```html
    <script src="https://utteranc.es/client.js"
            repo="[ENTER REPO HERE]"
            issue-term="pathname"
            theme="github-light"
            crossorigin="anonymous"
            async>
    </script>
    ```
5. Add this to the `layouts/partials/comments.html` file. 
6. Turn on the` comments` parameter in your `config.yml` file.
7. Verify everything works locally, and deploys your changes.