# Using `endgame`

<!-- > <br>endgame 0.1.3<br><br> -->

*endgame 0.1.3*

`endgame` is one of the tools in development right now. It's a [command-line interface (cli)](https://en.wikipedia.org/wiki/Command-line_interface) tool, meaning it involves interacting with the command-line interface (shell) provided by your operating system.

>If you're not sure how to access the shell on your operating system consult an appropriate tutorial for that.

## Running the program

You can either download and run a pre-compiled binary or compile the program yourself.

### Downloading binary

Probably the easiest way to run `endgame` is to download a binary suitable for your system and run it. You'll find [compiled binaries attached to the bigger releases](https://github.com/adamsky/endgame/releases). Note that the binaries may not be available for every release, also not all architectures/operating systems are covered.

To run the program you will need to navigate to the directory where you saved the binary from the command line. Then type in the name of the program to run it.

>If you don't know how to run a binary file from the command line please consult the nearest web search.

### Compiling yourself

You can also compile `endgame` yourself.

To do this you will need to install the Rust programming language on your machine. Installing Rust is easy, simply follow the instructions on [rustup.rs](https://rustup.rs). Installing `git` is also a good idea, but is not required.

Clone the repository with `git`
```
git clone https://github.com/adamsky/endgame
```
Alternatively just download the repository as zip archive and unpack it.

From the command line, change the directory to wherever you cloned/unpacked the repository. Then run
```
cargo run --release
```
Cargo is the package manager for Rust programming language. It takes care of downloading all dependencies, building everything, and finally running the program. The `--release` flag turns on optimizations and makes our program faster in the end, but it makes the build process itself longer.

In this guide we'll be passing arguments to the `endgame` program. You can pass those arguments right from the `cargo run` command.
```
cargo run --release -- --help
```
Anything after the `--` will be passed to our program.

## Available functionality

Running `endgame` you should be greeted with something similar to the following:
```
endgame 0.1.2
Adam Adamsky <adamadamsky@protonmail.com>
Endgame is a command line toolkit for creating,
running and analyzing outcome simulations.

It's is part of the effort to create an accessible
playground for world modeling and simulation.
For more info check out https://theoutcomeproject.com

USAGE:
    endgame [FLAGS] <SUBCOMMAND>

FLAGS:
    -d               Print debug information verbosely
    -h, --help       Prints help information
    -V, --version    Prints version information

SUBCOMMANDS:
    init      Initialize new content data structure
    lint      Check content for errors
    test      Test content configuration for memory requirements, average processing speed, etc.
    run       Run simulation
    server    Run endgame in server mode.
    client    Run endgame in client mode.
    coord     Run a cluster coordinator.
    worker    Run a cluster worker.
    gen       Generate optimized binary.
    help      Prints this message or the help of the given subcommand(s)
```

Descriptions for each subcommand tell us what it is they do. For additional information we can run any of the subcommands with an added `--help` flag to learn more.

For this guide we will not be looking into all of the subcommands. We will focus specifically on `run`.

><br>**NOTE:** `endgame` is currently in an early version, a lot of the features are not yet useful or are simply placeholders.
The functionality and it's specific layout (API) is likely to change over the course of development.<br><br>


## Interactive runner

Most interesting feature available to us in the current version is the interactive simulation runner under the `run` subcommand.

```
./endgame run <path-to-scenario>
```
`--interactive` option is by default set to `true`, so this will start an interactive session.

Let's run the scenario we made in the [guide called "first scenario"](./first-scenario.md).


You should be greeted with a few lines looking similar to this:
```
Running interactive session using scenario at: ".../endgame/test_scenario"
[INFO] generating sim instance from scenario at: .../endgame/test_scenario/
[INFO] there are 1 mods listed in the scenario manifest
[INFO] mod found: "test_module" version: "0.1.0" (version specifier in scenario manifest: "^0.1.0")
[INFO] found all mods listed in the scenario manifest (1)
[INFO] successfully created sim_instance
You're now in interactive mode.
See possible commands with "help". Exit using "quit" or ctrl-d.

Config file interactive.yaml doesn't exist, loading default config settings
[1]
```

The interactive mode enables you to interact with the simulation as it's being run. There are
a few different commands that enable you to do a bunch of different things. Run `help` to see
all available commands. You can use TAB key to navigate through the commands more easily too
(autocomplete). Try just typing "h" and then press TAB twice, it should show you possible
commands beginning with "h".

Simply pressing enter with no input ("empty command") progresses the simulation by one turn.
A turn is a number of base simulation ticks.

### `cfg` and `show`

You can set the number of ticks per turn using
the configuration (cfg) variable `ticks_per_turn`. By default it's set to 1. Let's
change this and make one turn do 24 ticks:
```
cfg ticks_per_turn 24
```
Preview the list of currently set cfg variables with:
```
cfg-list
```

```
ticks_per_turn          24
show_on                 true
show_list               []
```
Now when we process one turn the prompt should change by 24 at a time.

`show` command shows takes data from the simulation and shows it to us.
It uses the `show_list` cfg variable as input - it's a list of addresses that can
be used to pull data from the simulation. Let's add an address to the `show_list`.
```
show-add /region/greenland/property/bear_population/int/count
```
Now when you use the `show` command it should print out the value from the address.

Of course the address has to point to a variable that exists in the simulation.

`show_on` config variable defines whether on each turn `show` should be invoked.
We can easily toggle this with `show-toggle`.

You can export the current configuration to file with
```
cfg-save
```
Adding and modifying the variables from the command line can be tiresome,
you can edit the cfg file itself (`interactive.yaml`) and then just use
```
cfg-reload
```
to load it into the currently running interactive session. Every time
an interactive session is started it will look for this file in the
current working directory and automatically load it if it exists.

### `run` and `run-until`

`run` command takes in a number of base hour ticks and
executes exactly that number. `run-until` takes in an integer and will
run the simulation until the simulation clock count is equal to that number.
You can use `CTRL-D` (EOF) or `CTRL-C` to break out
of `run` and `run-until`. There are also `runf` and `runf-until` which are faster
but don't really allow for breaking out of the execution
(because they're not taking any time to listen for signals while running).
