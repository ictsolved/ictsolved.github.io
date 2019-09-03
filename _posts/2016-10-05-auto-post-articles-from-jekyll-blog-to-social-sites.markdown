---
layout: post
title: "Post articles from jekyll to Twitter, Facebook and LinkedIn automatically"
description: Automaticaly posting the new articles published on blog to social media in Jekyll can be obtained with IFTTT. Put jekyll-feed plugin inside your _config.yml file and in the head section of your html file, put the feed_meta code.
date: 2016-10-04 05:54:46
author: sarad
categories:
- blog
- Blogging
keywords: auto post jekyll, automatically post to facebook from website, jekyll auto post to facebook, auto post blog to social networks, jekyll auto post to facebook page, jekyll auto post to facebook group, auto post to social media from jekyll, auto post share
generes: jekyll
img: 2016-10-05-auto-post-articles-from-jekyll-blog-to-social-sites/autopost-blog-to-social-site-0.png
imagealt: auto post jekyll posts to social media
thumb: 2016-10-05-auto-post-articles-from-jekyll-blog-to-social-sites/ifttt0_thumb.png
redirect_from:
  - /blog/blogging/auto-post-articles-from-jekyll-blog-to-social-sites
---
In this article I am going to show how to auto post your articles from Jekyll blog that is hosted on github pages or any other hosting site, to your Facebook, Twitter and LinkedIn account. Since jekyll is a static site and it does not have any plugin that automatically posts your article to the social networks we need to follow this process in order to succeed. <!--more-->

I am going to show you the steps of setting up the Twitter but it is similar if you want to setup Facebook or LinkedIn. So lets move on to the steps:

<b>1. First you need to enable "Jekyll Feed Plugin" in your site. In order to do that, add this line to your site's _config.yml:</b>

	plugins:
	  - jekyll-feed

Please note that _config.yml does not support "TAB" so use "white space" for indentation.

<b>2. Now place following line inside the <head> section of your template which is probably inside "_include/head.html".

<pre>&#123;% feed_meta %}</pre>

This plugin will automatically generate an Atom feed at "/feed.xml" or "_site/feed.xml", if you are running locally.

<b>3. Go to [IFTTT <i class="fa fa-external-link" aria-hidden="true"></i>](https://ifttt.com/){:target="_blank"} and sign-up for an account.</b>

<img src="/assets/img/blog/2016-10-05-auto-post-articles-from-jekyll-blog-to-social-sites/autopost-blog-to-social-site-1.jpg" alt="IFTTT sign-up">

<b>4. After creating an account, you will see the page similar to the image below except your recipes will be empty.</b>

<img src="/assets/img/blog/2016-10-05-auto-post-articles-from-jekyll-blog-to-social-sites/autopost-blog-to-social-site-2.jpg" alt="IFTTT creating recipe">

<b>Click on Create a Recipe and the following page appears. We have to set a trigger so click on the link "this" which is underlined and highlighted with a cyan colour.</b>

<img src="/assets/img/blog/2016-10-05-auto-post-articles-from-jekyll-blog-to-social-sites/autopost-blog-to-social-site-3.jpg" alt="IFTTT trigger">

<b>5. To choose the trigger channel, type "feed" in search bar and the result with orange RSS feed icon shows up. Click that icon.</b>

<img src="/assets/img/blog/2016-10-05-auto-post-articles-from-jekyll-blog-to-social-sites/autopost-blog-to-social-site-4.jpg" alt="Choosing Feed">

<b>6. In the resulting page, choose "New feed item" as the trigger.</b>

<img src="/assets/img/blog/2016-10-05-auto-post-articles-from-jekyll-blog-to-social-sites/autopost-blog-to-social-site-5.jpg" alt="feed results">

<b>7. The next step is to provide link of feed.xml. If your site is hosted in Github it is probably "github_username.github.io/feed.xml" or "github_username.github.io/repo_name/feed.xml". Provide the link correctly link and click "Create Trigger".</b>

<img src="/assets/img/blog/2016-10-05-auto-post-articles-from-jekyll-blog-to-social-sites/autopost-blog-to-social-site-6.jpg" alt="feed.xml link">

<b>8. Trigger is set now. Another step is to execute action with the specified trigger so click "that" which is in cyan colour and underlined.

<img src="/assets/img/blog/2016-10-05-auto-post-articles-from-jekyll-blog-to-social-sites/autopost-blog-to-social-site-7.jpg" alt="setting action">

<b>9. In the action channel search bar type in "twitter" and click on the result that comes in.</b>

<img src="/assets/img/blog/2016-10-05-auto-post-articles-from-jekyll-blog-to-social-sites/autopost-blog-to-social-site-8.jpg" alt="action search">

<b>10. Connect twitter with IFTTT app. Since you want to auto tweet your new article choose "Post a tweet" action</b>

<img src="/assets/img/blog/2016-10-05-auto-post-articles-from-jekyll-blog-to-social-sites/autopost-blog-to-social-site-9.jpg" alt="choosing action">

<b>11. The box contains "EntryTitle" and "EntryUrl" by default but to make it look more cool, you can add your desired phrase and click next. Finally click "Create Recipe".</b>

<img src="/assets/img/blog/2016-10-05-auto-post-articles-from-jekyll-blog-to-social-sites/autopost-blog-to-social-site-10.jpg" alt="finalizing action">

Congratulations! You have successfully setup auto posting your article to twitter. Afterwards whenever you post a new article, it is fetched from the feed and is tweeted on your profile within few minutes.

Note: The URL of your posts get shortened while tweeting but if you do not want shortened URL you can change the preference by following steps:

<b>1. Click on your account name on the top right and choose Preferences</b>

<img src="/assets/img/blog/2016-10-05-auto-post-articles-from-jekyll-blog-to-social-sites/autopost-blog-to-social-site-11.jpg" alt="preferences">

<b>2. Remove check mark from "Auto shorten URLs" and click on Update settings</b>

<img src="/assets/img/blog/2016-10-05-auto-post-articles-from-jekyll-blog-to-social-sites/autopost-blog-to-social-site-12.jpg" alt="avoiding short urls">

This is all you need to do. Don't forget to share your experience on setting up IFTTT through comments.