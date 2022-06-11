---
title: "Hugo 2 - Deploy to AWS"
date: 2022-05-16
draft: false
weight: 101
tags: ['hugo']
TocOpen: true
ShowPostNavLinks: true
---

## Overview

**Amplify** integrates nicely with **GitHub**, which makes the whole
experience much better. 

I used this [walk-through](https://gohugo.io/hosting-and-deployment/hosting-on-aws-amplify/) to set up my site, which automatically
deploys changes from my `main` branch.

I then registered and purchased my own domain from **AWS Route53**, and linked my domain with my amplify app using the 
**Domain Management** tool in **Amplify**.

Costs have been about $0.5 per month and under $9 per year for the domain name.

In my GitHub Project [README](https://github.com/21han/blog/#readme), I have added
the Amplify OneClick button so that I can quickly navigate to the console
to track my deployment process. 

```markdown
## 🚀🚀🚀
[![amplifybutton](https://oneclick.amplifyapp.com/button.svg)](https://us-east-1.console.aws.amazon.com/amplify/home?region=us-east-1#/d1i779b6k8afpv)
```


![](https://user-images.githubusercontent.com/22876277/173204318-383ddd40-9a3a-4d66-89de-f422465fbf0b.png)


## See Also

- [Everything Hugo]({{< ref "posts/hugo/hugo.md" >}})
    - [Set up a Hugo website in 5 minutes?]({{< ref "posts/hugo/setups.md" >}})
    - [Deploy your Hugo website using the latest AWS tools?]({{< ref "posts/hugo/deploy.md" >}})
    - [Add a comment widget to your website to received feedbacks?]({{< ref "posts/hugo/comments.md" >}})
    - [How does Google Analytics work and how to add one to your website?]({{< ref "posts/hugo/google_analytics.md" >}})
    