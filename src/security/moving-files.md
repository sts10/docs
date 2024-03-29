# Tools for moving files between computers

I have not vetted or reviewed any of these tools. I also do not condone using any of these tools for illegal activity!

## Tools that use Tor
- [OnionShare](https://onionshare.org/) -- Offers both a GUI and [command-line tool](https://docs.onionshare.org/2.4/en/advanced.html#cli) (would recommend using [pipx](https://pypa.github.io/pipx/installation/) to install the CLI: `pipx install onionshare-cli`).

## CLI tools
- [Magic Wormhole](https://github.com/magic-wormhole/magic-wormhole) 
- [croc](https://github.com/schollz/croc) -- written in Go, looks good
- [qrcp](https://github.com/claudiodangelis/qrcp/) -- for transferring to and from a mobile device.

## Cloud-based file transferring services
- [Bitwarden Send](https://bitwarden.com/products/send/) 
- [Standard Notes FileSend](https://filesend.standardnotes.org/) 
<!-- - https://send.tresorit.com/ -->

## Also helpful
- [Dangerzone](https://dangerzone.rocks/) ([GitHub](https://github.com/freedomofpress/dangerzone)) takes potentially dangerous PDFs, office documents, or images and converts them to safe PDFs
- [age](https://github.com/FiloSottile/age) is a new PGP alternative for encrypting/decrypting files 
- [Cwtch](https://cwtch.im/) now supports file-sharing, but the tool is, overall, still in beta as of this writing.

## A GPG GUI, if you must

`sudo apt install gpa` installs a GUI called "GNU Privacy Assistant". You can [read more about it here](https://help.ubuntu.com/community/GnuPrivacyGuardHowto#Graphical_Interfaces).
