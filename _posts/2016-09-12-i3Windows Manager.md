---
layout: post
title: Customising i3 Windows Manager
comments: true
permalink: /:title
image: ''
date:   2016-12-09 00:06:31
tags:
- linux
description: ''
categories:
- Introduction
serie: learn


---
Today in this article , I will be telling you the step by step procedure for setting up i3 windows manager. For, those who don't know what it is, let me tell you about i3 in a brief.

i3 is primarily targeted at advanced users and developers. i3 is not a desktop environment in the sense of things like KDE and Gnome, or even the lightweight Xfce and LXDE. Unlike traditional desktop environments, window managers are flat, terminal-like environments that work in terms of workspaces and tiles. Window managers are independent from a GUI. As it is extremely lightweight,it doesn't require high-end hardwares, also it is highly customizable.

### Installing i3
To begin with, open terminal and run the following command.

```bash
sudo apt-get install i3 i3status i3lock feh
```
* i3 is the main window manager package.
* i3status is an utility to generate a string with information to be displayed in the i3bar.
* i3lock is an utilitu to lock the screen.
* feh is an X11 image viewer aimed mostly at console users.We will use this utility to set the wallpaper.

Now you can logout and login with i3.

### Customising i3

* During the first startup, i3 will ask you to set your default `$Mod` key and copy the configutation file to ~/.config/i3 . You can set it anything you want but I would suggest you to keep it default.

Now lets start with the configutation.

i3 by default keeps the configuration file in `~/.config/i3/config`.
Some of the applications needs to be run at startup, feh and nm-applets 
which set the wallpaper and shows network manager at i3bar respectively.

```bash
#Startup programs
exec --no-startup-id nm-applet
exec --no-startup-id feh --bg-fill ~/Pictures/wallpaper.png
```

Next, to set a keybinding for taking screenshots, you need to install `scrot`, a command-line tool for taking screenshot.

```bash
sudo apt-get install scrot
```
Setting the keybindings

```bash
#Take a screenshot upon pressing $mod+ ptrscs

bindsym Print exec scrot $HOME/Pictures/ScreenShoots/`date +%Y-%m-%d_%H:%M:%S`.png
```
For screen locking, i3lock can be used.
to set a keybinding,

```bash
#screen lock
bindsym Mod1+l i3lock -c 000000 -n
```
you can use any rgb colour you want. Just replace `000000` with the color's hex code. or you can set an image for the lock screen.
For that just replace `i3lock -c 000000 -n` with  `i3lock -i your-image-path -p default -n`

#### Setting named namespace
```bash
# Name the workspaces
set $tag1 "1: www"

# switch to workspace
bindsym $mod+1 workspace $tag1

# move focused container to workspace
bindsym $mod+Shift+1 move container to workspace $tag1
```
You can do like this for how many namespace you want.

let us change some settings for i3bar in config. Colors can be set here along with some position settings. Check for bar in config file as there are some defaults present. Help on these settings is available [here](http://i3wm.org/docs/userguide.html#_configuring_i3bar).

```bash
# Start i3bar to display a workspace bar (plus the system information)
bar {
	colors {
		# Whole color settings
		background #000000
		statusline #ffffff
		separator  #666666

		# Type             border  background font
		focused_workspace  #008fff #007fff #ffffff
		active_workspace   #333333 #5f676a #ffffff
		inactive_workspace #333333 #222222 #888888
		urgent_workspace   #aa0000 #990000 #ffffff
	}
	# i3bar position
	position top
	# Using custom i3status.conf
	status_command i3status -c ~/.i3/i3status.conf
}
```
Do not forget to copy the i3status.conf to ~/.i3/i3status.conf
```bash
cp /etc/i3status.conf ~/.i3/i3status.conf
```

**Changing the fonts**
```bash
font pango:Open Sans 8
```
Next, Setting up a theme for gtk3, gtk2 and gnome-shell. I chosed arc-theme, you can choose whatever you liked..
To add the ArcGTK repo run

`sudo sh -c "echo 'deb http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_16.04/ /' >> /etc/apt/sources.list.d/arc-theme.list"`

Then, refresh your software sources and install the theme:
`sudo apt-get update && sudo apt-get install arc-theme`

`sudo apt-key add - < Release.key`

A precompiled .deb installer for Ubuntu 16.04 LTS is also available to download from the theme website:
<a href="http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_16.04/all" onclick="_gaq.push(['_trackEvent', 'outbound-article', 'http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_16.04/all', 'Arc GTK Theme Installer for Ubuntu 16.04 LTS']);" class="omg-button download-link" target="_blank" title="Download Arc GTK Theme for Ubuntu 16.04 LTS">Arc GTK Theme Installer for Ubuntu 16.04 LTS</a>

Or you can head on to their [github repo](https://github.com/horst3180/arc-theme)


