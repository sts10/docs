# Rust + Neovim

This assumes you have [Neovim](../neovim.html) installed already.

1. [Install Rust](https://www.rust-lang.org/en-US/install.html). Make sure to add `export PATH="$HOME/.cargo/bin:$PATH"` to end of `~/.bashrc`. Note: you can uninstall at anytime with `rustup self uninstall`.

2. Install [rustfmt](https://github.com/rust-lang-nursery/rustfmt) and [its Vim counterpart, rust.vim](https://github.com/rust-lang/rust.vim#formatting-with-rustfmt)

3. Install [Rust Clippy](https://github.com/rust-lang-nursery/rust-clippy#usage)

## Getting Autocomplete in Neovim with Deoplete 

1. Install [Deoplete](https://github.com/Shougo/deoplete.nvim#install)
  - You may first be required to install some Python stuff. You may want to get your [pyenv setup](python-pyenv.html) working first. However, in a pinch, these commands have worked for me in the past: 
    - Install pip3 with `sudo apt-get install python3-pip` 
    - and then `pip3 install neovim`

2. Check that `let g:deoplete#enable_at_startup = 1` is set in your Vim config file.

3. Install [Racer](https://github.com/racer-rust/racer)

4. Make sure [Vim Racer](https://github.com/racer-rust/vim-racer) is installed. My vim-racer config is:

```vim
Plug 'racer-rust/vim-racer'
set hidden
let g:racer_cmd = "~/.cargo/bin/racer"
let g:racer_experimental_completer = 1
```

5. Make sure you you've got the rust.vim Vim plugin installed: `Plug 'rust-lang/rust.vim'`

## Language Server

1. Install [Rust Language Server](https://github.com/rust-lang/rls#setup) 
2. Get [LanguageClient-Neovim](https://github.com/autozimu/LanguageClient-neovim) setup. 

Altogether your Neovim `init.vim` is going to look something like this:

```vim
" Rust Language Server
Plug 'autozimu/LanguageClient-neovim', {
\ 'branch': 'next',
\ 'do': 'bash install.sh',
\ }

Plug 'junegunn/fzf'

" Auto-complete
if has('nvim')
  Plug 'Shougo/deoplete.nvim', { 'do': ':UpdateRemotePlugins' }
else
  Plug 'Shougo/deoplete.nvim'
  Plug 'roxma/nvim-yarp'
  Plug 'roxma/vim-hug-neovim-rpc'
endif

" Language or filetype specific
Plug 'rust-lang/rust.vim'
Plug 'racer-rust/vim-racer'


" ...


" Language Server Config
let g:LanguageClient_serverCommands = {
\ 'rust': ['~/.cargo/bin/rustup', 'run', 'stable', 'rls'],
\ }

nnoremap <silent> K :call LanguageClient#textDocument_hover()<CR>
nnoremap <silent> gd :call LanguageClient#textDocument_definition()<CR>
" got an error with this on only attempt
nnoremap <silent> gr :call LanguageClient#textDocument_rename()<CR>

" Deoplete (general auto-complete)
let g:deoplete#enable_at_startup = 1

" Racer (Rust auto-complete)
let g:racer_cmd = "~/.cargo/bin/racer"
let g:racer_experimental_completer = 1

" ...

set hidden
```

Then, from the command line, run `nvim +PlugInstall +UpdateRemotePlugins +qa` to install all that right. 



