# Installation

Currently the best way to run `outcome` deployments, whether local or distributed, is using the provided command-line tool. This will require us to [access and use the *terminal*](https://towardsdatascience.com/a-quick-guide-to-using-command-line-terminal-96815b97b955), also called the [*shell*](https://en.wikipedia.org/wiki/Shell_(computing)) of our operating system.


## Using `cargo` build tool

Since `outcome` is written in Rust programming language, we can leverage it's native [build tool `cargo`](https://doc.rust-lang.org/cargo/). `cargo`'s [`install` subcommand](https://doc.rust-lang.org/cargo/commands/cargo-install.html) can take care of downloading, building, and adding the resulting binary to our system's path so that we can easily run it from the command line.

First we will need to [install `cargo`](https://doc.rust-lang.org/cargo/getting-started/installation.html) itself. It comes bundled with a regular Rust language installation. Follow the instructions at [*rustup.rs*](https://rustup.rs/) to install Rust on your machine.

Once the installation is finished, run the following command:

```
cargo install outcome-cli
```

><br>**NOTE:** During compilation you may get an error message about missing dependencies. By default, `outcome` uses `zeromq` messaging library, or more accurately, it compiles it from c++ source. Long story short, using `outcome` with `zeromq` requires `cmake` and a c++ compiler, like `gcc`, to be installed on your system. This is not optimal, and in the future could be changed by replacing the currently used `libzmq-rs` bindings crate with native Rust implementation of the library.<br><br>

After the build process is complete, you should be able to use `outcome` from the command line like so:

```
outcome --help
```

## Using pre-compiled binaries

For major releases pre-compiled binary executables for selected operating systems may be provided. Check out the download section on the website for links to code repositories.
