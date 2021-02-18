# Some App Installation and Hard Drive Mounting Basics

## Installing Snap

Think it's just `sudo apt install snapd`. 

Know that, sometimes in order to _update_ applications that you install via Snap need to be updated with a command like `snap refresh` or `snap refresh <app_name>`. Run `snap refresh --help` for more information.

## Generic upgrade line

`sudo apt-get update && sudo apt-get dist-upgrade` is a good way to upgrade everything.

## How to install from an AppImage if it's not going easily

[This tutorial](https://itsfoss.com/use-appimage-linux/) instructs to right-click the download appimage file, go to "Properties" > "Permissions" and then check "Allow executing file as program". Alternatively `chmod u+x <AppImage File>` to make it executable.

## How to mount an external hard drive that's formatted as exFAT

Simply install these programs by running this line: `sudo apt-get install exfat-fuse exfat-utils` ([via](https://www.reddit.com/r/Ubuntu/comments/6r954q/mount_exfat_drive_in_ubuntu_1704/)). 

## Desktop files

The Arch Wiki has [an entry on desktop entries](https://wiki.archlinux.org/index.php/desktop_entries), which notes

> Desktop entries for applications, or .desktop files, are generally a combination of meta information resources and a shortcut of an application. These files usually reside in `/usr/share/applications/` or `/usr/local/share/applications/` for applications installed system-wide, or `~/.local/share/applications/` for user-specific applications. User entries take precedence over system entries.

### Desktop file example 

At `~/.local/share/applications/standard-notes.desktop` paste the following:

```
[Desktop Entry]
Type=Application
Name=StandardNotes
Exec=/home/$USER/standard-notes/standard-notes-*-x86_64.AppImage 
Icon=/home/$USER/standard-notes/standard-notes.png
Terminal=false
Categories=Office;Notes;
```

See the page on Standard Notes for more.
