# Ruby and rbenv

1. Install [rbenv (via "basic github checkout")](https://github.com/rbenv/rbenv#basic-github-checkout) 
2. Install [ruby-build](https://github.com/rbenv/ruby-build#installation) as an rbenv plugin. 
3. At this point you made need to run `sudo apt-get install -y libssl-dev libreadline-dev zlib1g-dev` before proceeding
4. `rbenv install -l` lists available versions of Ruby. Pick one to install. 
5. Set that version to global.

You can update the Ruby versions available to rbenv by running `rbenv_upgrade` (found in `bashrc`).


```bash
function rbenv_upgrade {
  cd ~/.rbenv && git pull
  cd ~/.rbenv/plugins/ruby-build && git pull
  cd ~
}
```
