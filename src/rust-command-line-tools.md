# A curated list of command-line tools written in Rust

(This list is also [available on GitHub](https://gist.github.com/sts10/daadbc2f403bdffad1b6d33aff016c0a), where it'll likely be updated more regularly.)

Note that I have not tried all of these personally, and **cannot and do not vouch for all of the tools listed here**. In most cases, the descriptions here are copied directly from their code repos. Some may have been abandoned. Investigate before installing/using.

The ones I use regularly include: bat, dust, exa, fd, hyperfine, miniserve, ripgrep, just, zoxide and cargo-wipe.

- [atuin](https://github.com/ellie/atuin): "Magical shell history"
- [bandwhich](https://github.com/imsnif/bandwhich): Terminal bandwidth utilization tool 
- [bat](https://github.com/sharkdp/bat): A replacement for `cat` that provides syntax highlighting and other features. 
- [bottom](https://github.com/ClementTsang/bottom): Yet another cross-platform graphical process/system monitor. 
- [broot](https://github.com/Canop/broot): A new way to see and navigate directory trees
- [counts](https://github.com/nnethercote/counts): "A tool for ad hoc profiling"
- [choose](https://github.com/theryangeary/choose): A human-friendly and fast alternative to `cut` and (sometimes) `awk`
- [delta](https://github.com/dandavison/delta): A syntax-highlighting pager for git, `diff`, and grep output 
- [difftastic](https://github.com/Wilfred/difftastic/): A syntax-aware diff  
- [dog](https://github.com/ogham/dog): A command-line DNS client
- [dua](https://github.com/Byron/dua-cli): "View disk space usage and delete unwanted data, fast."
- [dust](https://github.com/bootandy/dust): "a more intuitive version of `du` in Rust"
- [eva](https://github.com/nerdypepper/eva): "a calculator REPL, similar to bc(1)"
- [exa](https://the.exa.website/): "A modern version of `ls`"
- [fclones](https://github.com/pkolaczk/fclones): an "efficient duplicate file finder" 
- [fd](https://github.com/sharkdp/fd): "A simple, fast and user-friendly alternative to `find`"
- [felix](https://github.com/kyoheiu/felix): tui file manager with vim-like key mapping 
- [frum](https://github.com/TaKO8Ki/frum): A modern Ruby version manager written in Rust
- [grex](https://github.com/pemistahl/grex): A command-line tool and library for generating regular expressions from user-provided test cases 
- [htmlq](https://github.com/mgdm/htmlq): Like jq, but for HTML. Uses CSS selectors to extract bits of content from HTML files.
- [hyperfine](https://github.com/sharkdp/hyperfine): Command-line benchmarking tool
- [inlyne](https://github.com/trimental/inlyne): "GPU powered yet browsless tool to help you quickly view markdown files"
- [jql](https://github.com/yamafaktory/jql): A JSON query language CLI tool
- [just](https://github.com/casey/just): Just a command runner (seems like an alternative to `make`)
- [lemmeknow](https://github.com/swanandx/lemmeknow): Identify mysterious text or analyze hard-coded strings from captured network packets, malwares, and more.
- [lfs](https://github.com/Canop/lfs): A Linux utility to get information on filesystems; like `df` but better 
- [lsd](https://github.com/Peltoche/lsd): The next generation `ls` command (though personally I prefer `exa`)
- [macchina](https://github.com/macchina-cli/macchina): Fast, minimal and customizable system information frontend.
- [mdBook](https://github.com/rust-lang/mdBook): Create books from markdown files. Like Gitbook but implemented in Rust 
- [mdcat](https://github.com/lunaryorn/mdcat): Fancy `cat` for Markdown
- [miniserve](https://github.com/svenstaro/miniserve) is "a CLI tool to serve files and dirs over HTTP". I use this as a replacement for `python -m SimpleHTTPServer`, or whatever the latest version of that command is.
- [monolith](https://github.com/y2z/monolith): Save complete web pages as a single HTML file 
- [ouch](https://github.com/ouch-org/ouch): "Painless compression and decompression for your terminal"
- [pastel](https://github.com/sharkdp/pastel): A command-line tool to generate, analyze, convert and manipulate colors.
- [procs](https://github.com/dalance/procs): A modern replacement for `ps` written in Rust
- [qsv](https://github.com/jqnatividad/qsv): CSVs sliced, diced & analyzed. (A fork of `xsv`)
- [rip](https://github.com/nivekuil/rip): A safe and ergonomic alternative to `rm`
- [ripgrep](https://github.com/BurntSushi/ripgrep): A faster replacement for GNU’s `grep` command. This tool is very good.
- [ripsecrets](https://github.com/sirwart/ripsecrets): Find secret keys in your code before commiting them to git. I've contributed to this one!
- [sd](https://github.com/chmln/sd): Intuitive find & replace CLI (`sed` alternative).
- [tealdear](https://github.com/dbrgn/tealdeer): A very fast implementation of `tldr` in Rust. 
- [tin-summer](https://github.com/vmchale/tin-summer): Find build artifacts that are taking up disk space 
- [tokei](https://github.com/XAMPPRocky/tokei): Count your (lines of) code, quickly
- [topgrade](https://github.com/topgrade-rs/topgrade): Upgrade all of your tools
- [watchexec](https://github.com/watchexec/watchexec): Execute commands in response to file modifications. (Note: See [cargo watch](https://github.com/watchexec/cargo-watch) if you want to watch a Rust project.)
- [xcp](https://github.com/tarka/xcp): An extended `cp` 
- [xh](https://github.com/ducaale/xh): "Friendly and fast tool for sending HTTP requests" 
- [xsv](https://github.com/BurntSushi/xsv): A fast CSV command line toolkit written in Rust. (Last updated in 2018)
- [zoxide](https://github.com/ajeetdsouza/zoxide): A smarter `cd` command.

## Tools to help working with Rust lang itself
- [cargo-audit](https://github.com/RustSec/rustsec/tree/main/cargo-audit): Audit Cargo.lock files for crates with security vulnerabilities reported to the RustSec Advisory Database.
- [cargo-geiger](https://github.com/rust-secure-code/cargo-geiger): Detects usage of unsafe Rust in a Rust crate and its dependencies. 
- [cargo-wipe](https://github.com/mihai-dinculescu/cargo-wipe): Cargo subcommand that recursively finds and optionally wipes all "target" or "node_modules" folders that are found in the current path. 
- [cargo-crev](https://github.com/crev-dev/cargo-crev): A cryptographically verifiable code review system for the cargo (Rust) package manager.
- [bacon](https://github.com/Canop/bacon): A background Rust code checker
- [cargo watch](https://github.com/watchexec/cargo-watch): Watches over your Cargo project's source. 
- [cargo-binstall](https://github.com/cargo-bins/cargo-binstall): "Binary installation for [R]ust projects"

## Terminal emulators / terminal-related
- [Alacritty](https://github.com/alacritty/alacritty): A cross-platform, OpenGL terminal emulator. 
- [Wezterm](https://github.com/wez/wezterm): A GPU-accelerated cross-platform terminal emulator and multiplexer written by @wez and implemented in Rust 
- [Starship](https://starship.rs/): Customizable prompt for any shell.
- [Zellij](https://github.com/zellij-org/zellij): A terminal workspace with batteries included.

## Text editors written in Rust
- [amp](https://github.com/jmacdonald/amp)
- [helix](https://github.com/helix-editor/helix)
- [kibi](https://github.com/ilai-deutel/kibi): "A text editor in ≤1024 lines of code, written in Rust"
- [lapce](https://github.com/lapce/lapce)
- [pepper](https://github.com/vamolessa/pepper)
- [xi](https://github.com/xi-editor/xi-editor)
- [zee](https://github.com/zee-editor/zee)

See [this "Battle of the [Rust] text editors" post from 2022](https://matduggan.com/battle-of-the-text-editors/).

## Other lists of Rust command line utilities

- [lib.rs's list](https://lib.rs/command-line-utilities)
- ["Awesome Rust"](https://github.com/rust-unofficial/awesome-rust)
- [Awesome Alternatives in Rust](https://github.com/TaKO8Ki/awesome-alternatives-in-rust)

## Tips

### `exa` aliases I use in my `~/.bashrc`

```bash
if hash exa 2>/dev/null; then
    alias ls='exa'
    alias l='exa -l --all --group-directories-first --git'
    alias ll='exa -l --all --all --group-directories-first --git'
    alias lt='exa -T --git-ignore --level=2 --group-directories-first'
    alias llt='exa -lT --git-ignore --level=2 --group-directories-first'
    alias lT='exa -T --git-ignore --level=4 --group-directories-first'
else
    alias l='ls -lah'
    alias ll='ls -alF'
    alias la='ls -A'
fi
```

## Shameless plug: Tools that I've written in Rust

- [Tidy](https://github.com/sts10/tidy): A command-line tool for combining and cleaning large word list files.

## Know a good one that I don't have listed here?

Let me know in the comments, a PR, on [Mastodon](https://hachyderm.io/@schlink) or [Twitter](https://twitter.com/sts10/).
