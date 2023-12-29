---
layout: post
title: Linux File Hierachy Standards
tags: [Linux, FHS]
author : Christopher Githui
---
Given that today 90% of all cloud infrastructure and over 70% of handheld and smart devices are powered by Linux. It is therefore wise for a software engineer to farmiliarize with [Linux Commands](https://whiptix.github.io/2023/12/20/linux-fundamentals.html 'Linux Commands') and understand the Linux Standard File Hierachy System (FHS). 

In order to support interoperability of applications, ease of administration, and the ability to implement cross-distro applications reliably, the Linux foundation maintains a prescriptive standard that guides the organisational layout of directories.

In this article, we will highlight the various directories prescribed in the Linux file heirachy system standard. We will then explore these directories and where to look for various components in your server environment. 


# Introduction
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
This directory is reserved for configuration files that are local to the machine. No binaries are to be placed in this location. Idealy this id the directory where you will create a service and store the service configuration file.

## /usr
This directory is used to store all non-essential programs, their manuals, libraries and other data that is not required for minimal usage of the system. This means that it contains similar sets of folders to those in the **/** directory, such as **/usr/bin** , **/usr/sbin**, **/usr/lib**. This directory also contains **/usr/local** which ia similar to the **/opt** directory, however this directory is used for software that is local to the machine. Another interesting directory that resides here is the **/usr/share** directory, which contains documentation, configuration files, and other useful files.

## /run
This directory is used by the operating system to write temporary runtime information suring the early stages of the boot process.

## /srv
This directory is used to contain data files for services provided by the computer such as FTP,WWW, or CVS. In most cases, this directory is not used too much because its functionality can be implemented elsewhere in the filesystem.

## /tmp
This directory as the name suggests it is used to store temporary files that should not persist upon reboot as the files stored in this location will be automatically deleted once the system shuts down.

## /proc
This directory contains special files that either extracts information from or send information to the Kernel therefore the files stored in this directory reflects the internal state of the linux kernel. This means that you can check and modify different infomation from the kernel itself in realtime for example we can get detailed information about memory usage by typing   ``` cat /proc/meminfo``` 
## /sys
This directory contains information similarly held in **/proc**, but displays a hierarchical view of specific device information in regards to hot plug devices.
To see how certain USB and FireWire devices are actually mounted, refer to the ***/sbin/hotplug*** and ***/sbin/udev*** man pages.

## /dev
This directory contains files which represent devices that are attached to the system.Every hard drive, terminal device, input or output device available to the system is represented by a file here. Depending on the device, you can operate on the devices in different ways.
For instance, for a device that represents a hard drive, like /dev/sda, you can mount it to the filesystem to access it. On the other hand, if you have a file that represents a line printer like /dev/lpr, you can write directly to it to send the information to the printer.

## /var
This directory is supposed to store variable data that is, data that you expect to grow as the system is used, this includes spool directories and files, administrative and logging data, and transient and temporary files.  

## /root
This is the home directory of the administrative user (called ***“root”***). It functions exactly like the normal home directories, but is housed here instead.

# Conclusion
Having Highlighted the different directories and what they contain in general. It is important to note that the same can vary from distro to distro. Therefore for better understanding of the distro you are using simply traverse the various directories and try to find out what the files inside are for. Better yet you can use this command ***man hier*** to view the built in manual pages for what each directory is for.
