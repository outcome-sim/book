# endgame toolkit

endgame is a command-line application designed as a toolkit for running and analyzing outcome simulations.

It's based on the Rust lang implementation [outcome-sim](outcome-sim.md).

[Link to `endgame` repository on github](https://github.com/artrist/endgame)

## Installation

endgame binaries are available for download on the project website. 

You can also build it yourself, just follow the instructions in the repo readme. It's pretty easy, `cargo` (the package/dependency manager for Rust lang) takes care of most of the work for you.

## Features

endgame introduces a good number of features and tools for working with outcome simulations in creative ways.

### Run Simulations

Run simulations. Fast.

Basic simulation running can't take any data in once it's started. That's why it can go as fast as the hardware will allow - no input delays.

### Server mode

Run *endgame* in *server mode* and interact with it using JSON API over http. Basically - send commands and data over the network.

This can be used to develop other applications on top of *outcome* simulations.

### Run proofs on one or more machines

Running proofs basically means running multiple simulations one after another. We can use *endgame* to run whole proofs for us.

If extra processing power is needed we can run *endgame* on multiple machines and make them collaboratively run single proof simulations together.
