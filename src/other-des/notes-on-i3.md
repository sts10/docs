## Notes on i3

Good 3-video [playlist](https://www.youtube.com/watch?v=j1I63wGcvU4&index=1&list=PL5ze0DjYv5DbCv9vNEzFmP6sU7ZmkGzcf) that shows i3 window manager from the start: https://www.youtube.com/watch?v=j1I63wGcvU4&index=1&list=PL5ze0DjYv5DbCv9vNEzFmP6sU7ZmkGzcf

### Install i3 on Ubuntu
1. Log in 
2. Open Terminal
3. `sudo apt-get install i3`; enter passowrd
4. log out
5. in menu, choose i3 to be your desktop environment
6. Press enter to generate a config file
7. Select mod key (think we want the "windows" key)


### Basic, Default Keybindings
- open a new instance of terminal (hope it's GNOME...): mod + Enter
- Close window: mod + shift + q
- app launcher: mod + d
  - change it to synapse by adding this line to the i3 cofig: `bindsym $mod+d exec synapse`
- new vertical window: just open a new window
- new horizontal window: mod + v, then open a new window
  - one question is how I get out of this mode
- move between windows in current workspace: mod + arrow keys (or mouse)
- move or swap a window within the current workspace: mod + shift + arrow keys

- log out with mod + shift + e 
- lock out: enter in terminal `i3lock`

- refresh your i3 config: mod + shift + r

#### Workspaces

"There is no maximize key in i3. What you want to do is move it to a different workspace."

- move current window to a different workspace: mod + shift + number

#### Resizing Windows

First, enter resize mode with mod + r. Red box appears. Escape to exit resize mode. 

Now can use the arrow keys to resize the current window. 


#### Stacking and Tab mode (as opposed to tiling mode)

- enter stacking mode with mod + s
- navigate the stack with mod + arrows
- return to tiling mode with mod + e 

mod + w enters "tab" mode


### Customization Basics

### Questions 

1. How do I open a file manager window?
  - just launch dmenu or synapse and open documents or file manager
2. How do I set it so KeePassXC as a floating window by default (at least initially?)
3. 
