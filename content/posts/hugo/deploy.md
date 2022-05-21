---
title: "Hugo 2 - Deploy to AWS"
date: 2022-05-16
draft: false
weight: 101
tags: ['hugo', 'AWS', 'Amplify']
TocOpen: true
ShowPostNavLinks: true
---

**Amplify** integrates nicely with **GitHub**, which makes the whole
experience much better. 

I used this [walk-through](https://gohugo.io/hosting-and-deployment/hosting-on-aws-amplify/) to set up my site, which automatically
deploys changes from my `main` branch.

I then registered and purchased my own domain from **AWS Route53**, and linked my domain with my amplify app using the 
**Domain Management** tool in **Amplify**.

Costs have been about $0.5 per month and under $9 per year for the domain name.
