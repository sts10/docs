# GNOME Setup

## Some System-Level Basics (Gnome)

1. In settings > "Mouse and Track Pad", put "Mouse Speed" about in the dead center and turn off "Natural Scrolling"
2. In Gnome Keyboard settings, change "Switch windows of an application" OR "Switch windows of an app directly" to "Super + Escape"
  - You may also want to remap commands like "View split on left" and "Move one monitor left", as well as the Workspace commands
3. Download the Gnome Tweaks Tool via the Pop app store. In Tweaks:
  - Remap Caps Lock to Control in "Keyboard & Mouse" > "Additional Layout Options". 
  - Suggested: Change "Mouse" "Acceleration Profile" to "Flat"
4. Change your desktop background!

5. [Disable blinking cursor in gnome-terminal](https://askubuntu.com/a/947573): In terminal: `gsettings set org.gnome.desktop.interface cursor-blink false`

## Gnome-terminal profile

Head over to [my linux-config repo](https://github.com/sts10/linux-config) to load my Gnome terminal profile.

If there's a problem, `dconf dump /org/gnome/terminal/legacy/profiles:/` might be helpful, as it lists the profiles loaded on your system.

## Changing Default Fonts

Weirdly the only place I could find this is in Gnome Tweak Tool (which I think I installed via the GUI Pop software store). Here are the defaults and what I changed them to:

```
  - Window title: Fira Sans SemiBold 10 --> Noto Sans CJK KR Bold 10
  - Interface: Fira Sans Book 10        --> Noto Sans CJK KR Regular 10
  - Document: Roboto Slab Regular 11    --> IBM Plex Sans Regular 11
  - Monospace: Fira Mono Regular 11     --> Deja Vu Sans Mono Book 11
```

You can [download IBM Plex here](https://github.com/IBM/plex).
