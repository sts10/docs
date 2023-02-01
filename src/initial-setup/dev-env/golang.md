# Installing Go

As of 2023, on Linux, I prefer the method outlined on [this page](https://go.dev/doc/install)

It involves: 
1. Downloading the linux-amd64 file, e.g. go1.20.linux-amd64.tar.gz, from [go.dev](https://go.dev/dl/) to your `~/Downloads` directory.
2. `cd ~/Downloads`
3. `sudo rm -rf /usr/local/go && sudo tar -C /usr/local -xzf go1.20.linux-amd64.tar.gz`
4. Check with `go version` 

If it's your first time installing Go on the machine, you'll need to add this Go binary to your PATH by adding something like `export PATH=$PATH:/usr/local/go/bin` to your `~/.profile` or `~/.bashrc`. 
