---
layout: post
title: Linux Fundamentals
tags: [Linux, Commands]
author : Christopher Githui
---
"Linux" is more of an umbrella term for multiple OS's that are based on UNIX which happens to be open source thus enabling variants of Linux to come in all shapes and sizes best suited for the system they are being used for i.e as a web or application server or as a desktop.  

> If you are using a windows machine kindly look at [Development Environment Setup](https://whiptix.github.io/2023/12/19/dev-env-setup.html 'Development Environment Setup') before proceeding.

Linux based operating systems are good for software engineering as they are lightweight, However they are not quite user friendly as often users will be required to interact with these systems using the terminal. In this article we will cover basic linux commands that will enable us do basic functions like interact with the filesystem, searching for files, understanding shell operators, permissions etc.

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


on top of this commands there are different linux operators such as:

 Symbol / Operator | Description |
 -- | ---------------- |
 `&` | This operator allows you to run commands in the background of your terminal. |
 `&&` | This operator allows you to run commands in the background of your terminal. |

