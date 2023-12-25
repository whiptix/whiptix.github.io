---
layout: post
title: Linux Fundamentals
tags: [Linux, Commands]
author : Christopher Githui
---
"Linux" is more of an umbrella term used for OS's that are based on the Linux Kernel. Linux happens to be free and open-source thus enabling distributions of Linux to come in all shapes and sizes best suited for the system they are being used for i.e as a web or application server, as a desktop or in a cell phone.  

Linux-based operating systems are excellent choices for software engineering as they are lightweight, extremely versitile and adaptable. However, they are not quite user friendly as often newcomers will be required to interact with the "terminal" and have a different structure than those found on Windows or MacOs. In this article we will cover basic linux commands that will enable newcomers be terminal friendly.

> To follow along install a Linux-based OS or If you are using a windows machine kindly look at [Development Environment Setup](https://whiptix.github.io/2023/12/19/dev-env-setup.html 'Development Environment Setup') before proceeding.

### Introduction
To be able to confortably develop a software or application using a linux based operating system a developer should be confortable to do any administrative task using a command on the terminal this includes file manipulation, package installation or user management.

Below are some commands and their description:

 Command | Description |
 --- | -------------|
 `echo` | Output any text that we provide |
 `whoami` | Find out what user we're currently logged in as! |
 `ls` | lists the contents of the current diectory |
 `cd` | changing our current directory, this command is used to open a given directory |
 `cat` | used to output contents of a file  > You can use cat to output the contents of a file within directories without having to navigate to it by using cat and the name of the directory. I.e. cat /home/ubuntu/Documents/todo.txt|
 `pwd` | used to find out the full path to the current working directory |
 `find` | as the name suggests this command is used to search for files for instance ```find -name filename.ext``` or ```find -name *.txt``` |
 `grep` | this command enables searching for specific values in file contents eg ```grep "IP Address" access.log```  |
 `wc` | counts the number of entries in a file i.e ```wc -l access.log``` |
`mkdir` | this command enables creation of one or more directories |
`touch` | This command enables creation of a file i.e. ```$ touch file.txt``` |
`mv` | mv stands for **move** and this command is used to move a file or a directory from one place to another |
`cp` | cp is short for "copy" |


on top of this commands there are different linux operators such as:

 Symbol / Operator | Description |
 -- | ---------------- |
 `&` | This operator allows you to run commands in the background of your terminal. |
 `&&` | This operator allows you to run multiple commands in your terminal. |
 `~` | This operator is used as a shorthand for home directory of the user you have logged in as |

