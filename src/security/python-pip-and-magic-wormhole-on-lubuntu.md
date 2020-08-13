## Installing Pip and Magic Wormhole on Lubuntu 16.04

### Python
Python 2 and Python 3 come with Ubuntu/Lubuntu. `python` calls v 2.7.12 and `python3` calls 3.5.2. 

### Installing pip
I think you can install regular pip by running: `sudo apt install python-pip` and then upgrading it with `pip install --upgrade pip`. I'm not sure whether, after doing this, pip is tied to python 2 or 3. My guess is v 2, which is fine.

### Installing Magic Wormhole
To install [magic-wormhole](https://github.com/warner/magic-wormhole#installation), a CLI to "get things from one computer to another, safely", I needed to install some other stuff. They suggest installing all at once with `apt-get install python-pip build-essential python-dev libffi-dev libssl-dev`. I likely could have run that command without `python-pip`.

I was then able to install magic-wormhole with `sudo pip install magic-wormhole`.
