# Other Apps to Install

1. Installed Wire desktop via [these instructions](https://medium.com/@wireapp/a-step-forward-for-wire-for-linux-52f0538cac15)
2. [Download and install Signal](https://signal.org/download/)
3. Install Ricochet from [its website](https://ricochet.im/) -- not sure the procude here. You can also look in your distro's GUI app store, though check version.
4. Install Tor Browser (forget how exactly I did this-- maybe Tor Browser Launcher? From POP store?)
5. To install OnionShare, I followed the "Ubuntu" instructions on their [download page](https://onionshare.org/#downloads) and added their PPA. (The version in the POP store was 0.9 -- too old for me.) 
6. Install Chromium via the POP app store if you like.
7. Install Standard Notes app from [their site](https://standardnotes.org/getting-started?downloaded=linux)


## Standard Notes .desktop file

Put this in `~/.local/share/applications`

```desktop
[Desktop Entry]
Type=Application
Name=StandardNotes
# Exec=/home/$USER/standard-notes/standard-notes-2.3.8-x86_64.AppImage 
Exec=/home/$USER/standard-notes/standard-notes-*-x86_64.AppImage 
Icon=/home/$USER/standard-notes/standard-notes.png
Terminal=false
Categories=Office;Notes;
```

## Ricochet .desktop file

Download a Ricochet icon as a png if necessary. 

Then put this in `~/.local/share/applications`

```desktop
[Desktop Entry]
Type=Application
Name=Ricochet
Exec=/home/sschlinkert/other_apps/ricochet/ricochet
Icon=/home/sschlinkert/other_apps/ricochet/ricochet.png
Terminal=false
Categories=Network;InstantMessaging;Internet
```
