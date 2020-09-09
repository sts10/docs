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

## rust-analyzer and LanguageServer

To get some nice Rust features in Neovim, we're going to install [rust-analysis](https://rust-analyzer.github.io/manual.html). Below, I outline the [relatively simple install option that uses LanguageClient-neovim](https://rust-analyzer.github.io/manual.html#languageclient-neovim), though do check documentation for latest instructions.

1. [Install rust-analyzer Language Server Binary](https://rust-analyzer.github.io/manual.html#rust-analyzer-language-server-binary) by running the following.
```bash
git clone https://github.com/rust-analyzer/rust-analyzer.git && cd rust-analyzer
cargo xtask install --server
```

Think this installs the project's code to `~/.config/nvim/rust-analyzer/`. Executable is `rust-analyzer`, so can check that it's in your PATH by running `rust-analyzer --version`. Assume you'd upgrade by running `git pull && cargo xtask install --force --server`?

2.  Configure by adding this to your vim/neovim config file (replacing the existing Rust-specific line if it exists):

```vim
let g:LanguageClient_serverCommands = {
\ 'rust': ['rust-analyzer'],
\ }
```

3. Get the neovim LanguageClient installed

```vim
Plug 'autozimu/LanguageClient-neovim', {
\ 'branch': 'next',
\ 'do': 'bash install.sh',
\ }

" (Optional) Multi-entry selection UI.
Plug 'junegunn/fzf'
```

Then down below the `g:LanguageClient_serverCommands` bit:
```vim
nmap <F5> <Plug>(lcn-menu)
```

4. Back in the terminal, run `nvim +PlugInstall +UpdateRemotePlugins +qa`

Think you should ne good-to go? F5 will give you some options for analysis. 

### Notes on alternative approaches to making Neovim more of a Rust IDE

For rust-analyzer, there is [an alternative installation process described](https://rust-analyzer.github.io/manual.html#coc-rust-analyzer) where it's integrated with [coc.nvim](https://github.com/neoclide/coc.nvim), which you might be using anyway, or like for its other features. To me, right now, it seems a bit intense, and requires Node to be installed.

There also seems to be another way to "teach" Neopvim about the Rust language using [**Racer** ("code completion for Rust")](https://github.com/racer-rust/racer), but I think I tried it before and it through halting errors as I was typing code.
