# Schlink's Docs

Welcome! This is an [mdbook](https://github.com/rust-lang-nursery/mdBook) full on notes that Sam Schlinkert has written about installing and running a Linux desktop. It's mostly for personal reference, but you may find it useful. It mostly pertains to Ubuntu-based systems. 

## My Config Files

Most of my Linux config files (as opposed to guides, which is what this site is mostly made up of) live in [this GitHub repo](https://github.com/sts10/linux-config). (Separately, I keep [an Alacritty config file as a Gist](https://gist.github.com/sts10/df620672662fe4c6f03ac296a02b8e72).)

## How this book is set up

This is an [mdbook](https://github.com/rust-lang-nursery/mdBook). The book's source files live in [this GitHub repo](https://github.com/sts10/linux-notes-mdbook) -- if you wish to **contribute** to this book, please create an issue or pull request there!

The GitHub repo of my Jekyll website/blog, which is one place where this book is published, is [here](https://github.com/sts10/sts10.github.io).

### Publishing the mdbook to the GitHub Page: 

The `book.toml` file in [the mdbook source repo](https://github.com/sts10/linux-notes-mdbook) specifies that the mdbook builds to `../sts10.github.io/docs` (via the `mbdook build` command). So when you set this up you need those two directories in the same parent directory.

Once set up, you can run a publish: 

1. In the mdbook source repo, run `mdbook build`
2. In the `sts10.github.io` Jekyll site repo, add and commit the Git changes and run `git push origin master`

## Contact the Author

You can find Sam on [Twitter](https://twitter.com/sts10) or [Mastodon](https://octodon.social/@schlink) or [contact him via more secure channels](https://gist.github.com/sts10/4a4e01021b3a5ad42e9b73e0abd7b7e3).

