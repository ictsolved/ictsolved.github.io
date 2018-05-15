---
layout: post
title: "Purpose of each Directory inside Root Partition in Linux"
description: Linux or Unix-like operating systems are based on it's own Filesystem Hierarchy Standards (FHS). Each directory has it's own purpose. This article will talk about the purpose of these directories.
date: 2018-05-11 14:04:46
author: sarad
categories:
- blog
- Linux
img: 2018-05-11-linux-directories.jpg
imagealt: list of directories in linux
thumb: 2018-05-11-linux-directories.jpg
---

If we take a look inside the root directory of a Linux or Unix-like operating system, we can see numbers of directories present inside it. But have you ever thought what is those each directory intended to do? We call it Linux File System Hierarchy Standards (FHS). In this post, <!--more--> we are going to discuss briefly all those directories.

#### /
We call it root directory or root of the filesystem. This is the parent directory of the Linux Operating System. All the files or directory existing in the system starts from the root directory and write privilege is provided only to the root user under this directory.

#### /bin
This directory contains systemwide binary executables. The binary contained inside /bin can be used by all users in a system. Examples of common binaries are mkdir, cp, ls etc.

#### /boot
This directory contains the bootloader and its related files. The files inside this directory are used during the startup of the system. Common examples of file present inside this directory are kernel images, boot loaders like grub etc.

#### /dev
In Linux, everything is treated as a file. Even the hard disk, USB devices, CD-ROM, disk partitions exist as files. This folder contains all the device files such as hard drive, USB etc. attached to the system. For example: /dev/sda may be a hard drive, /dev/sdb may be USB Drive.

#### /etc
This directory includes configuration files of the programs and also contains scripts to start or stop each service during startup or shutdown. Examples: /etc/locale.conf to define the locales used in the system

#### /home
This directory contains the home folders of all users in a system. Home folders are used to store personal files and personal configurations such as customizations. Example: /home/ictsolved is a home directory of user ictsolved.

#### /lib
The libraries required for the binary executables stored inside /bin and /sbin are located inside this folder. Library files generally have .so extension. For example, libmatroska.so is a library required to play .MKV files by a media player.

#### /lib64
The purpose of this directory is same as /lib but inside this directory, 64-bit library files loaded by programs are stored. This directory is not present if you are using a 32-bit Operating System.

#### /mnt
This directory is used to mount the filesystems. For example, a hard drive /dev/sda with partition /dev/sda1 can be mounted inside this directory to access the files present in /dev/sda1 partition.

#### /opt
Applications that are not present in the official repository of a Linux distribution or the third-party applications installed in the system are stored inside this directory. For instance, if we install lampp server then it is stored inside /opt/lampp.

#### /proc
This directory contains the files that hold information about the system process. It contains pseudo or virtual filesystem generally identified with Process ID (PID) in a text file. Example: /proc/cpuinfo contains information about the CPU used in the system.

#### /root
Like home directory, this directory is used to store files and configurations but only for the root user.

#### /run
This directory contains runtime information of daemons that are started during the initial boot phase. For example, fsck to check the filesystem, mount to mount the file system are stored here.

#### /sbin
It is similar to /bin directory as it also contains the binary executables but only available to the root user and mostly used for system administration purpose. mkfs is an example of a file stored here which is used to build a filesystem.

#### /srv
This directory contains the location of data files for particular service in a system. The site-specific data structured under protocols such as ftp, www, cvs etc which is served by the system are stored here.

#### /sys
Similar to /proc, it is also a virtual filesystem which stores information about kernels and connected hardware as well as allows modifying them.

#### /tmp
This directory is intended for temporary storage of files and may be used for creating lock file by many programs. Most of the files inside this directory get deleted during shutdown or boot time.

#### /usr
Many newbie Linux user pronounces it as a User directory but actually, it's called Universal System Resources. The main contents of this directory are user binaries, their documentation (man pages) and libraries, source files of programs, etc. 

#### /var
This directory is used to store the data that changes frequently or is variable in nature such as log files, font caches, crash reports etc.

This is the quick lookup of the filesystem hierarchy of a Linux or Unix-like system. We only discussed the basics but there are much more things which cannot be covered in a single blog. There are even subdirectories inside this hierarchy for their specific purposes. If you are interested to learn more about the Linux Filesystem Hierarchy then you can visit [this site <i class="fa fa-external-link" aria-hidden="true"></i>](https://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html){:target="_blank"}. If you have any query or would like to add up, you can share your thoughts in the comment section.