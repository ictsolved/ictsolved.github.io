---
layout: post
title: "How to setup SkyPro/EVDO, NCELL Connect, UTL Modem/USB Dongle in Linux?"
description: Setting up USB dongle for internet access in Linux is easier when done correctly. Connect your USB modem into the computer and open a terminal. Input the following command to enable the USB modem first.
date: 2016-10-20 06:04:46
author: sarad
categories:
- blog
- Linux
keywords: skypro, evdo, ncell, linux modem, linux gsm modem, linux 4g usb modem, linux lte modem
generes: modem
img: 2016-10-20-connect-usb-dongle-modem-in-linux/modem-linux.jpg
imagealt: connect usb dongle to linux
thumb: 2016-10-20-connect-usb-dongle-modem-in-linux/modem-linux_thumb.jpg
redirect_from:
  - /blog/linux/connect-usb-dongle-modem-in-linux
---

Linux users are growing gradually in Nepal and mostly there are either IT students or IT professionals who use Linux in the context of our country. Every Linux user who was used to with Windows knows the hassle of migrating from Windows to Linux. Most of the companies target softwares for Windows and hence software availability becomes an ache for the general users. Our mobile broadband ISPs also constitute application for windows but not for Linux. This article will guide you through the setup process of using an USB Dongle/Modem in Linux. <!--more-->

Here I am using NTC SKyPro EVDO setup but you can follow the similar procedures for NCELL connect and UTL too. Let's jump into the steps without any delay.

<u><b>Steps:</b></u>

1. Plug in your <i>USB Dongle</i> and let it initialize for first 10 seconds. Now Open <i>Settings</i> of your Linux distribution and click on <i>Network</i>. If there is <i>Mobile Broadband</i> in the Network Manager skip to step 5 else continue to step 2. In my case <i>Mobile Broadband</i> did not appear.

	<img src="/assets/img/blog/2016-10-20-connect-usb-dongle-modem-in-linux/modem0.jpg" alt="Network-manager">

2. Unplug your <i>Dongle</i> then open up terminal and input following command:
	
		udisksctl status

	<img src="/assets/img/blog/2016-10-20-connect-usb-dongle-modem-in-linux/modem01.jpg" alt="udisksctl-status">

3. Now connect your <i>Dongle</i> and issue the same command again and note the <i>DEVICE</i> name that is newly added in the list, mine is <i>sr1</i>.

	<img src="/assets/img/blog/2016-10-20-connect-usb-dongle-modem-in-linux/modem02.jpg" alt="modem-added-in-the-list">

4. In the terminal, issue following command replacing <i>sr1</i> with <i>DEVICE</i> name you noted in step 2:
		
		sudo udisksctl power-off -b /dev/sr1

	Enter the following command and you should see that <i>DEVICE</i> name has been changed to something else than before. My device name changed to <i>sdb</i>.

	<img src="/assets/img/blog/2016-10-20-connect-usb-dongle-modem-in-linux/modem03.jpg" alt="sr1-powered-off">

5. Now wait for about 10 seconds to complete device initialization and refresh the <i>Network<i/> window. Now the <i>Mobile Broadband</i> should appear in the list. If it is still not seen enter the following command:

		 sudo service network-manager restart

	<img src="/assets/img/blog/2016-10-20-connect-usb-dongle-modem-in-linux/modem05.jpg" alt="Network-manager">

	Click on <i>Mobile Broadband</i> from the network menu, then choose <i>Add new connection</i> from drop-down list and click on the setting icon at the bottom.

6. On the next window, click <i>Next</i>.

	<img src="/assets/img/blog/2016-10-20-connect-usb-dongle-modem-in-linux/modem06.jpg" alt="setting-up-broadband">


7. Choose Nepal from the country list and click on <i>Next</i>.

	<img src="/assets/img/blog/2016-10-20-connect-usb-dongle-modem-in-linux/modem07.jpg" alt="country-list">


8. Choose <i>I can't find my provider and I wish to enter it manually:</i> and give a name for the connection then click <i>Next<i/>

	<img src="/assets/img/blog/2016-10-20-connect-usb-dongle-modem-in-linux/modem08.jpg" alt="naming-connection">


9. Click on <i>Apply</i> to save your new connection.

	<img src="/assets/img/blog/2016-10-20-connect-usb-dongle-modem-in-linux/modem09.jpg" alt="saving-connection">


10. Click on the setting icon that is at the bottom to set your credentials for connection.

	<img src="/assets/img/blog/2016-10-20-connect-usb-dongle-modem-in-linux/modem9_1.jpg" alt="setting-credentials">


11. In case of NTC SkyPro/EVDO and UTL, enter the following credentials:

			Number: #777

			Username: Mobile_Number

			Password: Mobile_Number

	In case of NCELL Connect enter following credentials:

		Number: *99***1#

		Leave username and password field blank.

	<img src="/assets/img/blog/2016-10-20-connect-usb-dongle-modem-in-linux/modem10.jpg" alt="user-pass">


12. Your connection is now ready so click on the <i>Network icon</i> of your task panel and click on <i>Connect</i> under <i>Mobile Brandband</i>.

	<img src="/assets/img/blog/2016-10-20-connect-usb-dongle-modem-in-linux/modem11.jpg" alt="Connection-network">


13. After the network is successfully connected, you will see two changes. First there will be signal bars on the task panel which shows you the power or signal strength of the connection and second one is in the <i>Network</i> window there will be information of your connection.

	<img src="/assets/img/blog/2016-10-20-connect-usb-dongle-modem-in-linux/modem12.jpg" alt="connected">


Hope this helps you to setting up your connection of USB Dongle in Linux. If you got stuck on any step or your having any problem, feel free to comment and also don't forget to share your experience setting up USB Dongle connection in Linux.