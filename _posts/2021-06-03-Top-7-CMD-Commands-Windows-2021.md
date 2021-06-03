---
layout: post
title:  "Top 7 CMD commands Windows 2021"
author: prince
categories: [ windows, tips&tricks ]
comments: True
image: assets/images/terminal-windows.jpg
---

Are you looking  for CMD commands  ? Here are some which could be helpful to you.
In this article, I will share the top commands that I have come across 2021 in my regular usage.

> Command Prompt, also known as cmd.exe, is a command-line interpreter for Windows CE, NT, OS/2, and eComStation OS. It is similar to COMMAND.COM on Windows 9x and DOS systems. Therese Stowell initially developed it for Windows NT.

Here’s a Best CMD Commands List. The command prompt is still viral on the Internet. Some of the most common command prompt commands can be reviewed below.

1. Assoc
2. Tasklist
3. ping
4. ipconfig
5. netstat
6. Del (Recursive deletion)
7. Trace route

### Assoc

The programs that are installed on our computer have their file extensions. We don't know and cannot remember all of them, because so many programs have been installed and each of their extensions will be different. We can use this command in such scenario,

![CMD]({{ site.baseurl }}/assets/images/Assoc.png)

### Tasklist:

Although the Task Manager is available on the Windows Explorer, some tasks are still hidden from it. Here, this command for the task list comes into play

![CMD]({{ site.baseurl }}/assets/images/tasklist-cmd.png)

This will show all the running tasks, including the hidden one.
	
If you  like more details about them, type `Tasklist-v` And by entering `Tasklist-svc` you get to see the resources relevant to each task.

### ping:

It is a useful command to test the speed at which data is transferred to a destination device through a network

![CMD]({{ site.baseurl }}/assets/images/ping-cmd.png)

Some extra options with the ping command,

`ping-t` and it pins the target until Ctrl-C stops it.
`ping-a` will solve the IP address and hostname of the destination.

If you want to count the count hops Record route, type `ping-r` and the `ping-s` counts the count hops time stamp

### ipconfig

It shows the IP address, default gateway, subnet mask, etc., that are most important for troubleshooting TCP / IP problems.

The below options will do more with the command,

Type `ipconfig` to view the use of IP address and subnet mask.
The `ipconfig / displaydns` command shows us the use of the DNS cache.
If you want to delete the local DNS cache used, type `ipconfig/flushdns`
Type `ipconfig / release` and set the IP address for the specific adapter.

### mkdir

Obviously `mkdir <foldername>` will create a new folder. Make new directory.

### netstat

If you want to  know who is connecting to your computer, this netstat command will come into action. You get information about all listening ports and active connections using the `netstat-a` order. 
The `netstat-e` command shows all ethernet stats. Sort the connections in numerical order by the command `netstat-n` The `netstat-r` command displays the contents of the routing list

### Del

When you need to delete all the files or folders inside a folder (i.e recursively delete all the files), then this option could be helpful.

    del <foldername> /q /s

![CMD]({{ site.baseurl }}/assets/images/del-recursive-cmd.png)

* /q disables Yes/No prompting
* /s means delete the file(s) from all subdirectories.

### Trace route

Traceroute is a network diagnostic tool that tracks the path of a packet of data as it travels from your computer to a destination over the internet. Running a traceroute lets you see where your connection is slow or unresponsive.

to test your internet connection, it is a good idea to run a traceroute to 8.8.8.8 (Google’s DNS server).

![CMD]({{ site.baseurl }}/assets/images/traceroute-cmd.png)

<iframe width="560" height="315" src="https://www.youtube.com/embed/8T37kStRowE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



Hope the above commands would be helpful !!

Share the top CMD commands you like in the comment box below. Let's Learn and explore together...
