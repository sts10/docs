# Customizing Appearance of XFCE (Ubuntu)

## Desktop Background

1. Pick one (I found one I liked [here](https://www.buzzfeed.com/jessicaprobus/26-remarkably-soothing-desktop-backgrounds?utm_term=.uhwBX0qylL#.vxgE1Z8Yar)). 
2. Download the image file to your Pictures folder. 
3. Go to Settings Manager > Desktop > Background. In bottom-right change Folder to Pictures and find your desired background.

## "Theme" 

I went with axiom, which I got [here](https://www.xfce-look.org/p/1016679/). To install it: 
1. I downloaded [the tar file](https://www.xfce-look.org/p/1016679/), 
2. In terminal I ran `mkdir ~/.themes`
3. I then extracted two directories from the tar file called "axiom" and "axiomd", and then moved them both into the new `~/.themes` directory. 
4. Go to Settings Manager > Appearance and choose either axiom or axiomd
5. Then is Settings Manager > Window Manager > Style and select either axiom or axiomd

## Icons

I went with "Papers" icons for now, which you can find download instructions for on [the offical website](https://snwh.org/paper/download). After running those updates, I went to Settings Manager > Appearance > Icons and selected Paper. 

## Login Window

Go to Settings Manager > LightDM GTK + Greeter Settings and select the theme and icon set you like. You can also change your user image or remove it all together. Unfortunately, for me, axiom was not available here, so I went with Adwaita for now. 

Note: [This video](https://www.youtube.com/watch?v=GR2y0xOIIdI) helped me quite a bit:

<iframe width="560" height="315" src="https://www.youtube.com/embed/GR2y0xOIIdI" frameborder="0" allowfullscreen></iframe>

## Font

I'm going with Noto Sans for now (the actual choice says "Noto Sans CJK JP"). I selected this font in Settings Manager > Appearance > Fonts. I also selected basically every where else I encountered a choice of font in Settings. 

## Panels

Odds are you Panel 1 is on top of your screen, and panel 2 is the dock-like panel that I think starts at the bottom of your screen. 

For customizing Panel 1, I followed some of the instructions in the first minute of [this video](https://www.youtube.com/watch?v=tJQ0y2XMoMw). I set the mode to Vertical, which puts in on the left, increased transparency, and made it 48 pixels wide, and had it never hide. Then, in Items > Applications Menu I deselected "show button title" and changed the image. In Items > Window Buttons I deselected "Show button labels", selected "Show flat buttons", deselected "Show handle", and set Window grouping to always.

I'm not sure what I want out of panel 2 (the dock) yet, so I set it to be pretty small and have it hide intelligently. 
