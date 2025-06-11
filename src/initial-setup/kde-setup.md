# KDE Setup and Troubleshooting

Basically, if you go with the Kubuntu "Minimal Install", configure KDE with your heart.

## Keyboard Stuff

In "Systems Settings", under Hardware, click "Input Devices". Make sure you're on the "Keyboard" section (you should see a menu titled "Keyboard Hardware and Layout"). Go to the "Advanced" tab. In this tab...

1. Under "Caps Lock behavior", check "Caps Lock is also a Ctrl"
2. Under "Position of Compose key", I like "Right Win" (aka Right Meta or Right Apple Command). This means you can insert special characters like an em dash (hold right meta/mac/win key and press the hyphen key three times). More info about the Compose Key [here](https://wiki.ubuntu.com/ComposeKey#KDE_4.x_configuration) and [here](https://cyberborean.wordpress.com/2008/01/06/compose-key-magic/) and [here](https://userbase.kde.org/Tutorials/ComposeKey). (An alternative method: Under "Key to choose the 3rd level" check "Right Alt; Shift+Right Alt as Compose". This allows you to insert an em dash by holding Right Alt + Shift and then inserting three hyphens in a row.)

## KDE Troubleshooting

### Everything looks big!

If, after installing the proper NVIDIA drivers and restarting the machine, everything looks big, go to Fonts settings menu and "Force" the DPI to 96.

### If external monitors aren't being recognized by your laptop

If external monitors aren't being recognized by your laptop, try opening "NVIDIA X Server Settings", then select "X Server Display Configuration" from the menu you on the left. Try clicking "Detect Displays". 

If the external monitor appears in the layout, it may just be "disabled". If that's the case, go to the drop-down menu on the right side of the window labeled "Configuration" and try choosing "X screen 0".

[An AskUbuntu question about this issue](https://askubuntu.com/questions/1083733/kubuntu-18-04-laptop-wont-recognize-external-monitor)

#### Are your drivers up-to-date?

If your machine isn't recognizing an external monitor, another possible issue may be that you need to upgrade your NVIDIA to match your current Linux kernel. For example, at one point I needed to upgrade to 515 by running `sudo apt install nvidia-driver-515`. Probably should run `flatpak update` right after. 

How could I have known I needed to do this? [A helpful Mattermost users writes](https://chat.pop-os.org/pop-os/pl/c8c6qrkfztdbujy5js8wc6gg9o):

> From the apt upgrade output, it probably said something about the Nvidia DKMS module not working with the 6.0.2 kernel. From there you'd have to know to try other Nvidia driver versions. Also we just released some updates that should make this not happen as much. It's definitely not ideal for this to happen.

More broadly, I think you need to use NVIDIA drivers (rather the FOSS ones) to use an external monitor with my Oryx Pro. I think.

**June 2025 update**: System76 tech suggests `sudo apt install nvidia-driver-550` or `sudo apt install nvidia-driver-550=550.144.03-0ubuntu0.22.04.1` to solve a similar issue to the one described on this page (which arose while running Pop_OS 22.04 LTS).
