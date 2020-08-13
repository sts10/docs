# Rsync

Rsync is a nifty back-up CLI tool. I likely installed it with `sudo apt install rsync`.

## Handy Bash function

Throw this in your `~/.bashrc`: 

```bash
function rsync_all {
  if [ -d /media/sschlinkert/Seagate\ 4TB ]
  then
    echo "External hard drive is mounted"
    echo "Running a couple rsync commands:"
    echo "Syncing keepass-databases..."
    rsync -arAX /home/sschlinkert/keepass-databases '/media/sschlinkert/Seagate 4TB/back-ups-rsync/'
    echo "Syncing pgp data..."
    rsync -arAX /home/sschlinkert/pgp '/media/sschlinkert/Seagate 4TB/back-ups-rsync/'
    echo "Syncing Documents, with --delete flag"
    rsync -arAX --delete /home/sschlinkert/Documents '/media/sschlinkert/Seagate 4TB/back-ups-rsync/'
    echo "Syncing code, with --delete flag"
    rsync -arAX --delete /home/sschlinkert/code '/media/sschlinkert/Seagate 4TB/back-ups-rsync/'
    echo "All done running rsync"
  else
    echo "Could not find Seagate 4 TB. It may not be mounted"
  fi
}
```
