## Installing rbenv on Lubuntu 16.04

We're attempting to install [rbenv](https://github.com/rbenv/rbenv) via the ["Basic GitHub Checkout" method](https://github.com/rbenv/rbenv#basic-github-checkout).

I think we're also going to want [ruby-build](https://github.com/rbenv/ruby-build#readme) plugin. I DON'T think I'm going to want [rbenv-gemset](https://github.com/jf/rbenv-gemset)?

### Installing rbenv

As mentioned above, we're going to install rbenv via the ["Basic GitHub Checkout" method](https://github.com/rbenv/rbenv#basic-github-checkout). I reproduce them below, but you should consult the latest instructions for Ubuntu on that GitHub page.

Clone down rbenv:
```
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
```

Make it more efficient:
```
cd ~/.rbenv && src/configure && make -C src
```

Add rbenv to your PATH:
```
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
```

And finally run this init script:
```
~/.rbenv/bin/rbenv init
```

Following instructions from the init script run, I added `eval "$(rbenv init -)"` to my `~/.bashrc`, just _below_ the `export PATH="$HOME/.rbenv/bin:$PATH"` line that we added with the echo command above.

Now restart your terminal and/or run `source ~/.bashrc`.

Check your rbenv installation by running `type rbenv`. It should say it's a function. 

### Installing the ruby-build plugin

Wanting to build the latest version of Ruby a nice and clean way, I installed [ruby-build](https://github.com/rbenv/ruby-build#readme) by running `git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build`

### Installing a version of Ruby using rbenv (some problems)

Now we can install some versions of Ruby using rbenv.

`rbenv install --list` gives us all available versions to install. 

I'm going with 2.3.3, so I ran `rbenv install 2.3.3`. It took a long time to install and then told my the build failed. It suggested running `apt-get install -y libreadline-dev` so I did that (prefaced with `sudo`) and that software seemed to install successfully. 

On second attempt I ran `rbenv install --verbose 2.3.3` so that I could better see what's going on (turns out, it's a lot!). Success this time!

Once that's all installed, I opened a new gnome-terminal window. I was greeted by this shitty message at the top of the terminal window: 

> The program 'rbenv' is currently not installed. You can install it by typing: `sudo apt install rbenv`

but I learned that this can be temporarily solved be running `source ~/.profile`. And that it will be solved permanently once you restart Ubuntu/Lubuntu (source: [this GitHub issue](https://github.com/rbenv/rbenv/issues/424)).

Then I had to set Ruby v. 2.3.3 as my global version of Ruby, which I did with `rbenv global 2.3.3`. After that, `ruby --version` gave me the familiar: `ruby 2.3.3p222 (2016-11-21 revision 56859) [x86_64-linux]`


### Installing gems with rbenv

I definitely want to install the "bundler" gem. To do this, I ran: `gem install bundler`, just like with RVM. 

From there things seem to be just fine. Installed gems just work so far. 



