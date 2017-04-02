---
layout: post
title: "How to remap or swap special keyboard keys in Linux?"
date: 2017-03-31 08:38:46
author: Sarad Gajurel
categories:
- blog
- Linux
img: linux-remap.png
thumb: linux-remap.jpg

---

If you are using Linux on MacBook or a key on your keyboard is broken or you have a special key on your keyboard and you want to use it differently than it is designed then you may feel the need to remap the keys of your keyboard. Remapping the keys means changing the input behaviour of your keyboard and making it work as we want, not as it was intended. In this post you will learn to remap the keys on Linux using 'xkb', which is pre-installed on most of the linux distros. If you want to remap the keys in Windows then you can follow <a href="/blog/windows/remap-key-in-windows"> this post.</a>  <!--more-->

The 'Delete' key is broken in my laptop so I am going to remap it to 'Insert' key. The procedure is same for other keys as well which is as follows:

<b>Step 1</b>: Edit the following file where 'xkb' stores the mapping of special keys:

	sudo nano /usr/share/X11/xkb/symbols/pc

<b>Step 2:</b> Find the lines of the keys which are to be remapped:

	key  <INS> {	[  Insert		]	};
	key <DELE> {	[  Delete		]	};

<b>Step 3:</b> Remap the key behaviour by changing its action:

	key  <INS> {	[  Delete		]	};
	key <DELE> {	[  Insert		]	};

<b>Step 4:</b> Press 'Ctrl+O' to save and press enter then press 'Ctrl+X' to exit the nano editor.

<b>Step 5:</b> Clear the 'xkb' cache with following command:
	
	sudo rm -rf /var/lib/xkb/*

<b>Step 6:</b> Finally quit the session and re-login.

Now you have successfully changed your keymap. If you faced any trouble modifying your keymap or need any assistance comment below and I'll help you solving your problem. If you find it useful and think it will help other as well you can share the article on your favorite social media.