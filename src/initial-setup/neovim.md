# Neovim

I think I used the stable ppa and followed [these instructions](https://github.com/neovim/neovim/wiki/Installing-Neovim#ubuntu), though given [this page](https://github.com/neovim/neovim#install-from-package), we might be able to just do `sudo apt install neovim` at this point?

Before proceeding, make sure git is installed. 

A decent init.vim file is contained in [my linux-config repo](https://github.com/sts10/linux-config). 

```bash
mkdir ~/.config/nvim
curl -o ~/.config/nvim/init.vim https://raw.githubusercontent.com/sts10/linux-config/master/neovim/init.vim
```

Next, we can install our plugins by running `nvim +PlugInstall +qa`.

## Deoplete / Neovim

For Deoplete to work well, first I'd recommend setting up [pyenv](dev-env/python-pyenv.md).
  
To update Deoplete, you may need to run `:UpdateRemotePlugins` in Neovim. Neovim's `:CheckHealth` is your friend here.
