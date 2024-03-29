# `cargo-dist` tips

**Sam's notes on using [cargo-dist](https://opensource.axo.dev/cargo-dist/)**

Some notes on cargo-dist v0.4.2; following [this documentation](https://opensource.axo.dev/cargo-dist/book/way-too-quickstart.html)

## Preparation

1. Make sure the `repository` variable is specified in your `Cargo.toml`. It takes the URL of your GitHub repo (`repository = "https://github.com/sts10/password-strength-checker"`). You should probably also specifiy a `license` or `license-file` (but not both), and the location of the `readme` file. (See here for more things to specify: [https://doc.rust-lang.org/cargo/reference/manifest.html](https://doc.rust-lang.org/cargo/reference/manifest.html).)
2. Install or update cargo-dist with something like `cargo install cargo-dist`
3. Run a `git push --tags` to push any and all local tags you've created up to GitHub. If any local tags are rejected for already existing on GitHub, I recommend you just delete the local tags with `git tag --delete <tag_name>`.

## Initializing cargo dist

1. In your Rust project's directory, run `cargo dist init`. This launches a lil interactive install guide. Be sure to enable the GitHub CI; and you probably want the SHELL installer, which I'm not sure is enabled by default?
2. This will create a new file at `.github/workflows/release.yml`, which tells GitHub what magic to do later, and edit your Cargo.toml. Don't worry about it.
3. Commit these changes (`git add . && git commit -m "init cargo dist"`)

A note on that nifty `cargo dist init` command from the official cargo-dist docs:
> [This command] should be run again whenever you want to change your settings or want to update cargo-dist.

> Just to really emphasize that: `cargo dist init` is designed to be rerun over and over, and will preserve your settings while handling any necessary updates and migrations. Always Be Initing.

## Getting ready to create a release (testing builds)

Let's see if your code is going to make for a non-broken release. 

First, run `cargo dist build` to try building for the platform (OS) you're currently using. cargo-dist will print the version it assume you want to release, plus paths to the files it created, so you can inspect their contents.

If that's all good, next try `cargo dist plan`. This too will print the version of the project it assumes you want to release -- check that it's right. Further info:
> The plan command should be running the exact same logic that cargo-dist's generated CI will run, but without actually building anything. This lets you quickly check what cutting a new release will produce. It will also try to catch any inconsistencies that could make the CI error out.

Note that: 
> As of cargo-dist 0.3.0, we now by default run the "plan" step of your release CI on every pull-request so that we can catch breakage to your release process as early as possible. This will work even for a pull-request that sets up cargo-dist for the first time, so you can be confident you're landing something that works.

Basically, now for every PR to your project, GitHub will run part of this `cargo dist plan` command for you before you merge, to see if building goes well. I don't really know what happens if this build process fails... hopefully it doesn't get in the way of any troubleshooting.

## Create a new release!
1. Get your main branch into a good, working place. Commit changes, at least locally.
2. Run `cargo test`, etc. as well as the tests described above (`cargo dist build` and `cargo dist plan`).
3. Increment that `version` in `Cargo.toml` to a new highest version. Let's say we're going from `v0.3.8` to `v0.3.9`.
4. Optional: Add release notes to a file called `CHANGELOG.md`, under a heading like `## Version 0.3.9`, which Cargo Dist will auto-detect.
5. Run another `cargo build` to make sure `Cargo.lock` is up-to-date.
6. Commit changes -- message can be something like "Release v0.3.9" -- and `git push origin main`
7. Create a git tag for this release. Match the version number to the one in `Cargo.toml`. So in our case: `git tag v0.3.9`. (Obviously make sure this tag has not been seen by git or GitHub before.)
8. Push your tags to GitHub: `git push --tags`

> At this point you're done! The generated CI script should pick up the ball and create a Github Release with all your builds over the next few minutes!

(FYI This is the point where you'd run `cargo publish` to push to crates.io, if your project is hosted there.)

## Upgrading cargo-dist itself

If and when you upgrade cargo-dist (using `cargo install cargo-dist`), you'll need to take some steps within the project that you use cargo-dist to distribute. 

### New way of doing this (as of cargo-dist v0.7.0)

Just run `cargo dist init`, as per [these cargo-dist docs](https://opensource.axo.dev/cargo-dist/book/updating.html).

### My old notes on how to do this

1. In your project's `Cargo.toml` file, edit the `cargo-dist-version` variable to match the version of cargo-dist you now have installed on your system.
2. Re-run `cargo dist init`. (You may also need to run `cargo dist generate` afterward for changes to take affect.)
3. Try `cargo dist built` and `cargo dist plan`, as usual, to see if everything is in working order.

## Suggested Markdown to add to README of project that uses cargo-dist

```markdown
## For developers: How to create a release

This project uses [cargo-dist](https://opensource.axo.dev/cargo-dist/) to create releases. 

Some of [my personal docs are here](https://sts10.github.io/docs/cargo-dist-tips.html); but basically, `cargo install cargo-dist`. When you're ready to cut a new release, test the current state of the project with `cargo dist build` and `cargo dist plan`. If that went well, create a new git tag that matches the current project version in `Cargo.toml` with `git tag vX.X.X`. Finally, run `git push --tags` to kick off the release process. GitHub will handle it from here -- check your project's GitHub Releases page in about 5 to 10 minutes.
```
