---
layout: post
title: Development Environment Setup
author : Christopher Githui
---

As a software developer or one aspiring to be, there will be a need to setup a software development environment. This would always require the developer to have following:-
1. A working PC / Laptop
2. Internet Connection

There may be more to it, However, for starters that's pretty much what you need. 
Linux maybe the best operating system for Software development. However, Windows is a popupar and user friendly option therefore, in this article we will focus on setting up our linux development environment on a windows pc.

We will proceed and setup windows subsystem for linux(wsl) which will enable us to install a Linux distribution(such as Ubuntu, OpenSUSE, Kali, Debian, Arch Linux, etc), this is to enable newbies or windows enthusiast get a feel of the linux environment which will be used in many production environments. 

> NOTE: You must be running Windows 10 version 2004 and higher or Windows 11 to use the commands 

### Installing wsl
 we are going to install Oracle Linux 9 distribution, by default wsl installs ubuntu linux distribution. To install 

```
  wsl --list --online
```
![wsl-list](/assets/img/wsl_list.png){:class="img-responsive"}

  choose the linux distribution Oracle Linux 9.1 and install

```
  wsl --install -d OracleLinux_9_1
```
![install](/assets/img/install.png){:class="img-responsive"}

  setup your username.

![username](/assets/img/username.png){:class="img-responsive"}

  setup a strong password.

![password](/assets/img/password.png){:class="img-responsive"}

  to access the linux environment, open command prompt and type

```
  bash 
```

Now that we have our linux environment setup, one may be tempted to ask what are the next steps? well we recommend that you farmiliarize with linux by reading [Linux fundamentals](https://whiptix.github.io/2023/12/20/linux-fundamentals.html 'Linux fundamentals'), then explore the different [Career Paths](https://whiptix.github.io/2023/12/21/career-paths.html 'Career Paths').




