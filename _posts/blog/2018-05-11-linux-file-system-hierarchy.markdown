---
layout: post
title: "Purpose of each Directory inside Root Partition in Linux"
description: Linux or Unix-like operating systems are based on it's own Filesystem Hierarchy Standards (FHS). Each directory has it's own purpose. This article will talk about the purpose of these directories.
date: 2018-05-11 14:04:46
author: sarad
categories:
- blog
- Linux
tags: fhs, linux directories
generes: linux
img: 2018-05-11-linux-directories.jpg
imagealt: list of directories in linux
thumb: 2018-05-11-linux-directories.jpg
---

If we take a look at the root directory of a Linux or Unix-like operating system, we can see numbers of directories present inside it. But have you ever thought what is those each directory intended to do? We call it Linux File System Hierarchy Standards (FHS). In this post, <!--more--> we are going to discuss briefly all those directories.

    Note: This article is updated on 2018 May 27 and is based on FHS 3.0.

#### /
We call it root directory or root of the filesystem. This is the parent directory of the Linux Operating System. Path for all the files or directory existing in the system starts from the root directory.

#### /bin, /sbin
In FHS 3.0, these are symlinks which point to /usr/bin. For the scripts and binaries referencing to these legacy paths, these symlinks help to find their binaries correctly.

#### /boot
The boot partition or EFI System Partition (On EFI Systems) is mounted in this directory. It contains bootloader and its related files. The files inside this directory are used during the startup of the system. Common examples of file present inside this directory are kernel images, boot loaders like grub etc.

#### /dev
This is a root directory for device nodes. A number of special purpose virtual file systems might be mounted below this directory.

#### /etc
This directory is intended for system-specific configuration. It frequently includes configuration files supplied by the vendor. Also if the configuration is missing for any application, should fall back to defaults.

#### /home
This is the location for home directories of normal users. Home directories have write permission for the users and are generally used to store files and personal configurations.

#### /lib
This is also a symlink in FHS 3.0 that points to /usr/lib. The programs referencing to this legacy path can find thier resources correctly with the help of this symlink.

#### /lib64
It is also a symlink and exists only on architectures whose ABI places the dynamic loader in this path. Binaries referencing this legacy path find their dynamic loader correctly through this symlink.

#### /mnt
This directory is usually used to mount the filesystems temporarily. For example, a hard drive /dev/sda with partition /dev/sda1 can be mounted inside this directory to access the files present in /dev/sda1.

#### /opt
This directory generally stores the files of those installed applications which are not in the official repository. For instance, if we install lampp server then it is stored inside /opt/lampp.

#### /proc
It is a virtual kernel file system that exposes the process list and other functionality. This file system is mostly an API to interface with the kernel. A number of special purpose virtual file systems might be mounted below this directory.

#### /root
It is a home directory of the root user. It is located outside of /home directory to enable root user log in to the system even if /home is not mounted.

#### /run
It is a "tmpfs" filesystem where system packages place runtime data. During the boot, this directory is flushed and write permission is granted to privileged programs only.

#### /srv
This directory stores general server payload and is managed by the administrator. Generally, it is writable and possibly shared among systems.

#### /sys
It is a virtual kernel file system that exposes the discovered devices and other functionality. This file system is mostly an API to interface with the kernel. A number of special purpose virtual file systems might be mounted below this directory.

#### /tmp
This directory is intended for temporary storage of small files. This directory is usually flushed during the system boot.

#### /usr
This directory contains operating system resources supplied by the vendor. This directory should not be modified by the administrator, except when installing or removing vendor-supplied packages.

#### /var
This directory stores persistent, variable system data. It might contain vendor-supplied data. Applications should be able to reconstruct necessary files and directories in this subhierarchy.

This is the quick lookup of the filesystem hierarchy of a Linux or Unix-like system. We only discussed the basics but there are much more things which cannot be covered in a single blog. There are even subdirectories (subhierarchy) inside this hierarchy for their specific purposes. If you are interested to learn more about the Linux Filesystem Hierarchy then you can issue "man file-hierarchy" command without quotes in your terminal or visit [FHS 3.0 link. <i class="fa fa-external-link" aria-hidden="true"></i>](http://refspecs.linuxfoundation.org/FHS_3.0/fhs-3.0.html){:target="_blank"}. If you have any query or would like to add up, you can share your thoughts in the comment section.