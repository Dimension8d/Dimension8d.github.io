---
layout: post
title:  "Customize your terminal in 3 Steps"
author: grim
categories: [ Linux , tips & tricks ]
comments: True
image: assets/images/Figlet/1.png
---

Everytime I run up with coding/pen-testing kind of videos in youtube, I see cool patterns or texts at the top of terminal. I had wondered how this is done? I did some browsing stuffs and playarounds with my local machine...and here we are!!!

This post is both a collection and detailed explanation of "How to customize your terminal - without any external packages in Linux".

## Figlet:

Step 1 to our customization is done with Figlet command. This command takes a string(text) and converts them into patterns/various text formats. In linux systems, this library comes pre-installed. In case, if your machine doesn't has this one, you can easily add this with below command

```shell
sudo apt-get install figlet (in debian)
pacman -S install figlet (in arch)
```
![Figlet]({{ site.baseurl }}/assets/images/Figlet/pic7.png)

Syntax of the command is as below,

```shell
figlet "Code Genesis|Zero Whats"
```
![Figlet]({{ site.baseurl }}/assets/images/Figlet/pic1.png)

We can pass tag information(optional) `-f` along with the base command. This gives variety of options to customize our terminal.

![Figlet]({{ site.baseurl }}/assets/images/Figlet/pic2.png)

To check the supported/available options in your system, use `showfigfonts` command.

![Figlet]({{ site.baseurl }}/assets/images/Figlet/pic3.png)

## Editing Bashrc

This does gives a fancy format of texts. But is reverted/reset after every instance. In order to see the changes every time we fire up the terminal, we need to edit the `./bashrc` file accordingly.

The bashrc file is a script that is instantiated every time the terminal is fired up.
The bashrc.original is another script which is executed during user login (will be holding some preset informations of user). Note that the execution purpose of these files will be different in **Mac environment**.

![Figlet]({{ site.baseurl }}/assets/images/Figlet/pic4.jpg)

Add the command at the end of the file, like in above image.

**Note**: If your machine calls some other shells by default, for instance my latest debian calls Zsh shell by default. Then editing the bashrc file will be ineffective. Such shells has its own script files(for Zsh->zbashrc) which are similar to bashrc and we need to edit those files.

Remember that these files are preceeded by a `.(dot)`. That means these are hidden files and are not listed with a usual `ls` command. We need to pass parameter `-a` along with ls to view these files.
Editing can be done with any text editors.

**command** : `ls -a`

Once editing is done, hit save and exit. Fire up the terminal again and Voila!!!
We have customized our terminal with default command that is available in our linux machine.

![Figlet]({{ site.baseurl }}/assets/images/Figlet/pic5.png)

Try tweeking the color options(I'd prefer Green for text and Black in background) as per your wish in the "Preference" option in terminal's GUI to enhance these effects.

If you need more customizations, there are additional packages that can be installed. One such popular package is `lolcat`. This intakes the user string and formats the text with multiple colors,or in simple terms it would apply a Rainbow effect to the text given.

**Additional Info:**
The Figlet package sits in path `/usr/share/figlet`. Change to this directory by giving command

```shell
 cd /usr/share/figlet
```

![Figlet]({{ site.baseurl }}/assets/images/Figlet/pic6.png)

In this directory, you can find some bunch of files. The `.flc` files are configuration(like header in C) files with which the figlet command converts the provided text.
The `.flf` and `.tlf` are the text format files. Few formats that were not listed with `showfigfonts` can be seen sitting here!!!

Moreover, you can do more customization with commands like `echo` combined with the figlet command. Few examples were covered in the video segment of this post where you can find a live session of customising our terminal.

![Figlet]({{ site.baseurl }}/assets/images/Figlet/pic8.png)

Hope you guys find this information useful for a basic customization tasks.
See yall with another post. Peace!


<iframe width="560" height="315" src="https://www.youtube.com/embed/Ogb2lnl_95A" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>