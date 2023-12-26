---
layout: post
title: Linux Fundamentals
tags: [Linux, Commands]
author : Christopher Githui
---
"Linux" is more of an umbrella term used for OS's that are based on the Linux Kernel. Linux happens to be free and open-source thus enabling distributions of Linux to come in all shapes and sizes best suited for the system they are being used for i.e as a web or application server, as a desktop or in a cell phone.  

Linux-based operating systems are excellent choices for software engineering as they are lightweight, extremely versitile and adaptable. However, they are not quite user friendly as often newcomers will be required to interact with the "terminal" and have a different file structure than those found on Windows or MacOs. In this article we will cover basic linux commands that will enable newcomers be terminal friendly.

> To follow along install a Linux-based OS on your PC or If you are using a windows machine kindly look at [Development Environment Setup](https://whiptix.github.io/2023/12/19/dev-env-setup.html 'Development Environment Setup') before proceeding.

### Introduction
To be able to confortably develop a software or application using a linux based operating system a developer should be confortable to do any administrative task using a command on the terminal this includes file manipulation, package installation or user management.

Below are some commands and their description to help familiarize with linux:

|Command | Description |
| :----: | :---------- |
| `echo` | Output any text that we provide |
| `su` | this command allows you to run a program as a different user e.g ```su user1```|
| `whoami` | Find out what user we're currently logged in as! |
| `ls` | lists the contents of the current diectory |
| `cd` | changing our current directory, this command is used to open a given directory |
| `cat` | used to output contents of a file **NOTE:** You can use cat to output the contents of a file within directories without having to navigate to it by using cat and the name of the directory. I.e.<br> <span style="background-color:#ddd;"> ```cat /home/ubuntu/Documents/todo.txt``` </span>|
| `pwd` | used to find out the full path to the current working directory |
| `find` | as the name suggests this command is used to search for files for instance <br> <span style="background-color:#ddd;">```find -name filename.ext```</Span> or <br> <span style="background-color:#ddd;"> ```find -name *.txt``` </span> |
| `grep` | this command enables searching for specific values in file contents eg <br> <span style="background-color:#ddd;"> ```grep "IP Address" access.log``` </span> |
| `sed` | this command allows you to find, replace and delete patterns in a file without using a text editor, it follows this syntax <br> <span style="background-color:#ddd;"> ```sed [option] 'script' input_file``` </span> <br> the script contains the searched regular expression pattern, the replacement string and subcommands*(**s** subcommand to replace matchind patterns or **d** to delete them)*. Here is an example that replaces *red* with *blue* in the colors.txt file <br> <span style="background-color:#ddd;"> ```sed 's/red/blue' colors.txt``` </span> |
| `wc` | counts the number of entries in a file i.e <br> <span style="background-color:#ddd;"> ```wc -l access.log``` </span> |
| `mkdir` | this command enables creation of one or more directories |
| `touch` | This command enables creation of a file i.e.<br> <span style="background-color:#ddd;"> ```$ touch file.txt``` </span> |
| `mv` | mv stands for **move** and this command is used to move a file or a directory from one place to another i.e. <br> <span style="background-color:#ddd;"> ```$ mv file.txt newfile.txt``` </span>|
| `cp` | cp is short for **copy** and its used to copy a file from one location to the other i.e. <br> <span style="background-color:#ddd;"> ```$ cp file.txt newfile.txt``` </span> |
| `vim` | vim is a command from a file editor called vim that you can use to edit files i.e. <br> <span style="background-color:#ddd;"> ```$ vim file.txt``` </span> or <br> <span style="background-color:#ddd;"> ```$ vi file.txt``` </span> <br> to save the file after editting to learn more about vim checkout  [VIM Docs](https://vimhelp.org/ 'VIM Docs') |
| `nano` | nano is also a file editor that is suitable for beginners as it is user friendly to use it type into the terminal <br> <span style="background-color:#ddd;"> ```$ nano file.txt``` </span> <br> and start editing the file on the resultant screen. To save your file press **CTRL + X**, **Y** , and then enter |
| `less` | similar to ```cat```, less outputs the contents of a file and it is suitable for viewing long files as it allows you to paginate the output. To use less type <br> <span style="background-color:#ddd;">```$ less file.txt``` </span> <br>, use spacebar to advance a page, or the arrow keys to go up and down one line at a time. Press **q** to quit out of less |
| `rm` | this command stands for **remove** and is used to delete files i.e to delete file.txt type into terminal <br> <span style="background-color:#ddd;"> ```$ rm file.txt``` </span>. <br> **NOTE:** Without other options, this command cannot be used to delete directories. However with the **-d** flag it is able to delete empty directories and the **-r** flag enables it to remove non-empty directories including any subdirectory.i.e <br> <span style="background-color:#ddd;">```$ rm -d directory```</span> or <br> <span style="background-color:#ddd;">```rm -r directory``` </span>|
| `rmdir`| this command is used to delete empty directories i.e. <br> <span style="background-color:#ddd;"> ```$ rmdir directory``` </span> |
| `man` | this command offers detailed documentation for nearly every command. to use it pass the commands name as an argument i.e <br> <span style="background-color:#ddd;"> ```$ man rm``` </span> |
| `file` | this commands checks a file type <br> <span style="background-color:#ddd;"> ```$ file filename.txt``` </span> <br> add **-k** flag to display more detailed information and **-i** to show the file's MIME type  |
| `zip` `unzip` | the zip file lets you compress items into a **.zip** file with the optimal compression ratio. Example <br> <span style="background-color:#ddd;"> ```zip archive.zip note.txt filename.txt``` </span> <br>The **unzip** command extracts the compressed file. Example <br> <span style="background-color:#ddd;"> ```unzip archive.zip```</span> |
| `tar` | this command archives multiple items into a **TAR** File (*format similar to ZIP*). The command follows this syntax <br> <span style="background-color:#ddd;"> ```tar [options] [archive_file] [target file or directory]``` </span> <br> i.e <br> <span style="background-color:#ddd;">```tar -cvzf newarchive.tar /home/user/Documents``` </span> |
| `head` | this command prints the first 10 lines of a text file or pipped data, it follows the following syntax <br> <span style="background-color:#ddd;"> ```head [option] [file]``` </span> <br> e.g <br> <span style="background-color:#ddd;"> ```head note.txt``` </span> <br> This command accepts the following options **-n** denotes the nummber of lines to be printed |
| `tail` | the tail command outputs the last ten lines os a file follows the same syntax as **head** e.g. <br> <span style="background-color:#ddd;"> ```tail -n audit.log``` </span> <br> |
| `diff` |this command compares two files' content and outputs the differences e.g. <br> <span style="background-color:#ddd;"> ``` diff file1 file2```|
| `tee` | this command writes terminal output to a file, for instance you would like to capture the output of a command eg get the result of a ping with the following command <br> <span style="background-color:#ddd;"> ```ping google.com \| tee ping_result.txt ``` </span> |
| `chmod` |  this command allows you to modify directory or file permissions in linux, it follows the following syntax <br> <span style="background-color:#ddd;"> ```chmod [option] [permission] [file_name]``` </span> <br> <span style="background-color:#ddd;"> ```chmod -rwxrwxrwx note.txt``` </span> |
| `chown` | this command lets you change a file, directory or symbolic links ownership to the specified username, it follows this syntax <br> <span style="background-color:#ddd;"> ```chown [option] owner[:group] file(s)``` </span> <br> For Example <br> <span style="background-color:#ddd;"> ```chown user1 note.txt``` </span> |


on top of this commands there are different linux operators such as:

 Symbol / Operator | Description |
 -- | ---------------- |
 `&` | This operator allows you to run commands in the background of your terminal. |
 `&&` | This operator allows you to run multiple commands in your terminal. |
 `~` | This operator is used as a shorthand for home directory of the user you have logged in as |



### Conclusion
Well, to become an expert in linux it takes time, dedication and a curious mindset; we encourage you to go through our ***Linux How To Articles*** to get an insight on how to :- 
1. Fix Permission Issues on Linux.
2. View and configure Linux Logs.
3. Monitor Server Resources.
4. Manage Processes in Linux.

When you have a question on how to accomplish a certain task feel free to comb through several avenues for instance search engines like Google and DuckDuckGo, question and answer sites like Stack Exchange.
