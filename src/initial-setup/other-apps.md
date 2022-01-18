# Other Apps to Install

- [Download and install Signal](https://signal.org/download/)
- Install Tor Browser (forget how exactly I did this-- maybe Tor Browser Launcher? From POP store?)
- Install Chromium via the POP app store if you like.
<!-- - Install Standard Notes app from [their site](https://standardnotes.org/getting-started?downloaded=linux) -->
- Consider installing Cwtch.im
- Install Wire desktop via [these instructions](https://medium.com/@wireapp/a-step-forward-for-wire-for-linux-52f0538cac15)

## Onionshare (consider the CLI)

If [OnionShare](https://onionshare.org/)'s GUI installations are throwing errors, try [installing and using the CLI](https://docs.onionshare.org/2.4/en/advanced.html#cli). I'd recommend installing it with [pipx](https://pypa.github.io/pipx/installation/) rather than pip. Here's an example:

```bash
# Install pipx (see: https://pypa.github.io/pipx/installation/)
python3 -m pip install --user pipx
python3 -m pipx ensurepath
# Install onionshare-cli
pipx install onionshare-cli
onionshare-cli --help
```

### Upgrading `onionshare-cli`

If using pipx, try `pipx upgrade onionshare-cli`

If using regular `pip3`, try something like `pip3 install --user --upgrade onionshare-cli`

## GUI Markdown editors

While Neovim/Vim is fine for editing Markdown, if you want a different aesthetic, try [Typora](https://typora.io/) (with [my forked theme](https://github.com/sts10/Turing-CSS)), [Apostrophe](https://somas.pages.gitlab.gnome.org/apostrophe/), or [Ghostwriter](https://wereturtle.github.io/ghostwriter/). 

[Manuskript](http://www.theologeek.ch/manuskript/) seems like a decent novel-writing app for Linux, but there are others.

## Standard Notes .desktop file

If you install any of the programs below, you may need to create your own "desktop" file, so that your Desktop Environment can "find" these applications. These desktop files go in `~/.local/share/applications`. 

And sometimes you need to go download a PNG file to serve as the `Icon`.

### Standard Notes

```desktop
[Desktop Entry]
Type=Application
Name=StandardNotes
Exec=/home/$USER/other-apps/standard-notes/standard-notes-*-x86_64.AppImage 
Icon=/home/$USER/other-apps/standard-notes/icon.png
Terminal=false
Categories=Office;Notes;
```

### Cwtch

([Releases](https://git.openprivacy.ca/cwtch.im/ui/releases))

```
[Desktop Entry]
Type=Application
Name=Cwtch
Exec=/home/$USER/other_apps/cwtch/ui
Icon=/home/$USER/other_apps/cwtch/cwtch.png
Terminal=false
Categories=Network;InstantMessaging;Internet
```

### Ricochet (no longer maintained)

Download a Ricochet icon as a png if necessary. 

```desktop
[Desktop Entry]
Type=Application
Name=Ricochet
Exec=/home/sschlinkert/other_apps/ricochet/ricochet
Icon=/home/sschlinkert/other_apps/ricochet/ricochet.png
Terminal=false
Categories=Network;InstantMessaging;Internet
```
