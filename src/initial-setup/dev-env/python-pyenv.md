# Python 

## Installing Pyenv

I'm not sure if you have to _uninstall_ any versions of Python before you do this, but I doubt it. You might want to checkout your bashrc to make sure there isn't any weird Python PATH stuff in there before we start.

1. Install [Pyenv](https://github.com/pyenv/pyenv#installation), probably via the ["Basic GitHub Checkout" method](https://github.com/pyenv/pyenv#basic-github-checkout). Could also try [new auto-installer](https://github.com/pyenv/pyenv-installer), which seems to make updating easier.
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

If you use Neovim + Deoplete, you probably want to run `pip3 install neovim` or `pip3 install pynvim` to ensure Deoplete works smoothly (see [Deoplete's requirements](https://github.com/Shougo/deoplete.nvim#requirements)).

Another tip to try is to explicitedly tell Neovim which Python3 to use. Do this by including this line in your Neovim config file: 

```vim
let g:python3_host_prog = expand('~/.pyenv/shims/python')
```

I don't think you need to provide Neovim with a version of Python2 these days to make Neovim do its job well.
<!-- I also ran `pip2 install neovim` because Neovim's `:CheckHealth` told me too. --> 

At this point, you may need to update Deoplete by running `:UpdateRemotePlugins` in Neovim. (Neovim's `:CheckHealth` is your friend here.)

## Tips for _writing_ Python in Vim/Neovim

### Formatter
For a formatter, I like [Black](https://github.com/psf/black/blob/master/docs/editor_integration.md) so far. All you need to integrate it into Vim is to install the Vim plugin:

```vim
Plug 'psf/black', { 'branch': 'stable' }
```

And I'll probably add this to my vimrc to have it run on save: 

```vim
autocmd BufWritePre *.py execute ':Black'
```

Note that I did **not** need to run any pip install commands to get it working.

### Syntax and style checker

For checking Python syntax and style you could try [flake8](https://pypi.org/project/flake8/). 

After installing with `pip install flake8` ([reference](https://pypi.org/project/flake8/)), you can run it on individual python files from the command line with `flake8 <filename>.py`, which will print out recommendations to the terminal. 

It also has a [corresponding Vim plugin](https://github.com/nvie/vim-flake8), though after installing it the default mapping, `<F7>`, didn't work, so I had to run `:call flake8#Flake8()`. Obviously I could try mapping it to a key myself.

2023 Update: Try [ruff](https://github.com/charliermarsh/ruff) and [these docs on Vim & Neovim integration](https://beta.ruff.rs/docs/editor-integrations/#language-server-protocol-unofficial)!

## 2020 updates / notes

These two blog posts may offer better, newer solutions for Python environment set ups:

- [https://read.acloud.guru/my-python-setup-77c57a2fc4b6](https://read.acloud.guru/my-python-setup-77c57a2fc4b6)
- [https://jacobian.org/2019/nov/11/python-environment-2020/](https://jacobian.org/2019/nov/11/python-environment-2020/)

### pipx

Specifically, if you've been using pip to install packages solely for use on the command-line (as opposed to active development using Python), like the `neovim` package, I'm hoping that [pipx](https://pypi.org/project/pipx/) may be a better, more self-contained solution. Though given that you need either Homebrew or pip to install pipx, it might not be as strong of a solution on Ubuntu as it is on MacOS.

## 2023 updates

* [Rye](https://github.com/mitsuhiko/rye) looks like a possible all-in-one solution for future machines where I need access to Python.
* For packages: [uv](https://github.com/astral-sh/uv)? For formatting: [ruff](https://github.com/astral-sh/ruff).

* There's also ["Python launcher"](https://github.com/brettcannon/python-launcher)?
