# Installing Pyenv

I'm not sure if you have to _uninstall_ any versions of Python before you do this, but I doubt it. You might want to checkout your bashrc to make sure there isn't any weird Python PATH stuff in there before we start.

1. Install [Pyenv](https://github.com/pyenv/pyenv#installation), probably via the ["Basic GitHub Checkout" method](https://github.com/pyenv/pyenv#basic-github-checkout)
2. Add the necessary stuff to your `.bashrc` (not `.bash_profile`)
3. Restart terminal
4. Maybe [install dependencies](https://github.com/pyenv/pyenv/wiki#suggested-build-environment)? (You may be good to go already.)
5. Run `pyenv install --list` and pick new-ish-but-stable versions of  python2 and python3 to install. For example: `pyenv install 3.7.4 && pyenv install 2.7.16`
6. You can set version 3 as the global, with 2 as fall-back: `pyenv global 3.7.4 2.7.16`. You could also set the `system` version as a fallback, with `pyenv global 3.7.0 2.7.15 system`.
7. Check that `pip` is installed (I think it's included?). You should be able to upgrade `pip3` with `pip3 install --upgrade pip` and `pip2` with `pip2 install --upgrade pip`

**Let's see how we did**: If successful, `python2` gets you Python 2, `python3` or `python` gets you Python 3. Similar with `pip2`/`pip3`/`pip`. 

To install [autosub](https://github.com/agermanidis/autosub) (which I think necessitates Python2) run `pip2 install autosub`

## Deoplete / Neovim

Now that we've got a nice little Python and Pip environment set up, let's make sure Deoplete is using it.

If you use Neovim + Deoplete, you probably want to run `pip3 install neovim` to ensure Deoplete works smoothly (see [Deoplete's requirements](https://github.com/Shougo/deoplete.nvim#requirements)).

I also ran `pip2 install neovim` because Neovim's `:CheckHealth` told me too. 

At this point, you may need to update Deoplete by running `:UpdateRemotePlugins` in Neovim. (Neovim's `:CheckHealth` is your friend here.)
