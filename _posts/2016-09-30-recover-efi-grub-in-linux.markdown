---
layout: post
title: "Recover Grub of EFI System in Linux"
description: Recovering GRUB is an easy task and it can be done quickly by following these steps. Prepare your Live bootable linux media and get your hands ready to issue the command to the terminal.
date: 2016-09-30 03:16:46
author: sarad
categories:
- blog
- Linux
keywords: fix Grub, grub rescue, repair grub, grub rescue unknown filesystem, boot repair debian, grub rescue windows 7
generes: grub
img: 2016-09-30-recover-efi-grub-in-linux/linux-grub.png
imagealt: grub screen
thumb: 2016-09-30-recover-efi-grub-in-linux/grub-thumb.png
redirect_from:
  - /blog/linux/recover-efi-grub-in-linux
  - /blog/linux/recover-grub-in-linux-efi
---

All the linux users who use distro with <b>GRUB</b> as a bootloader are aware of its value. That hard time when you power on the computer and after a brand logo the next screen just appears to show you message that GRUB was not able to load the entries. In this article, you'll get to know how to recover the GRUB bootloader on EFI/UEFI system. <!--more-->

<b>NOTE:</b> This article shows the method of recovering the GRUB only for Debian and it's derrivatives that uses 'apt-get' as package manager with EFI/UEFI systems. If your bootsector uses MBR this does not work at all.

<b>Pre-requisite:</b> Live bootable media of your Linux distro and an working internet connection

<u><b>Steps:</b></u>

1. Boot your Linux distro live

2. open the terminal

3. Find out Linux partition and EFI partition with following command:
	
		sudo fdisk -l
		
	You will see the output similar to image below:

	<img src="/assets/img/blog/2016-09-30-recover-efi-grub-in-linux/linux-fdisk.jpg" width="850" height="450" alt="list partitions with fdisk">

	Look at the 'Device' and 'Type' column. In my case, 

		/dev/sda2 is EFI System
	
		/dev/sda7 is Linux filesystem
	
	Note out your EFI System and Linux filesystem Device.

4. Now you need to execute the following commands replacing with your 'Device' accordingly:

		sudo mount /dev/sda7 /mnt
	
		sudo mount /dev/sda2 /mnt/boot/efi
	
		sudo for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
	
		sudo cp /etc/resolv.conf /mnt/etc/
	
		sudo modprobe efivars
	
		sudo chroot /mnt

		sudo apt-get update
	
		sudo apt-get install --reinstall grub-efi-amd64
	
		sudo update-grub
	
		sudo umount /mnt/boot/efi
	
		sudo umount /mnt

		exit
	
		sudo reboot
	
5. Now you are done and the grub menu should appear on reboot.

<b>NOTE:</b> If you have dual boot, another OS may not be listed in the entry so after reboot open the terminal and enter following command:

		sudo update-grub

That's all and you are good to go. Let me know through comments if you face any problem and I'll be there for you.
