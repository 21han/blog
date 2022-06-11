---
title: "Hugo 3 - comments?"
date: 2022-05-17
draft: false
weight: 102
tags: ['hugo']
TocOpen: true
ShowPostNavLinks: true
---

## Why comments?

More fun! And a great way to encourage more discussion about the topic that you have just written about.

## What's out there?

Here is a [list of comment services](https://gohugo.io/content-management/comments/). 
Initially, I chose [utterances](https://github.com/utterance/utterances) because
it is free and no ads/tracking, but most importantly because it is a comment widget built on **GitHub Issues**.

Since I am a heavy GitHub user, [utterances](https://github.com/utterance/utterances) naturally becomes my first choice.


## 3 minutes integration

It takes no time to add [utterances](https://github.com/utterance/utterances) to my site. 

1. Make sure that your repo is public.
2. Install the [Utterances GitHub App](https://github.com/apps/utterances)
3. Fill this [form](https://utteranc.es/) to generate the HTML script.
4. By now, you should have something like this
   {{<gist 21han 648a8c1d8f02c016e506b9db41eb21bd>}}

5. Add this to the `layouts/partials/comments.html` file. 
6. Turn on the` comments` parameter in your `config.yml` file.
7. Verify everything works locally, and deploys your changes.

## Comment 2.0

Utterances is great! But I also wanted to add social reactions to my blog.

Plus, not everyone has GitHub, so my comment system is fairly limited if I were to continue
using Utterances. After some googling, I decided to switch over to Disque.

In order to change over:

1. I created an account on Disqus
2. I signed up for the free tier plan
3. Install Disque to your web app, I chose "manual" option, which generated the following code
4. I placed the following code under `<root>/layouts/partials/comments.html`

{{<gist 21han f21fe081ade9f182f9c9a3601b8b7572>}}

5. I have added the following code chunk to the end of the above file in hope to remove any ads that Disque places

{{<gist 21han 69f8fe94e11c0bac351e861d36819150>}}


## See Also

- [Everything Hugo]({{< ref "posts/hugo/hugo.md" >}})
    - [Set up a Hugo website in 5 minutes?]({{< ref "posts/hugo/setups.md" >}})
    - [Deploy your Hugo website using the latest AWS tools?]({{< ref "posts/hugo/deploy.md" >}})
    - [Add a comment widget to your website to received feedbacks?]({{< ref "posts/hugo/comments.md" >}})
    - [How does Google Analytics work and how to add one to your website?]({{< ref "posts/hugo/google_analytics.md" >}})
    