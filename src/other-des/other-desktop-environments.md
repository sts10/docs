# Trying Other Desktop Environments with Ubuntu (Besides Unity)

## XFCE

### To install 

1. `sudo apt-get install xfce4 xfce4-goodies`
2. Restart
3. Login as "xfce session"

### What You Get Straight out of the Box

- "Whisker menu" is the Start-menu-like menu in the top left. Same as Lubuntu 
- A nice, MacOS-like dock on the bottom with GNOME Terminal, File Manager, Web Browser (default), and a search

### Settings

There's a nice Settings menu in Whisker menu > Settings > Settings Manager

- In Window Manager > Keyboard, I set up a bucnh of window resizing keyboard shorts!
- In Session and Startup > Application Autostart, I entered a custom command to remap caps lock to control. 
    Name: remap caps
    Description: remap caps lock to control
    Command: `/usr/bin/setxkbmap -option "ctrl:nocaps"`
- In Mouse and Touchpad > Devices > Touchpad, I enabled "Disable touchpag while typing" and I disabled "Tap touchpad to click"


### Memory Usage

With Firefox, Terminal, and Settings open, I've got about 980 MB out of 2GB RAM "available". (This is compared to abut 1180 MB available when using Lubuntu-- it makes sense that Xubuntu slightly heavier than Lubuntu.)

### Pros

- Nice desktop
  - has a dock by default (edit settings by right-clicking between icons)
  - Window Switcher is nice. 
  - Toolbar on top is nice out of the box. 
- Available on many distros! Only have to learn the tweaks and settings once!

### Cons
- Cursor is solid white (not smart) in Neovim 0.2, and then when I quit Neovim it's solid white (not smart) in the terminal as well. Not sure how to get at it... I tried creating `~/.config/xfce4/terminal/terminalrc` and setting a hard-coded cursor color there but I couldn't get it to make any effect (even after a computer restart). 
 - A helpful Mastodon user pointed me to his XFCE terminal config: https://github.com/zacanger/z/blob/master/.config/xfce4/terminal/terminalrc

## KDE 

### To install from Ubuntu
1. `sudo apt-get install kubuntu-desktop`?
2. When you get the chance to choose between "lightdm" and "sddm", I think you want "sddm".

More: https://www.linuxbabe.com/ubuntu/install-kde-plasma-5-7-ubuntu-16-04-ubuntu-16-10

## GNOME 

seems more difficult:  http://sourcedigit.com/20948-how-to-ubuntu-install-gnome-3-22-desktop-environment-on-ubuntu-16-04/

## What if this all goes to shit

Here's a very old "How to get back to pure Ubuntu post"? http://www.psychocats.net/ubuntu/pureubuntu
