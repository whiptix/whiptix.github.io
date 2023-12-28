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
This is the root directory, unlike windows where each hard drive or storage space is represented as it own file system (Typically Labelled with a Letter i.e. C:, D:). in linux, every file and device on the system resides under the root directory.

