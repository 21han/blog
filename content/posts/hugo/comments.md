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

## Comment 2.0

Utterances is great! But I also wanted to add social reactions to my blog.

Plus, not everyone has GitHub, so my comment system is fairly limited if I were to continue
using Utterances. After some googling, I decided to switch over to Disque.

In order to change over:

1. I created an account on Disqus
2. I signed up for the free tier plan
3. Install Disque to your web app, I chose "manual" option, which generated the following code
4. I placed the following code under `<root>/layouts/partials/comments.html`

```html
<div id="disqus_thread"></div>
<script>
    /**
     *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
     *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables    */
    /*
    var disqus_config = function () {
    this.page.url = PAGE_URL;  // Replace PAGE_URL with your page's canonical URL variable
    this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
    };
    */
    (function () { // DON'T EDIT BELOW THIS LINE
        var d = document, s = d.createElement('script');
        s.src = 'https://www-guozihan-link.disqus.com/embed.js';
        s.setAttribute('data-timestamp', +new Date());
        (d.head || d.body).appendChild(s);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by
    Disqus.</a></noscript>
```

5. I have added the following code chunk to the end of the above file in hope to remove any ads that Disque places

```html
<script id="dsq-count-scr" src="//www-guozihan-link.disqus.com/count.js" async></script>
<script>(function ($) {
    setInterval(() => {
        $.each($('iframe'), (arr, x) => {
            let src = $(x).attr('src');
            if (src && src.match(/(ads-iframe)|(disqusads)/gi)) {
                $(x).remove();
            }
        });
    }, 300);
})(jQuery);</script>
```

## See Also

- [Everything Hugo]({{< ref "posts/hugo/hugo.md" >}})
    - [Set up a Hugo website in 5 minutes?]({{< ref "posts/hugo/setups.md" >}})
    - [Deploy your Hugo website using the latest AWS tools?]({{< ref "posts/hugo/deploy.md" >}})
    - [Add a comment widget to your website to received feedbacks?]({{< ref "posts/hugo/comments.md" >}})
    - [How does Google Analytics work and how to add one to your website?]({{< ref "posts/hugo/google_analytics.md" >}})
    