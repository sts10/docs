# GitHub and ssh keys

Make sure Git is installed 

## 1. Set git username (email) and email locally

Via [this post](https://linuxize.com/post/how-to-configure-git-username-and-email/):

To set your global commit name and email address run the git config command with the --global option:

```
git config --global user.name "Your Name"
git config --global user.email "youremail@yourdomain.com"
```

Once done, you can confirm that the information is set by running: `git config --list`

These commands save the values in the global configuration file, ~/.gitconfig:

## 2. Generate a new shh key pair on your machine, then upload the public key to Github

I followed [these instructions](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/), creating an ssh key locally, with a passphrase that I stored in my Keepass database.

## 3. ssh-agent stuff

In the `bashrc` included in this repo is some code that handles your `ssh-agent`. I got it from [this section of the Arch Linux wiki](https://wiki.archlinux.org/index.php/SSH_keys#ssh-agent). Here's the bash code if you need:

```bash
if ! pgrep -u "$USER" ssh-agent > /dev/null; then
    ssh-agent -t 1h > "$XDG_RUNTIME_DIR/ssh-agent.env"
fi
if [[ ! "$SSH_AUTH_SOCK" ]]; then
    source "$XDG_RUNTIME_DIR/ssh-agent.env" >/dev/null
fi
```

It was once this:

```bash
if ! pgrep -u "$USER" ssh-agent > /dev/null; then
    ssh-agent > ~/.ssh-agent-thing
fi
if [[ "$SSH_AGENT_PID" == "" ]]; then
    eval "$(<~/.ssh-agent-thing)"
fi
```

## 4. ssh config

`touch ~/.ssh/config` and in that file write `AddKeysToAgent yes`, as per [the Arch wiki entry](https://wiki.archlinux.org/index.php/SSH_keys#ssh-agent).

Given this setup, you're going to want to use the ssh URL (`git@github.com:sts10/terminal_and_vim_settings.git`) when cloning down repos from GitHub (as opposed to HTTPS).

## Notes/alternative approaches

Alternatively, you could try [storing ssh key in KeePassXC database](https://keepassxc.org/docs/#faq-ssh-agent-how), but I haven't had luck with that in the past.
