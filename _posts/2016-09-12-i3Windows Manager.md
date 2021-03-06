---
layout: post
title: Customizing i3 Windows Manager
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
Today in this article , I will be telling you the step by step procedure for setting up i3 windows manager. For, those who don't know what it is, let me tell you about i3 in brief.

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

For a complete list of i3 commands you can visit [refcard page](https://i3wm.org/docs/refcard.html)

### Customizing i3

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
**Screen Locking**

~~For screen locking, i3lock can be used.
to set a keybinding,~~


>~~bindsym Mod1+l i3lock -c 000000 -n~~

~~you can use any rgb colour you want. Just replace `000000` with the color's hex code. or you can set an image for the lock screen.
For that just replace `i3lock -c 000000 -n` with  `i3lock -i your-image-path -p default -n`~~

Edit: I got a better method for the screen-locking.
I use `gnome-screensaver` to lock my screen with `gnome-screensaver-command -l` command.
For autolocking , I use `xautolock`
```bash
exec xautolock -time 1 -locker screenlock
```
The above line in the config file execute the screenlock command after every 1 minute of inactivity. Also to bind the Mod+Ctrl+l keys to lock the screen, I added below script to my config file.
```bash
bindsym Control+Mod1+l exec gnome-screensaver-command -l
``` 

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
Do not forget to copy the i3status.conf to `~/.i3/i3status.conf`

```bash
cp /etc/i3status.conf ~/.i3/i3status.conf
```
**To Enable multimedia keyboard keys**


```bash
# Pulse Audio controls
bindsym XF86AudioRaiseVolume exec --no-startup-id pactl set-sink-volume 1 +5% #increase sound volume
bindsym XF86AudioLowerVolume exec --no-startup-id pactl set-sink-volume 1 -5% #decrease sound volume
bindsym XF86AudioMute exec --no-startup-id pactl set-sink-mute 1 toggle # mute sound

# Sreen brightness controls
bindsym XF86MonBrightnessUp exec xbacklight -inc 20 # increase screen brightness
bindsym XF86MonBrightnessDown exec xbacklight -dec 20 # decrease screen brightness
```

where `1` in Pulse audio controls is the sink number found with

```bash
$ pactl list sinks
```

**Battery Low Warning**

By default, if the battery level fall below a threshold, the color of battery status text in the i3 bar turns red which I usually don't notice.For this, I have used a script I found on archlinux forum’s i3 thread. This script needs `acpi` installed and root permissions to run, so add a no-password entry for it in the sudoers file. You will also need `pm-utils` for power management. Then add it in the config file.You need to use `exec_always sudo /path/to/script.sh`, to run at restart also. 

```bash
#! /bin/bash

SLEEP_TIME=5   # Default time between checks.
SAFE_PERCENT=30  # Still safe at this level.
DANGER_PERCENT=15  # Warn when battery at this level.
CRITICAL_PERCENT=5  # Hibernate when battery at this level.

NAGBAR_PID=0
export DISPLAY=:0.0

function launchNagBar
{
    i3-nagbar -m 'Battery low!' -b 'Hibernate!' 'pm-hibernate' >/dev/null 2>&1 &
    NAGBAR_PID=$!
}

function killNagBar
{
    if [[ $NAGBAR_PID -ne 0 ]]; then
        ps -p $NAGBAR_PID | grep "i3-nagbar"
        if [[ $? -eq 0 ]]; then
            kill $NAGBAR_PID
        fi
        NAGBAR_PID=0
    fi
}


while [ true ]; do

    killNagBar

    if [[ -n $(acpi -b | grep -i discharging) ]]; then
        pm-powersave true
        rem_bat=$(acpi -b | grep -Eo "[0-9]+%" | grep -Eo "[0-9]+")

        if [[ $rem_bat -gt $SAFE_PERCENT ]]; then
            SLEEP_TIME=10
        else
            SLEEP_TIME=5
            if [[ $rem_bat -le $DANGER_PERCENT ]]; then
                SLEEP_TIME=2
                launchNagBar
            fi
            if [[ $rem_bat -le $CRITICAL_PERCENT ]]; then
                SLEEP_TIME=1
                pm-hibernate
            fi
        fi
    else
        pm-powersave false
        SLEEP_TIME=10
    fi

    sleep ${SLEEP_TIME}m

done
```

#### Beautification

**Changing the fonts**

```bash
font pango:Open Sans 8
```
[gnome-look](https://www.gnome-look.org/) is a great resource for gtk themes. 
I chosed arc-theme but you can find one that strikes your fancy and extract it's archive to either $HOME/.themes (local install) or /usr/share/themes (global install). Then open up `lxappearance` and apply the new theme.

Some themes require newer versions of gtk installed. To find version of gtk we're using, run in a terminal 

```bash
dpkg -l libgtk* | grep -e '^i' | grep -e 'libgtk-*[0-9]'.
```

To add the ArcGTK repo run

`sudo sh -c "echo 'deb http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_16.04/ /' >> /etc/apt/sources.list.d/arc-theme.list"`

Then, refresh your software sources and install the theme:
`sudo apt-get update && sudo apt-get install arc-theme`

`sudo apt-key add - < Release.key`

A precompiled .deb installer for Ubuntu 16.04 LTS is also available to download from the theme website:
<a href="http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_16.04/all" onclick="_gaq.push(['_trackEvent', 'outbound-article', 'http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_16.04/all', 'Arc GTK Theme Installer for Ubuntu 16.04 LTS']);" class="omg-button download-link" target="_blank" title="Download Arc GTK Theme for Ubuntu 16.04 LTS">Arc GTK Theme Installer for Ubuntu 16.04 LTS</a>

Or you can head on to their [github repo](https://github.com/horst3180/arc-theme)

__Extra applications you can try out__

1. compton

    A pretty sweet composite manager. I like some shadows and fading effects on my windows and menus. Install it with sudo apt install compton.

2. parcellite

    A simple, lightweight clipboard manager. Install it with sudo apt install parcellite.

3. pnmixer

    Volume control tray icon. Install it with sudo apt install pnmixer.

**Screenshots**
<img src= "/assets/img/i3wm/2016-12-10-145049_1920x1080_scrot.png">



