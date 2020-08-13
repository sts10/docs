## Switching from Ubuntu to Lubuntu

To avoid the high memory usage of Ubuntu's Unity desktop environment, I installed Ubuntu's LXDE desktop environment (called Lubuntu). I had a gist that Unity was a bit of a memory hog compared to other desktop environments. I also spotted [this Reddit post](https://www.reddit.com/r/linux/comments/5l39tz/linux_distros_ram_consumption_comparison_updated/?st=ixpgu5wy&sh=67b8f57f) that compares some lightweight distros in terms of RAM consumption and Lubuntu did well.

To install Lubuntu, I ran `sudo apt-get install lubuntu-desktop` (I learned this from a helpful user in the [Ubuntu Riot.im channel](https://riot.im/app/#/room/ubuntu:matrix.org)). The size of the installation was about 340 mb. 

After installing the Lubuntu desktop environment, you want to run the software updater (you can also update software in the Terminal by running `sudo apt update && sudo apt upgrade`). Then restart the computer (that seems to have been pretty important), and at the login screen choose Lubuntu (or LXDE... that's another option and I'm not sure what the difference is). 

You can check how much RAM you have available by running `free -m` in the terminal. Thanks to [this site](http://www.linuxatemyram.com/), I knew to look for the value under "available" to get an accurate estimate of how many megabytes of my memory were "free". With my terminal and Firefox running on Lubuntu, I have about 1187 MB RAM of my 2 GB available, as opposed to Ubuntu, which generally only left about 700 or 800 MB available when I was running a couple of programs (not a very scientific test, I know).

Plus I can always switch back to regular Ubuntu via the login screen.

Lubuntu is pretty snappy! I did want to make a few simple changes right off the bat. Here's how I went about some of them. 

### How to disable tap to click persistently in Lubuntu

I wanted to disable my touchpad from clicking, which I did by doing this:

1. Open `~/.config/lxsession/lubuntu/autostart` or possibly `~/.config/lxsession/LXDE/autostart` (not sure which)
2. To disable tap touchpad to click, add `synclient MaxTapTime=0`

You can find other settings to set [here](https://help.ubuntu.com/community/Lubuntu/Mouse), like enabling two-finger horizontal scroll (`synclient HorizTwoFingerScroll=1`).

### Installing an application launcher for Lubuntu

On macOS I make frequent use of [Alfred](https://www.alfredapp.com/) as an application launcher. Ubuntu's Unity desktop environment sort of had something like that, which you can initiate by pressing the command key on its own at any time. But I couldn't find something similar in LXDE-- the application menu (similar to the Start menu in Windows) was just not fast enough for me coming from macOS + Alfred). 

So I found [this askubuntu answer](https://askubuntu.com/questions/203851/any-search-tool-for-lxde-menu/203852#203852) that recommends installing an application called Synapse by running `sudo apt-get install synapse`. By default the launcher is invoked by hitting `ctrl + space`, but I changed it to `alt+Enter` by launching Synapse and clicking on the not-super-obvious round button on the right side of the pop-up display and clicking "Preferences". Works great! 

### My attempt to make the Gnome terminal the default

The default Terminal in Lubuntu (think it's called LXTerminal) didn't support true color in Vim, so I looked for other options. I had gotten used to the terminal in regular Ubuntu (which I'm pretty sure is the Gnome Terminal), so I figured I could switch that in on Lubuntu. Oddly it's not in the main menu of applications though. 

First, I figured out a way to set it as the "default" terminal:

1. menu > Preferences > Default applications LXSession
2. Launching applications > Terminal manager > More > write in "gnome-terminal" for "Manual setting"

This seems to have worked? Notably, Gnome Terminal launches when I enter the standard launch-terminal shortcut of `option + control + t`.

While here, I also changed default application for spreadsheets to LibreOffice Calc

To get an icon from Gnome Terminal to appear in the desktop menu, I loosely followed [this forum answer](https://ubuntuforums.org/showthread.php?t=2121412) and created a new file in the directory `~/.local/share/applicatons` called `gnome-terminal.desktop` and entered the following text into that new file:

```
[Desktop Entry]
Name=GNOME Terminal
TryExec=gnome-terminal
Exec=gnome-terminal
Icon=gnome-terminal
Type=Application
Categories=System;TerminalEmulator;
Keywords=console;command line;execute;
```

Upon saving that file, I got a new icon in menu > System Tools called "GNOME Terminal" that launches my now-beloved Gnome Terminal. Woohoo! (If `Icon=gnome-terminal` hadn't worked I would have used `Icon=lxterminal`)

_See separate entry for more on using Vim in Lubuntu._

### More Lubuntu configuration ideas

Just found [this long forum post](https://ubuntuforums.org/showthread.php?t=1905408) with more ideas of recommended features for Lubuntu.  There's also the [Community Help Page](https://help.ubuntu.com/community/Lubuntu) here.


### Some lingering problems on Lubuntu
  - can't figure out how to set custom openbox keybindings
  - Want to disable scrolling in Gnome terminal

