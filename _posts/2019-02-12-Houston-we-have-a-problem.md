---
layout: post
title: Okay, Houston, we've had a problem here
date: 2019-02-12 18:20:45
categories: [Mingw-w64]
---

The other day I tried to compile SQLite source code with Mingw-w64 compiler (MSYS2 distro). I headed on over to SQLite.org for the instruction. I run Mingw-w64 compiler environment and typed command: **gcc shell.c sqlite3.c -lpthread -ldl**
![libdl missing]({{site.baseurl}}/assets/libdlmissing.png)  
What the hell?  I was thinking "Now, just breathe deeply and think, please." The message was "..... ld.exe cannot find -ldl"  

- Question 1 - what is ld.exe?  Answer [LoaD](https://en.wikipedia.org/wiki/GNU_linker)
- Question 2 - what is -ldl?    Answer -l is a linker option. It's shortcut means link libdl library

OK. But how can I find and install this library? Msys2 uses [pacman](https://www.archlinux.org/pacman/pacman.8.html) as a package manager. It means I should read the documentation. Reading.......  
A few examples of pacman commands:  
Synchronizes the repository databases and updates all the system's packages  
pacman -Syu  
Install package  
pacman -S \<package> example: install make.exe pacman -S make  
Remove package  
pacman -R \<package> example: uninstall make pacman -R make  
Now high time to install libdl.a  
First update the files database  
pacman -Fy  
Search the files database for libdl.a  
pacman -Fs libdl.a  
Install package  
pacman -S mingw-w64-x86_64-dlfcn  
![pacman]({{site.baseurl}}/assets/sqlitecompilation.png)  
Remember, always stay calm and keep your wits about yourself.