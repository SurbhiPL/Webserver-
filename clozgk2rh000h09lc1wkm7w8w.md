---
title: "Linux For Dev"
datePublished: Wed Nov 15 2023 07:45:48 GMT+0000 (Coordinated Universal Time)
cuid: clozgk2rh000h09lc1wkm7w8w
slug: linux-for-dev
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1700034238658/dd9d615b-2db1-433c-9f02-af621a980b80.png
tags: linux, learning, linux-for-beginners, linux-for-devops

---

### Linux is an open-source operating system. It is like Windows, Mac, Android, etc.

It was initially released by **Linus Torvalds** on September 17, 1991. It is a free and open-source operating system

### [Listing commands](https://github.com/LondheShubham153/90DaysOfDevOps/blob/master/2023/day02/basic_linux_commands.md#listing-commands)

`ls option_flag arguments` --&gt; list the sub directories and files avaiable in the present directory

Examples:

* `ls -l`\--&gt; list the files and directories in long list format with extra information
    
* `ls -a` --&gt; list all including hidden files and directory
    
* `ls *.sh` --&gt; list all the files having .sh extension.
    
* `ls -i` --&gt; list the files and directories with index numbers inodes
    
* `ls -d */` --&gt; list only directories.(we can also specify a pattern)
    

### [Directoy commands](https://github.com/LondheShubham153/90DaysOfDevOps/blob/master/2023/day02/basic_linux_commands.md#directoy-commands)

* `pwd` --&gt; print work directory. Gives the present working directory.
    
* `cd path_to_directory` --&gt; change directory to the provided path
    
* `cd ~` or just `cd` --&gt; change directory to the home directory
    
* `cd -` --&gt; Go to the last working directory.
    
* `cd ..` --&gt; change directory to one step back.
    
* `cd ../..` --&gt; Change directory to 2 levels back.
    
* `mkdir directoryName` --&gt; to make a directory in a specific location
    

Examples:

```basic
mkdir newFolder              # make a new folder 'newFolder'

mkdir .NewFolder              # make a hidden directory (also . before a file to make it hidden)

mkdir A B C D                  #make multiple directories at the same time

mkdir /home/user/Mydirectory   # make a new folder in a specific location

mkdir -p  A/B/C/D              # make a nested directory
```