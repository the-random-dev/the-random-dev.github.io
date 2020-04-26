---
layout: article
title: Useful Linux Commands
tags: linux terminal
comments: true
key: linux-commands-2020-04-25
sharing: true
---

Linux Shell is one of most handful tools for developing and for backend services. Those are some of most linux commands for beginners. 

### ls
List directory contents.

It allows you to see which files and folders are there. 
It is a basic but very useful command on linux  terminal.

Use it with  ‘ -la’  if you want to see more details


	
### cd
Change the current directory.

You use this command to navigate between directories. 

It is another essential command on Terminal.
	
### mkdir
Change the current directory.

That is the command you need to create a new directory. 

Use it with ‘ -p’ or ‘ --parents’ to create directories and subdirectories.
	
### cat
Concatenate files and print on the standard output.

Examples:
```bash
~$ cat myfile.txt
```

It will print on the screen the content of your file.
```bash
~$ cat file1.txt file2.txt > file3.txt
```
It will concatenate file1.txt and file2.txt then save it on file3.txt
Concatenate files and print on the standard output.

Examples:
```bash
~$ cat myfile.txt
```

It will print on the screen the content of your file.

```bash
~$ cat file1.txt file2.txt > file3.txt
```
	
It will concatenate file1.txt and file2.txt then save it on file3.txt
### mv

Move or rename directories and folders.
	
Examples:
```bash
	~$ mv pic001.jpg dog.jpg 
```
	
pic001.jpg will be renamed to dog.jpg.
```	
~$ mv brainstorm.txt project
```
It will move brainstorm.txt to directory project
		
### cp

Copy files and directories.
	
Examples:

```bash
~$ cp file1.txt file2.txt 
```
It copies file1.txt to file2.txt.
```bash
~$ cp -rf folder1 backup
```	

‘ -rf’ copies recursively, that means, it will copy all files and subdirectories from folder1 to folder2.

### rm
Delete files and directories.

Examples:

```bash
~$ rm file1.txt
```
It deletes file1.txt

```bash
~$ rm -rf mySecretFolder
```

It will delete all files and subdirectories from myScretFolder then will delete the directory itself.
	
### vi/nano

Those are the most popular text editors on Terminal.
	
Nano has an intuitive and easier syntax for beginners than Vi.
	
Vi on other hand is a powerful and advanced command line editor.

```shell
	~$ vi file1.txt
```
```bash
~$ nano file1.txt
```	
### sudo
It allows to execute a command as another user. That means, you can run a specific command as root or another user on the current section.
	
Example:

```bash
$ mkdir secret
mkdir: cannot create directory ‘secret’: Permission denied

/$ sudo mkdir myFolder
[sudo] password for user:

```	
The current user needs to be allowed on /etc/sudoers to use it.

	

	
### man

Man is an interface to the on-line reference manuals. 
	
It is a manual of linux commands and its syntax. Sometimes you get the answer here faster than searching on Google =)
	
Examples:
```bash
	~$ man top
```
It will print the description of top command. Press ‘q’ to close it.
