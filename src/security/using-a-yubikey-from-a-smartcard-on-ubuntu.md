# Using a PGP private key from a Smartcard on Ubuntu

I think I need to :
1. add the key's public half 
  a. get the .asc file onto your system. 
  b. run `gpg2 --import <file-name>.asc`
2. Plug in the card
3. try `gpg2 --card-status` If that doesn't work try installing scdaemon and pcscd with `sudo apt install scdaemon` and then `sudo apt install pcscd`. You may also need to `sudo apt install gpgsm`
  - you may also need to kill and restart scdaemon with: 
  ```
  killall scdaemon
  pgrep scdaemon
  ```

You can now encrypt and decrypt files with the pgp keys on your martkey using the `gpg2` command line tool. 

## GUI 

To add GUI support on Xfce, while using Thunar file manager, it looks like I'm going to need to build some [Thunar custom actions](https://help.ubuntu.com/community/ThunarCustomActions), which doesn't seem ideal. Xcfe doesn't use Nautilus by default, so I doubt installing `seahorse-nautilus` is going to do me any good.


