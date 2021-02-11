---
layout: post
date: 2021-02-11 19:09:42 +0545
author: sarad
tags:
- Blogging
title: Configure Custom Domain and Sub-domain with GitHub Pages in Cloudflare
description: If you have already registered for a domain and you want your GitHub
  pages site to be hosted in the sub-domain, you have to make these configurations
  in Cloudflare.
keywords: ''
img: ''
thumb: ''
imagealt: ''

---
I started blogging with GitHub pages as a hobby and wrote few articles. I had also integrated Google Analytics so I noticed that some of my posts were gaining more organic traffic than I expected. I then decided to use custom domain for my blog so that it would help to create a brand value. Few months later, I created another static portal and decided to host it in the GitHub pages but in the sub-domain. At first, I faced some issue but after some hit-and-trial in Cloudflare, I succeeded to linking another portal in the sub-domain. In this article, I will show how you can configure a custom domain as well as sub-domian for your GitHub pages in Cloudflare.

### Step 1

The first step is to host your site in GitHub Pages and make sure it is accessible at https://username.github.io or https://username.github.io/repo. Also register for a custom domain, if you have not already registered.

### Step 2

Once your site is up and running on GitHub pages and you have your custom domain, head towards [https://www.cloudflare.com/](https://www.cloudflare.com/ "Cloudflare"), sign up for an account if you are not already registered. After you login, you will see following page. 