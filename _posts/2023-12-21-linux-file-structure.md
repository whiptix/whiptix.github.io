---
layout: post
title: Linux File Hierachy Standards
tags: [Linux, FHS]
author : Christopher Githui
---
 Given that today 90% of all cloud infrastructure and over 70% of handheld and smart devices are powered by Linux. It is therefore wise for a software engineer to farmiliarize with [Linux Commands](https://whiptix.github.io/2023/12/20/linux-fundamentals.html 'Linux Commands') and understand the Linux Standard File Hierachy System (FHS). 
 In order to support interoperability of applications, ease of administration, and the ability to implement cross-distro applications reliably, the Linux foundation maintains a prescriptive standard that guides the organisational layout of directories.

 In this article, we will highlight the various directories prescribed in the Linux file heirachy system standard. We will then explore these directories and where to look for various components in your server environment. 
 
 The linux file system is organized in a single tree, regardless of how many devices are incoporated as depicted below : -

 ![fhs](/assets/img/fhs.png){:class="img-responsive" height="600px" width="400px"}

## /
This is the root directory, unlike windows where each hard drive or storage space is represented as it own file system (Typically Labelled with a Letter i.e. C:, D:). in linux, every file and device on the system resides under one directory **the root directory** which is the top level directory of the entire system and has all other directories inside it.
>Note: This is different from the default administrative user, which is also called “root”. It is also different from the default administrative user’s home directory, which is located at “/root”.

## /boot
This directory contains the core components that actually allow the system to boot this are the actual files, images and kernels necessary to boot the system. 

## /bin 
This directory contains basic commands and programs that are needed to achive a minimal working environment upon booting. The ***ls***, ***pwd***, ***cd*** etc reside here.
These basic commands are kept separate from some of the other programs on the system to allow you to boot the system for maintainance even if other parts of the filesystem may be damaged or unavailable.
>Note these commands are available to all users of the system.

## /sbin 
This directory is similar to /bin in that, it contains programs deemed essential for using the operating system the only difference is that it contains commands that are only available to system administrators. The commands that are located in this directory are used in booting, restoring, recovering and/or reparing the system. For example **arp**, **clock**, **halt**, **init**, **ifconfig** etc.

## /lib
This directory is used for all of the shared system libraries(files that basically provide functionality to the other programs on the system) that are required by the **/bin** and **/sbin** directories.

## /media
This directory provides a location to mount removable media(e.g DVDs) therefore in a server environment this directory may not be used.

## /mnt
This directory is reserved for temporarily mounted file systems such as NFS file system mounts e.g. external harddrives.
>Note This directory must not be used by installation programs.

## /opt
This directory is used to store optional packages i.e packages and applications that were not installed from the repositories. It provides storage for large, static application software packages. If an application stores its files in the **/opt** directory it creates a directory bearing the same name as the package e.g ***sample*** will create ***/opt/sample/bin***.

## /home
This Location contains the home directories of all the users on the system (except the root user whose home directory is **/root**). A regular user typically has a directory bearing the username at this directory to which the user has white access this ensures that not just anyone can change important configuration files.

## /etc
This directory is reserved for configuration files that are local to the machine. No binaries are to be placed in this location.

## /usr

## /run
## /svr
## /tmp
## /proc
## /sys
## /dev
## /var
## /root


