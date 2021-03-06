# Project Overview

This project is not monolithic. It's composed of a number of smaller efforts aimed at different subgoals. This includes not only core software, but also tech demos, documentation, community building and outreach.


## Simulation engine

This is where the magic happens. [`outcome` repository](https://github.com/outcome-sim/outcome) consists of the core library, default networking library and the command line application.


### Core library

At the core of it all lies **outcome-core**, the *core engine library*. It defines all the basic functionality related to creating and running simulations, exposing a simple interface to the programmer.

If you were to look into the code you would find that `outcome-core` package itself doesn't actually implement any concrete networking functionality. What is does is it provides a set of abstractions, like *nodes*, *connections* and *signals*, which it uses internally to sketch out processing routines in a distributed setting without using any specific networking solution. Implementing different network transports and topologies 
on top of `outcome-core` is therefore fairly easy and doesn't involve hacking on the core library itself.

### Net library

`outcome-net` implements functionality for coordinating large simulation runs over multiple machine nodes. It builds on abstractions provided by `outcome-core` and implements them using concrete transports.

As ease of use is high on the priority list, interoperability between different applications written in different programming languages and different environments is one of the features provided by `outcome-net`. For example one client connecting to a server can be a JavaScript application using `zmq` messaging library with `msgpack` encoding, while another can be a Rust program connecting over udp and encoding messages with Rust's native encoding library.

`outcome-net` creates it's own notions of *servers*, *clients*, *workers* and more, enabling network processing patterns. It builds on the generic concepts provided by `outcome-core` and gives them substance, using concrete network transports and encoding libraries. 


### CLI tool

`outcome-cli` is the main user-facing application for the project. It aims to provide a complete suite of tools for creating, running, inspecting, analyzing and interacting with `outcome` simulations.


## Tech demos

While larger technology demonstrations have not been built yet, a few smaller demos are available:
- [outcome-bevy](https://github.com/outcome-sim/outcome-bevy)
- [outcome-unity-demo](https://github.com/outcome-sim/outcome-unity-demo)


## Inspector tools

Command line application `outcome-cli` provides an interactive way for inspecting simulations as they are being run.

Generic GUI inspector using `imgui` is planned.


## Documentation

Documentation effort takes place on two fronts. First is crate documentation for the code libraries and applications. Second is a more beginner-friendly material in the form of [this book](/).


## Community and support

As this project is still very fresh it doesn't yet have a vibrant community behind it. 

If you want to get involved in helping to spread the word and get people modelling cool things together, feel free to stop by the project's [discord server](https://discord.gg/VxC4ssK7eX) and [subreddit](https://www.reddit.com/r/TheOutcome/).



