# PGP / GPG

Note from 2022: Consider using [age](https://github.com/FiloSottile/age), especially for file encryption, rather than PGP.

## GNU Privacy Assistant 

For a GPG GUI application for Linux/Ubuntu for key management etc., try `sudo apt install gpa` which installs a program called ["GNU Privacy Assistant"](https://help.ubuntu.com/community/GnuPrivacyGuardHowto#Graphical_Interfaces)

## GPG conf

Let's make sure we've got good GPG settings. To do this, create a new file at `~/.gnupg/gpg.conf`. 

Then do one or all of the following:

1. Trust the decent gpg.conf I made for myself in 2021 below.
2. Copy [this guide's "hardened" config](https://github.com/drduh/YubiKey-Guide#harden-configuration) ([actual gpg.conf file](https://github.com/drduh/config/blob/master/gpg.conf)) 
3. Read through [this guide](https://riseup.net/en/security/message-security/openpgp/best-practices#putting-it-all-together), which points to [this Github repo](https://github.com/ioerror/duraconf/tree/master/configs/gnupg).

### A decent gpg.conf

Put this in `~/.gnupg/gpg.conf`

```text
# This gpg.conf takes inspiration from: 
#   - Riseup OpenPGP Best Practices 
#     https://help.riseup.net/en/security/message-security/openpgp/best-practices
#   - DrDuh: https://github.com/drduh/config/blob/master/gpg.conf
#
# Put this in ~/.gnupg/gpg.conf

#-----------------------------
# behavior
#-----------------------------

# Disable inclusion of the version string in ASCII armored output
no-emit-version

# Disable comment string in clear text signatures and ASCII armored messages
no-comments

# Display long key IDs
keyid-format 0xlong

# List all keys (or the specified ones) along with their fingerprints
with-fingerprint

# Display the calculated validity of user IDs during key listings
list-options show-uid-validity
verify-options show-uid-validity

# Try to use the GnuPG-Agent. With this option, GnuPG first tries to connect to
# the agent before it asks for a passphrase.
use-agent

# Enable smartcard (from: https://github.com/drduh/config/blob/master/gpg.conf#L41-L42)
use-agent

#-----------------------------
# keyserver
#-----------------------------

# This is the server that --recv-keys, --send-keys, and --search-keys will
# communicate with to receive keys from, send keys to, and search for keys on
keyserver hkps://keys.openpgp.org/

# Set the proxy to use for HTTP and HKP keyservers - default to the standard
# local Tor socks proxy
# It is encouraged to use Tor for improved anonymity. Preferrably use either a
# dedicated SOCKSPort for GnuPG and/or enable IsolateDestPort and
# IsolateDestAddr
#keyserver-options http-proxy=socks5-hostname://127.0.0.1:9050

# Don't leak DNS, see https://trac.torproject.org/projects/tor/ticket/2846
keyserver-options no-try-dns-srv

# When using --refresh-keys, if the key in question has a preferred keyserver
# URL, then disable use of that preferred keyserver to refresh the key from
keyserver-options no-honor-keyserver-url

# When searching for a key with --search-keys, include keys that are marked on
# the keyserver as revoked
keyserver-options include-revoked


#-----------------------------
# algorithm and ciphers
#-----------------------------

# list of personal digest preferences. When multiple digests are supported by
# all recipients, choose the strongest one
personal-cipher-preferences AES256 AES192 AES CAST5

# list of personal digest preferences. When multiple ciphers are supported by
# all recipients, choose the strongest one
personal-digest-preferences SHA512 SHA384 SHA256 SHA224

# message digest algorithm used when signing a key
cert-digest-algo SHA512

# This preference list is used for new keys and becomes the default for
# "setpref" in the edit menu
default-preference-list SHA512 SHA384 SHA256 SHA224 AES256 AES192 AES CAST5 ZLIB BZIP2 ZIP Uncompressed
```

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

