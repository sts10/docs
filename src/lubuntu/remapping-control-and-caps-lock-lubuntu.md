## Swapping control and caps lock on Lubuntu 16.04

First I ran `setxkbmap -option ctrl:swapcaps` in gnome-terminal, and observed that the keys were switched on my Macbook keyboard. 

Now, following an answer on the web whose URL I've lost, I added that line of text to `~/.config/lxsession/Lubuntu/autostart`.

Note that the `setxkbmap` line the worked in Ubuntu 16.04, `setxkbmap -option caps:ctrl_modifier`, did not work immediately when run in terminal in Lubuntu.
