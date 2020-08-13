## How to Install Neovim on Lubuntu 16.04

I'm using Lubuntu 16.04 and we're assuming that we're going to be using gnome-terminal. I couldn't figure out how to get HEX colors in Vim when using Lubuntu's default Terminal application, LXTerminal. 

Thus I took some steps to make Gnome terminal the default Terminal application, and added an icon for it in my menu. These steps are described in another section of this document.


**Note:** If you're looking for info on installing plain Vim, see the end of this post.

### Installation

First, we're going to want to install git in order to use vim-plug later: `sudo apt install git`

Next, I went over to [the Ubuntu section of the Neovim installation page](https://github.com/neovim/neovim/wiki/Installing-Neovim#ubuntu)

Assuming I needed this dependency, I probably ran: `sudo apt-get install software-properties-common`

I then chose the unstable version: https://launchpad.net/%7Eneovim-ppa/+archive/ubuntu/unstable 

To add the PPA to my system, I ran 

```
sudo add-apt-repository ppa:neovim-ppa/unstable
sudo apt-get update
```

I then installed Neovim from this PPA by running `sudo apt-get install neovim`. I think the `nvim` command worked after that.


### Critical changes to Vim config file

First, since on Lubuntu I'm likely only going to use Neovim and not Vim, I renamed my vimrc to `init.vim` and put it in `~/.config/nvim/` (which I may have had to create myself). 

I then changed my [vim-plug](https://github.com/junegunn/vim-plug) call to download my plugins to `~/.config/nvim/plugged`: `call plug#begin('~/.config/nvim/plugged')`

I could have chosen to set vim-plug to download plugins to another directory somewhere in `~/.local/`, which may have kept the `~/.config` directory closer to what I assume is its intended purpose of just being configuration files, and not actual software.

Also, I had to redo this mappings that open my vim config file:

```vim
" Quickly open a vertical split of my VIMRC and source my VIMRC
nnoremap <silent> <leader>ev :vs $MYVIMRC<CR>
nnoremap <silent> <leader>sv :so $MYVIMRC<CR>
```

#### Syntax Highlighting Colors

I also made sure that `set termguicolors` was definitely being run in my `init.vim` file-- on my Mac I ran it only conditionally based on the terminal Vim detected. For now, let's just run it, as gnome-terminal is capable of running hex color vim themes.

### System Clipboard

Within Neovim I ran `:CheckHealth` which kindly informed me that to get system clipboard support, I'd need to install a program called [XSel](https://apps.ubuntu.com/cat/applications/xsel/). So back on the terminal I ran `sudo apt install xsel` and then restarted my terminal. 

Then in my `init.vim` I figured out through trial and error that I needed to use the `+` register to access the system clipboard, rather than `*` that I used on MacOS:

```vim
" use leader to interact with the system clipboard
nnoremap <Leader>p "+]p
nnoremap <Leader>P "+]P

nnoremap <Leader>y :y+<cr>
nnoremap <Leader>c ^"+c$
nnoremap <Leader>d ^"+d$

vnoremap <Leader>y "+y
vnoremap <Leader>c "+c
vnoremap <Leader>d "+d
```

Though strangely, custom mappings that use the systemclipboard register still work with the `*` rather than the `+`:

```vim
" place enter file on system clipboard
nnoremap <Leader>a :%y*<cr>

" In markdown files, Control + a surrounds highlighted text with square
" brackets, then dumps system clipboard contents into parenthesis
autocmd FileType markdown vnoremap <c-a> <Esc>`<i[<Esc>`>la](<Esc>"*]pa)<Esc>
```

### Other Things To Consider

I have Lubuntu installed on an old MacBook, whose track pad sometimes gets triggered when I'm typing. Thus in this Vim configuration I chose to disable my mouse

```vim
" disable mouse
autocmd BufEnter * set mouse=
```


### Appendix: Some Notes on Vim (not Neovim)

As of this writing, you can install Vim 7.4.X with something like `sudo apt-get vim`. To install, Vim 8 currently you need to use [a PPA](http://tipsonubuntu.com/2016/09/13/vim-8-0-released-install-ubuntu-16-04/). 

But with both versions of Vim I was having trouble getting access to the system clipboard, so I went with Neovim. Though you can have both installed, with their own configurations, pretty easily.
