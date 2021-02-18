# Rust + Neovim

This assumes you have [Neovim](../neovim.html) installed already.

1. [Install Rust](https://www.rust-lang.org/en-US/install.html). Make sure to add `export PATH="$HOME/.cargo/bin:$PATH"` to end of `~/.bashrc`. Note: you can uninstall at anytime with `rustup self uninstall`.

2. Install [rustfmt](https://github.com/rust-lang-nursery/rustfmt) and [its Vim counterpart, rust.vim](https://github.com/rust-lang/rust.vim#formatting-with-rustfmt)

3. Install [Rust Clippy](https://github.com/rust-lang-nursery/rust-clippy#usage)

## Getting Autocomplete in Neovim with Deoplete 

Install [Deoplete](https://github.com/Shougo/deoplete.nvim#install)
  - You may first be required to install some Python stuff. You may want to get your [pyenv setup](python-pyenv.html) working first. However, in a pinch, these commands have worked for me in the past: 
    - Install pip3 with `sudo apt-get install python3-pip` 
    - and then `pip3 install neovim`

Then make sure you've got all this (or something similar) in your init.vim file:

```vim
" Auto-complete
if has('nvim')
  Plug 'Shougo/deoplete.nvim', { 'do': ':UpdateRemotePlugins' }
else
  Plug 'Shougo/deoplete.nvim'
  Plug 'roxma/nvim-yarp'
  Plug 'roxma/vim-hug-neovim-rpc'
endif

" then further down
let g:deoplete#enable_at_startup = 1
```

## rust-analyzer and LanguageServer

To get some nice Rust-specific, IDE-esque goodies in Neovim, we're going to install [rust-analyzer](https://rust-analyzer.github.io/manual.html). Below, I outline the [relatively simple installation option that uses LanguageClient-neovim](https://rust-analyzer.github.io/manual.html#languageclient-neovim), though do check documentation for latest instructions.

### 1. Install rust-analyzer Language Server Binary

[Install rust-analyzer Language Server Binary](https://rust-analyzer.github.io/manual.html#rust-analyzer-language-server-binary) by running the following:

```bash
git clone https://github.com/rust-analyzer/rust-analyzer.git && cd rust-analyzer
cargo xtask install --server
```

Think this installs the project's code to `~/.config/nvim/rust-analyzer/`. Executable is `rust-analyzer`, so can check that it's in your PATH by running `rust-analyzer --version`. Assume you'd upgrade by running `git pull && cargo xtask install --force --server`?

### 2. Configure by adding this to your vim/neovim config file...

...replacing the existing Rust-specific line if it exists:

```vim
let g:LanguageClient_serverCommands = {
\ 'rust': ['rust-analyzer'],
\ }
```

### 3. Get the neovim LanguageClient installed

```vim
Plug 'autozimu/LanguageClient-neovim', {
\ 'branch': 'next',
\ 'do': 'bash install.sh',
\ }

" (Optional) Multi-entry selection UI.
Plug 'junegunn/fzf'
```

Then down below the `g:LanguageClient_serverCommands` bit, let's add some mappings. The [plugin's readme provides some ideas](https://github.com/autozimu/LanguageClient-neovim#quick-start), but as a minimum:

```vim
nmap <F5> <Plug>(lcn-menu)
```

### 4. Install plugins

Back in the terminal, run `nvim +PlugInstall +UpdateRemotePlugins +qa`

Think you should now be good-to go? F5 will give you some options for analysis. 

## Notes on alternative approaches to making Neovim more of a Rust IDE

### Alternative methods of installing rust-analyzer

For rust-analyzer, there is [an alternative installation process described](https://rust-analyzer.github.io/manual.html#coc-rust-analyzer) where it's integrated with [coc.nvim](https://github.com/neoclide/coc.nvim), which you might be using anyway, or like for its other features. To me, right now, it seems a bit intense, and requires Node to be installed.

### Racer

There also seems to be another way to "teach" Neovim about the Rust language using [**Racer** ("code completion for Rust")](https://github.com/racer-rust/racer) and its [associated Vim plugin](https://github.com/racer-rust/vim-racer), but I think I tried it before and it through halting errors as I was typing code.
