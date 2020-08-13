# bashrc and Terminal

Here are some tips on setting up your bash environment and your terminal. Most of the config files live in [this GitHub repo](https://github.com/sts10/linux-config), for now. Below are some instruction on how to load them correctly and easily.

## bashrc

Here's a one-line bash command to copy down my Linux `.bashrc` from GitHub:

```bash
curl -o ~/.bashrc https://raw.githubusercontent.com/sts10/linux-config/master/bash/bashrc
```

## Konsole color profile

If you're using KDE, the default terminal emulator, [Konsole](https://konsole.kde.org/), is pretty good. To get my colors -- based on my [Pink Moon Vim colorscheme](https://github.com/sts10/vim-pink-moon) -- and profile, run the following two lines:

```bash
curl --create-dirs -o ~/.local/share/konsole/Pink\ Moon.colorscheme https://raw.githubusercontent.com/sts10/linux-config/master/plasma/konsole/Pink\ Moon.colorscheme
```

```bash
curl --create-dirs -o ~/.local/share/konsole/pink-moon.profile https://raw.githubusercontent.com/sts10/linux-config/master/plasma/konsole/pink-moon.profile
```

## Alacritty terminal emulator config file 

[Alacritty](https://github.com/jwilm/alacritty/) is a cross-platform terminal emulator written in Rust, so it's really fast.

My Alacritty config file -- complete with colors -- is tested on MacOS, not Ubuntu, but if you want to try it: Place the following yaml file at `~/.config/alacritty/alacritty.yml`: [Alacritty config]( https://gist.github.com/sts10/df620672662fe4c6f03ac296a02b8e72). To do this, try running:

```bash
curl --create-dirs -o ~/.config/alacritty/alacritty.yml https://gist.githubusercontent.com/sts10/df620672662fe4c6f03ac296a02b8e72/raw/e219e9433b108bb8345f1aaa114b3f716b6df1e3/alacritty.yml
```


