# Using restic to back up files

Here's [the official user's guide from restic](https://restic.readthedocs.io/en/latest/020_installation.html), which I found pretty helpful. Since I'm just putting backups onto USB devices, I only need to follow the instructions for a "local" back up.

### Installing restic on Ubuntu

`sudo apt install restic`

Let's check the version really quick:

`restic version` prints `restic 0.9.6 compiled with go1.12.12 on linux/amd64`. A little outdated -- 0.12.1 is [on Github](https://github.com/restic/restic/releases) as I write this -- but it'll do.

### Getting set up with restic

Now let's do some backing up!

First, let's try to gain a bare-bones conceptual understanding of how Restic works. Restic has a concept called "repositories", which is where your backup(s) will live. [From the docs](https://restic.readthedocs.io/en/latest/030_preparing_a_new_repo.html#preparing-a-new-repository):

> The place where your backups will be saved is called a “repository”. This chapter explains how to create (“init”) such a repository. The repository can be stored locally, or on some remote server or service. 

Basically we use restic to pull data into these backup repositories. So for me, my repository (singular for now) will be on my external hard drive.

### Initializing a Restic repository

OK, let's initialize one of these repositories. On my external hard drive, I ran:

```bash
mkdir /media/sschlinkert/external_harddrive/restic-repo
restic init --repo /media/sschlinkert/external_harddrive/restic-repo
```

Restic now asks us to create a password for this back-up "repo" (restic uses encryption). We'll be asked to enter the new password as second time to confirm.

### Doing our first backup

Finally, time to back-up some data. Following [the docs](https://restic.readthedocs.io/en/latest/040_backup.html), I composed this command using the `backup` subcommand to backup my entire `home/` directory:

```bash
restic -r /media/sschlinkert/external_harddrive/restic-repo --verbose backup /home/sschlinkert/
```

We will do subsequent snapshots by running the exact same command at later times. In other words this is the command you'd run every night or week to keep the backup up-to-date.

### Ensure a snapshot was created

We can do a quick check to see our first snapshot by running: 

```bash
restic -r /media/sschlinkert/external_harddrive/restic-repo snapshots
```

### Check integrity of that snapshot

One thing that's nice about restic is that you can check the state or "health" of the backup.

```bash
restic -r /media/sschlinkert/external_harddrive/restic-repo check
```

which should output a block of text that should end with: `no errors were found`. Awesome!

### Now try restoring our data!

Now let's say something bad has happened and we need to restore our files from this back-up repo. 

Our files aren't exactly just sitting in a directory, as they are when using a tool like rsync. (This is a bit of a downside for restic, but it's fine.) Instead, we have to use restic's `restore` subcommand.

First, we copy the snapshot id of the snapshot we want to restore from from that `snapshot` command. Then we'll make a new directory to restore to, and restore to it using restic's restore subcommand:

```bash
mkdir ~/Documents_restored
restic -r /media/sschlinkert/external_harddrive/restic-repo restore 37769142 --target ~/Documents_restored
```

This'll take a while, but when it's done our data should be restored to the location we specified, `~/Documents_restored`. At that point, we can do a sanity-check with:

```bash
ls ~/Documents_restored
```

## A simpler approach for a small directory

I've got a small directory of very important documents. This directory is included in my restic snapshots, but I also want to put it in other locations as redundancies. One such location is Dropbox. However, I want it to encrypt it before I upload it to Dropbox.

### Step 1: Compressing with tar

It's a directory (rather than a single file), so the first thing I'm going to do is put it in a tar ball.

```bash
tar -czvf important_documents.tar.gz important_documents/
```

Running this command creates important_documents.tar.gz for us. This single, compressed file will be easier for us to encrypt. (If you need more compression, try `tar -cjvf`.)

### Step 2: Encrypting with age

I've chosen to use an encryption tool called [age](https://github.com/FiloSottile/age) to encrypt and decrypt this file. [I wrote a short guide here](https://sts10.github.io/2021/09/06/exploring-age-1-point-0.html), but this'll work for our purposes:

```bash
age -p important_documents.tar.gz > important_documents.tar.gz.age
```

Enter a new passphrase twice. Age will create an encrypted file called `important_documents.tar.gz.age`. 

We can safely upload this `important_documents.tar.gz.age` file to Dropbox or another unencrypted cloud provider (I do this through the website, but I'm sure there's a way to do it through the command line...).

### Step 3: Decrypting and decompressing

We of course need to be able to restore these files. First we decrypt:  

```bash
age -d important_documents.tar.gz.age > important_documents.tar.gz
```

Enter your passphrase to decrypt to `important_documents.tar.gz`. Then we extract the files from the tar ball:

```bash
tar -xzvf important_documents.tar.gz
```

### All together (one-liners)

I think these work.

```bash
# compress and encrypt
tar -czv important_documents/ | age -p > important_documents.tar.gz.age
# decrypt and extract
age -d important_documents.tar.gz.age | tar -xzv
```

### Using symmetrical GPG encryption

If you don't want to use age (it's new), you can use gpg. 

Encrypting:
```bash
gpg -c important_documents.tar.gz
```

Decrypting:
```bash
gpg --output important_documents.tar.gz --decrypt important_documents.tar.gz.gpg
```

