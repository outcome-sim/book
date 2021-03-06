# Installation

Currently the best way to run `outcome` simulations, whether local or distributed, is using the provided command-line tool. This will require you to [access and use the *terminal*](https://towardsdatascience.com/a-quick-guide-to-using-command-line-terminal-96815b97b955), also called the [*shell*](https://en.wikipedia.org/wiki/Shell_(computing)) of your operating system.


## Use pre-compiled executable

For major releases pre-compiled binary executables for selected operating systems are provided. Check out the download section on the website for links to code repositories.

Download the file that matches your machine and run it from the command line. 


## Build it yourself

If there is no binary provided for your target system, or you just want to try out latest changes in-between releases, you can building the executable yourself. It's quite painless actually.

Since `outcome` is written in Rust programming language, you can leverage it's native [build tool `cargo`](https://doc.rust-lang.org/cargo/). `cargo`'s [`install` subcommand](https://doc.rust-lang.org/cargo/commands/cargo-install.html) can take care of downloading, building, and adding the resulting binary to your system's path so that you can easily run it from the command line.

First you will need to [install `cargo`](https://doc.rust-lang.org/cargo/getting-started/installation.html) itself. It comes bundled with a regular Rust language installation. Follow the instructions at [*rustup.rs*](https://rustup.rs/) to install Rust on your machine.

Once the installation is finished, run the following command:

```
cargo install outcome-cli
```

Cargo will attempt to download and build everything for you. Building process may take a while, depending on your machine.


## Version check

If everything goes well, you should be able to use `outcome` from the command line like so:

```
outcome
```

That's assuming you went the *build it yourself* route. If you downloaded a pre-made executable, you should be able to run it by specifying path to the downloaded file, like so:

```
./Downloads/outcome.exe
```

Running the program without any additional arguments you should see the default *help information* displayed. This includes the version number and list of available subcommands, among other things.

><br>**NOTE:** Whenever in doubt when using the application or any of it's subcommands, try passing it the `--help` argument.<br><br>