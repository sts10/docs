# Syncthing

I installed Syncthing via the instructions at the top of [this page](https://apt.syncthing.net/)

I then setup Syncthing, including my KeePass database. 

## Useful bash functions

```bash
# Via: https://sts10.github.io/2018/11/27/syncthing-and-tmux.html
function ss {
  if tmux has-session -t synct 2>/dev/null; then
    echo "Syncthing session already started at http://127.0.0.1:8384/" >&2
    return 1
  fi
  
  echo "Starting up Syncthing at http://127.0.0.1:8384/"
  tmux new-session -d -s synct "syncthing -no-browser"
}

function se {
  if ! tmux has-session -t synct 2>/dev/null; then
    echo "No Syncthing session to end." >&2
    return 1
  fi
  
  echo "Stopping Syncthing and killing the tmux session"
  tmux send-keys -t synct C-c
}

```
