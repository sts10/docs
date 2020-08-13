# PGP

## GNU Privacy Assistant 
For a GPG GUI application, try `sudo apt install gpa` which installs a program called ["GNU Privacy Assistant"](https://help.ubuntu.com/community/GnuPrivacyGuardHowto#Graphical_Interfaces)


## Using a PGP private key from a Smartcard on Ubuntu

1. Add the public key to your system: Get the .asc file onto your system, then run `gpg2 --import <file-name>.asc`
2. Plug the smartcard into your computer.
3. Try running `gpg2 --card-status`. 

**Troubleshooting**
- If the above doesn't work try installing scdaemon and pcscd with `sudo apt install scdaemon` and then `sudo apt install pcscd`. You may also need to `sudo apt install gpgsm`
- You may also need to kill and restart scdaemon with:
```
killall scdaemon
pgrep scdaemon
```

You can now encrypt and decrypt files with the pgp keys on your smartkey using the gpg2 command line tool. To decrypt a file run something like this: `gpg --output test --decrypt '/home/schlinkert/keepass-databases/key-files/fly1.key.gpg'`. Check that you can decrypt a Keepass database AND that you can alter settings.

