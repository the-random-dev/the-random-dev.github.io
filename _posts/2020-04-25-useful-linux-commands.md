---
layout: article
title: Basic Shell Commands - Part 1
tags: linux terminal basic shell
comments: true
key: linux-commands-2020-04-25
sharing: true
description: Shell is a Command Line Interface (CLI) is a very handful tool for developing and managing systems. Those commands work on Linux and macOS shell. Some of them also work on Microsoft PowerShell terminal. In the first part, let's see how to list directory contents, create directories, and how to edit a text file.
---



Shell is a Command Line Interface (CLI) is a very handful tool for developing and managing systems. Those commands work on Linux and macOS shell. Some of them also work on Microsoft PowerShell terminal. In the first part, let's see how to list directory contents, create directories, and how to edit a text file.

### Listing Directory Contents

When you open a terminal, it opens in a specific folder. Usually it opens in your home folder. To see which files and subdirectories are in a specific directory, we use the command ```ls```

To see files and folder of current directory:
```bash
~$ ls 
```
Result:
```bash
backup  file1.txt  pic.jpg
```


If you wan to see which files are in another directory, you pass it as parameter. Let's see which files are in root directory. The root directory is ```/```

```bash
~$ ls /
backups  cache  crash  lib  local  lock  log  mail  opt  run  snap  spool  tmp
```

For a detailed list, you can use ```ls -la```:

```bash
~$ ls -la
```
```bash
total 100
drwxr-xr-x  24 root root  4096 Apr  7 10:56 .
drwxr-xr-x  24 root root  4096 Apr  7 10:56 ..
drwxr-xr-x   2 root root  4096 Mar 30 16:05 bin
drwxr-xr-x   5 root root  4096 Apr  7 10:57 boot
drwxr-xr-x   2 root root  4096 Mar 30 15:50 cdrom
drwxr-xr-x  18 root root  3860 Apr 15 19:18 dev
drwxr-xr-x  95 root root  4096 Apr 25 15:08 etc
drwxr-xr-x   3 root root  4096 Mar 30 16:02 home
drwxr-xr-x  22 root root  4096 Apr 25 15:08 lib
drwxr-xr-x   2 root root  4096 Feb  3 18:22 lib64
```


	
### Changing the Current Directory

Okay, now we can see which files are in any directory, but how can we navigate to another directory? To do it, we can use the command ```cd```

For example, let's suppose we have a directory called *music*. To move there:
```bash
~$ cd music
```
Now we are inside folder music:
```bash
~/music$
```

If you want to go one directory up, just type ```cd ..``:
```bash
~/music$ cd ..
```
Now we are inside folder music:
```bash
~$
```
To return our home folder for any directory, just type ```cd```
	
### Creating directories

To create a directory, we use the command ```mkdir```.

Let's create a folder called "dogs" in our example:

```bash
~$ mkdir dogs
```
Our directory has been created. Let's use ```ls``` command to check it out: 
```bash
~$ ls
```
Result:
```bash
dogs
```

### Printing and Concatenating files

To print the content of a file in terminal, we use ```cat``` command. 

Let's suppose we have a file called ```lorem.txt``` and we want to print it. To do it:
```bash
~$ cat lorem.txt
```
Output
```
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed nec sem eget orci malesuada
ultricies. Phasellus iaculis lacinia odio id faucibus. Vivamus feugiat id diam eu consequat.  
```

Now let's suppose we want to print on our terminal files ```lorem.txt``` and ```ipsum.txt``` concatenated:
```bash
~$ cat lorem.txt ipsum.txt
```
Output
```
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed nec sem eget orci malesuada
ultricies. Phasellus iaculis lacinia odio id faucibus. Vivamus feugiat id diam eu consequat.
Mauris non quam est. Donec ac arcu vitae ligula blandit interdum eu nec leo. Donec imperdiet
faucibus nisl, nec iaculis nulla rutrum fringilla. Aenean in vulputate eros, at vulputate
nisi.
```

Finally, if you want to save it in a file called ```loremIpsum.txt```, we can use the output operator ```>``` to save the concatenation of both:

```bash
~$ cat lorem.txt ipsum.txt > loremIpsum.txt
```
It will generate a file called ```loremIpsum.txt```, that contains the content ```lorem.txt``` and ```ipsum.txt```.

	
### Editing a text

Most popular editors on Linux are ```emacs```, ```nano``` and ```vi```. If you have no experience with terminal, I highly recommend using ```nano```. ```emacs``` and ```vi``` are powerful text editors, but ```nano``` is a pretty easier for beginners.

To create or edit our text, just type ```nano``` and the filename. Let's edit our file lorem.txt

```shell
	~$ nano lorem.txt
```
```bash
  GNU nano 2.9.3                         lorem.txt                                    
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed nec sem eget orci
malesuada ultricies. Phasellus iaculis lacinia odio id faucibus. Vivamus feugiat 
id diam eu consequat.  



                                                                                      
^G Get Help   ^O Write Out  ^W Where Is   ^K Cut Text   ^J Justify    ^C Cur Pos
^X Exit       ^R Read File  ^\ Replace    ^U Uncut Text ^T To Spell   ^_ Go To Line
```

to save it, press ```CTRL + X``` then ```Y``` to confirm.

### Conclusion

This was the first part of basic Linux shell commands. In next post, we will continue with  operations on files and folders. See you there!