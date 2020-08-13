# Go

[Go](https://en.wikipedia.org/wiki/Go_(game)) is a ~2,500-year-old abstract strategy board game that you might play or want to play. I got into it after watching the AlphaGo documentary ([currently on Netflix](https://www.netflix.com/title/80190844)).

If you just want to play Go on your desktop, an easy way to do it is in your browser through an online server like [OGS](https://online-go.com/). On iOS I like [SmartGo](https://apps.apple.com/us/app/smartgo-player/id314506629). See more Go resources at the bottom of this page. But the bulk of this page is dedicated to playing Go through a desktop app called Sabaki.

## Sabaki, a desktop Go app for Linux

A good desktop app that works for Linux is [Sabaki](https://sabaki.yichuanshen.de/) ([GitHub repo](https://github.com/SabakiHQ/Sabaki)). To install it, I went with the x64 AppImage, probably from [the GitHub Releases tab](https://github.com/SabakiHQ/Sabaki/releases)).

In Sabaki you can play against yourself or load and go through SGF files. But you can also "attach" [a number of "game engines"](https://github.com/SabakiHQ/Sabaki/blob/master/docs/guides/engines.md) to Sabaki to either play against or have analyze games. You can manage the engines available to Sabaki by going to "Engines" > "Manage Engines". 

## Setting up the GNU Go engine

[GNU Go](https://www.gnu.org/software/gnugo/gnugo.html) is an engine that's nice in that it can (a) play on multiple board sizes out of the box, and (b) has multiple levels to choose from (1 through 10 or 1 through 9, I'm not sure).

### Installing GNU Go on Ubuntu

Go to the [Download page](https://www.gnu.org/software/gnugo/download.html) and download the source code to the latest version of GNU Go. It's likely to be a `tar.gz` file. Once downloaded, expand it. 

Inside that directory, there should be a README and an INSTALL documentation text file for you. But basically, to make the executable for a specific level, I'm pretty sure you run:

```
./configure --enable-level=4; make
```

To build a level 4 binary. (There are plenty of other options explained in one of the documentation text files.) This binary will be created and placed at `./interface/gnugo`. Cool. 

Now in Sabaki, go to Engines > Manage Engines and click the "Add" button. For path, enter `path/to/interface/gnugo`, and then for "arguments" I'm pretty sure you want to put `--mode gtp`. Leave "Initial commands" blank. Note that after Adding an engine, you may need to restart Sabaki to use it.

To build/attach **multiple levels** of GNU Go, I just duplicated the entire `gnudo` directory and rebuilt with the level I want. So in `go-engines` I've got:

```txt
go-engines/gnugo-3.8-lvl1
go-engines/gnugo-3.8-lvl2
go-engines/gnugo-3.8-lvl3
go-engines/gnugo-3.8-lvl5
go-engines/gnugo-3.8-lvl7
go-engines/gnugo-3.8-lvl9
```

each of which have their own executables at `interface/gnugo` to attach in Sabaki. For example, my engine named "GNUGo_lvl_3" has a path of `go-engines/gnugo-3.8-lvl3/interface/gnugo` ("arguments" for all of them are (still) `--mode gtp`).

## Pachi

[Pachi](https://github.com/pasky/pachi) is a pretty strong engine, but that, unlike LeelaZero, can play smaller board sizes out-of-the-box, so to speak. The developers note:

> The default engine plays by Chinese rules and should be about 7d KGS strength on 9x9. On 19x19 it can hold a solid KGS 2d rank on modest hardware (Raspberry Pi, dcnn) or faster machine (e.g. six-way Intel i7) without dcnn.

### Install Pachi via pre-compiled binary
To install Pachi via pre-compiled binary, head over to [GitHub Releases page](https://github.com/pasky/pachi/releases) and download the latest `-linux-static.zip`. Extract this. 

### Connecting Pachi to Sabaki

I didn't change any configurations. 

Then in Sabaki, I just entered the path to the `pachi-12.40-amd64` file in the unzipped directory, with no arguments or initial commands, and it seems to work. However, as I installed it, it can only do analysis on 19x19 boards I think?

### Compiling Pachi from Source

I haven't tried this, but the Pachi README says it might improve performance to build it from source. [Instructions here](https://launchpad.net/~lemonsqueeze/+archive/ubuntu/pachi).

## Setting up LeelaZero (Ubuntu)

1. Download and install [Sabaki](https://github.com/SabakiHQ/Sabaki/). Make sure it runs before proceeding.
2. [Build LeelaZero from source](https://github.com/leela-zero/leela-zero#example-of-compiling---ubuntu--similar)
3. Get a "network hash file" for LeelaZero, "likely the best network is the one you want". [Download it here](http://zero.sjeng.org/best-network) or find [more instructions here](https://github.com/SabakiHQ/Sabaki/blob/master/docs/guides/engines.md).
4. In Sabaki, go to Engines > Manage Engines. Enter the absolute file path to the `leelaz` binary file you just built, which is probably at something like `leela-zero/build/leelaz`. For "Arguments", enter `--gtp -w path/to/weightsfile` (which I think is the "network hash file"?)
5. Restart Sabaki 
6. Find the Game Info menu item. For White, in the drop-down menu, select Leela Zero. Make sure you choose a 19 by 19 board. And you're probably going to want a large handicap.

## KataGo

[KataGo](https://github.com/lightvector/KataGo) is another new engine. I think I like it best of these options since it works on smaller board sizes and, apparently, it works well with handicaps.

To run it on Linux (or Windows), I think you want to download the appropriate binary from [the GitHub release page](https://github.com/lightvector/KataGo/releases). On my System76 Oryx Pro, I apparently prefer the `katago-v1.X.X-opencl-linux-x64.zip` version. And you also need one of the "block network" files, which I think are called "models". These files end in `bin.gz` or `txt.gz`. I think I've chosen the "40 block network" before, though I don't fully understand what that number means. 

Next, you may want to have the binary create a config file tuned to your computer. From [the README's "How to Use" section](https://github.com/lightvector/KataGo#how-to-use):

"To automatically tune threads and other settings for you based on asking simple questions, and generate a GTP config for you: `./katago genconfig -model <NEURALNET>.gz -output <PATH_TO_SAVE_GTP_CONFIG>.cfg`"

Answer the questions as you like. It'll create a fresh text config file that we'll point Sabaki to (see below).

At some point, you'll want to run something like `chmod a+x ./katago`.

### Settings for KataGo for Sabaki

```
/home/sschlinkert/code/go-engines/katago-v1.3.5-opencl-linux-x64/katago
gtp -model '/home/sschlinkert/code/go-engines/katago-v1.3.5-opencl-linux-x64/g170-b30c320x2-s2846858752-d829865719.bin.gz' -config '/home/sschlinkert/code/go-engines/katago-v1.3.5-opencl-linux-x64/my_oryx_pro_config.cfg'
```
and no "initial commands" 

Note that you may need to run `chmod a+x` on the executable before it'll work.


## How to play against a game engine in Sabaki

To play against one of these engines, open Sabaki. Be sure you're on a blank, new game. Then go to "File" > "Game Info". If you want Balck, make the engine take Whtie by clicking the down arrow next to "White" and selecting the engine you want to play. Fill out the other fields as desired, then hit the OK button. If you're Black, place a stone to start the game, and the engine should respond. To see what the engine is doing, go to "Engines" > "Toggle GTP console".

Alternatively you can manually attach an engine by going to Engines > "Attach". 

## Recommended Sabaki preferences

To prevent engines from making moves _right_ when you initially attach them (which can be annoying if you just want to use the engine to analyze possible moves [see below]), I would go to File > Preferences and uncheck "Start game right after attaching engines". The con to this is that to start playing a game against an engine, you have to first attach it ("Engines" > "Attach"), then (sometimes) tell it to start playing ("Engines" > "Start Playing").

## Using a game engine to do analysis of a game in Sabaki

Some of these engines  -- like LeelaZero and Pachi -- allow you to analyze next moves (though usually only on 19x19 games it seems?). To do this:

1. "Engines" > "Toggle Analysis" gives you a heat map of what the engine likes for the next move. Leela will do both show the analysis of its moves _as well as_ provide analysis for your move (you can accept by clicking on the green blob, or move somewhere else)
2. With "Analysis" toggled on, you can also hover a piece over a space and the engine will play out the game from there, if you were to move there.

If the GPU load gets to be too much, you can always make the engine suspend by going to "Engines" > "Suspend". Toggling Analysis off will help too, as the engine won't think during your move.


## Appendix: Go resources

If you're here and want to learn more about Go, I've pasted some of my notes on general Go resources below.

### Learning the rules

To learn how to play Go, I'd recommend watching YouTube videos (links below), but obviously there are other ways.

- YouTube videos I liked: ["How to Play Go" YouTube series](https://www.youtube.com/watch?v=Vov_keBQOJ8&list=PL5mVjO5OFYSzIlp0aTDsE_1Xsx16AaUej). Here's [another one I watched](https://www.youtube.com/watch?v=xMshtO8h7RU), and [one from the New York Institute of Go](https://www.youtube.com/watch?v=eNpJF0BzUig). 
- The [r/baduk subreddit](https://www.reddit.com/r/baduk) ("Baduk" is what they call the game in Korean, and has much better search-ability online) has [a pinned post full of links for newcomers](https://www.reddit.com/r/baduk/comments/4c8xs5/learning_links_for_newcomers_after_alphago/), including to YouTube resources.
- There's also [this interactive tutorial](http://playgo.to/iwtg/en/), though I had to fiddle with my browser settings a bit to make it work. 
- Here's [a non-interactive slideshow of sorts](http://www.learngo.co.uk/GoTutor/Tutor.php) that looks good.

### Actually playing games

- On desktop web: I like [online-go.com](https://online-go.com/) for actually playing Go games online. You can play both other humans and a variety of bots with different skill levels. 
  - If you don't want to be bothered to create an account, there's [this site](https://www.cosumi.net/en/), though it doesn't offer handicaps on smaller boards like 9 by 9, so you're probably going to lose way more than half the time.
- On iOS: As mentioned, I've found [this $2.99 app called SmartGo](https://apps.apple.com/us/app/smartgo-player/id314506629) nice for beginners like me. If you ask, it'll estimate the score for you and even suggest a move for you. If that's not challenging enough, [A Master of Go](https://new3rs.github.io/a_master_of_go/index.html) is an expensive iOS app that features high-end AI software.
- On your desktop, you can install Sabaki and a number of Go engines to play against.
- There are more software options listed [here](https://www.reddit.com/r/cbaduk/comments/c0o8f1/go_software/).

### Exercises

If you're don't want to play full games, you can find apps and websites that provide small exercises or puzzles to play through. 

- The iOS app SmartGo that I've mentioned above has a tutorial of live exercises somewhere in the menus.
- online-go.com has [a "playlist" of puzzles for beginners](https://online-go.com/puzzle/2625), though I found them a bit too difficult?

### More English-language YouTube channels

- [dwyrin](https://www.youtube.com/channel/UCCYMY6j5mUvPMPzvN5bxuKA)
- [Nick Sibicky](https://www.youtube.com/channel/UC_msctwlIh2cwM8yAtaju1A)
- [Go Pro Yeonwoo](https://www.youtube.com/user/goingceo/videos)
- [American Go Association](https://www.youtube.com/user/USGOWeb/videos)
- [New York Institute of Go](https://www.youtube.com/user/goingceo/videos)

### Books

I'm not sure if you _need_ a book or books to learn, but obviously there are plenty out there. In my cursory search of posts on r/baduk, I found and bought three popular options for beginners. I've read at least half of them, and I'd recommend reading them in this order:

1. [_Learn to Play Go_ by Janice Kim](https://www.amazon.com/gp/product/1453632891/ref=ox_sc_act_title_3?smid=ATVPDKIKX0DER&psc=1) would probably work for brand new players.
2. [_Go for Beginners_ by Kaoru Iwamoto](https://www.amazon.com/gp/product/0394733312/ref=ox_sc_act_title_2?smid=ATVPDKIKX0DER&psc=1) seems like a classic intro text.
3. [_Lessons in the Fundamentals of Go_ by Toshiro Kageyama](https://www.amazon.com/gp/product/4906574289/ref=ppx_yo_dt_b_asin_title_o03_s00?ie=UTF8&psc=1) is still a bit advanced for me.
