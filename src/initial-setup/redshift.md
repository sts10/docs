# Redshift

## Redshift + Xorg + KDE

If you're running KDE and Xorg, you'll likely need to use Redshift to tint your screen at night. "Redshift Control" is a KDE widget that gives you a nice GUI to configure Redshift (found by searching the "Get new widgets" interface).

I also found (in [this video](https://youtu.be/O0K9TzKZ9x4?t=1016)) what might be the command line way to install both redshift and the plasma widget:

```bash
sudo apt install redshift plasma-applet-redshift-control
```

Although [elsewhere](https://linoxide.com/tools/install-use-redshift-ubuntu-16-04/) I've seen an additional program recommended:

```bash
sudo apt-get install plasma-widget-redshift plasma-applet-redshift-control
```

## Configuring Redshift in Plasma

First, I'd recommend moving the widget to the task bar. Then, to configure it, simply right-click the widget and click configure. Hit "Locate" to automatically locate your position. Then for temperature 6500 for Day and 3250 for Night seems to work well.

## GTK (GNOME) 

For gtk-based desktop environments like GNOME, you're probably going to want to run `sudo apt-get install redshift redshift-gtk`

