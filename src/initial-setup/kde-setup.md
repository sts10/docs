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
