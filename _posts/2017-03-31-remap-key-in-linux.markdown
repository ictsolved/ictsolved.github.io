---
layout: post
title: "How to remap or swap special keyboard keys in Linux?"
description: Remapping keyboard keys in Linux can be performed by following two methods. If a key is broken or you need to change the functionality of certain key, keyboard remapping is necessary. You can tweak the keys to function differently with following command.
date: 2017-03-31 08:38:46
author: sarad
categories:
- blog
- Linux
img: linux-remap.jpg
imagealt: linux keyboard remap
thumb: linux-remap.jpg
redirect_from:
  - /blog/linux/remap-key-in-linux
---

If you are using Linux on MacBook or a key on your keyboard is broken or you have a special key on your keyboard and you want to use it differently than it is designed then you may feel the need to remap the keys of your keyboard. Remapping the keys means changing the input behaviour of your keyboard and making it work as we want, not as it was intended. In this post you will learn to remap the keys on Linux using 'xmodmap' and 'xkb' which are pre-installed on most of the linux distros. If you want to remap the keys in Windows then you can follow <a href="/blog/windows/remap-key-in-windows"> this post.</a>  <!--more-->

The 'Delete' key is broken in my laptop so I am going to remap it to 'Insert' key. The procedure is same for other keys as well. There are two methods for doing this, first method is safe and recommended method but if first method does not work then go for second method which includes modifying the system file and is not preferred. The steps are as follows:

<b><u>First Method:</u></b> Safe and recommended method

<b>Step 1:</b> Find the KeyCode (number assigned to key) and Keysym (name of key) for your desired keys to swap

	xmodmap -pk

In my case 118 is KeyCode for Insert key and 119 is for Delete key.

<b>Step 2:</b> Swap the keys by issuing following command:

	xmodmap -e "keycode 118 = Delete"
	xmodmap -e "keycode 119 = Insert"

Now your keys are swapped but this action is not persistent and only works until you reboot. If you want to make your changes persistent then you need to write a script and make it auto execute at startup or you can make a .desktop file and make it run at every startup. I prefer .desktop approach.

<b>Step 3:</b> Create "swap.desktop" file and put it into ~/.config/autostart with following contents in it:

	[Desktop Entry]
	Name=Swap
	Exec=xmodmap -e "keycode 118 = Delete" && xmodmap -e "keycode 119 = Insert"
	Terminal=false
	Type=Application

<b>Step 4:</b> Now make it executable

	chmod +x ~/.config/autostart/swap.desktop

This way the .desktop file will auto start on every boot and the keys are swapped.

<b><u>Second Method:</u></b> If the above method does not work then you can try this method but please be aware that this method modifies the system file so do not mess with the system file and do it carefully.

<b>Step 1:</b> First we will create a backup of the file in case anything goes wrong so that we can restore it later.

	sudo cp /usr/share/X11/xkb/symbols/pc /usr/share/X11/xkb/symbols/pc.bak

<b>Step 2:</b> Edit the following file where 'xkb' stores the mapping of special keys:

	sudo nano /usr/share/X11/xkb/symbols/pc

<b>Step 3:</b> Find the lines of the keys which are to be remapped:

	key  <INS> {	[  Insert		]	};
	key <DELE> {	[  Delete		]	};

<b>Step 4:</b> Remap the key behaviour by changing its action:

	key  <INS> {	[  Delete		]	};
	key <DELE> {	[  Insert		]	};

<b>Step 5:</b> Press 'Ctrl+O' to save and press enter then press 'Ctrl+X' to exit the nano editor.

<b>Step 6:</b> Clear the 'xkb' cache with following command:

	sudo rm -rf /var/lib/xkb/*

<b>Step 7:</b> Finally quit the session and re-login.

Now you have successfully changed your keymap. If you get any unexpected result with this method then restore the backup we created earlier with following command and repeat Step 6 and 7.

	sudo mv /usr/share/X11/xkb/symbols/pc.bak /usr/share/X11/xkb/symbols/pc

 If you faced any trouble modifying your keymap or need any assistance comment below and I'll help you to solve your problem. If you find it useful and think it will help others as well you can share the article on your favorite social media.
