# Project Overview

This project is not monolithic. It's composed of a bunch of smaller efforts aimed at different subgoals. This includes not only core software, but also tech demos, documentation and community outreach.

## Simulation engine

This is where the magic happens. `outcome` repository consists of the core library and the main command line tool.

### Core library

At the core of it all lies the __core engine library__. It defines all the basic functionality related to creating and running simulations, exposing a simple interface to the programmer.

If we were to look into the code we would find that `outcome-core` package itself doesn't actually implement any concrete networking functionality. What is does is it provides a set of abstractions, like *nodes*, *connections* and basic *messages* (*"signals"*), which it uses internally to sketch out processing routines in a distributed setting without using any specific networking solution. Implementing different network transports and topologies on top of `outcome-core` is therefore fairly easy and doesn't involve hacking on the library itself.


### CLI tool

Alongside the core library there exists the main *command-line interface* tool. It is what we will actually invoke working with the `outcome` engine from the command line.

One of the important things it implements is networking functionality. `outcome-cli` creates it's own notions of *servers*, *clients*, *workers* and more, to enable networked processing patterns, including running distributed simulation deployments. It builds on the generic concepts from the core library and gives them more substance, importing established solutions like the `zeromq` messaging library.

In the future, more networking middleware options may get integrated, either into `outcome-cli` itself, or as separate tools. For example, one very promising alternative to `zeromq` is the `aeron` library.

## Inspector tools

WIP

## Tech demos

WIP
