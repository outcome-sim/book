# Introduction

This page serves as a quick introduction to the project. It's written in a form of a list of answers to some of the frequently asked questions.


## What is this project about?

It's about creation of user friendly solutions for simulation model design and processing. It's about discovering possibilities for collaboration on different kinds of simulations, from multiplayer game worlds to models of cities and economies.

At a more basic level it's also about discovering a good minimal simulation architecture that's useful, extendable and easy to use.


## What could it be compared to, in terms of already existing projects?

Currently there are not that many projects aiming at making distributed simulations for games and science easier and more accessible.

Two commercial projects I'm aware of that exist in this space are [SpatialOS](https://documentation.improbable.io/spatialos-overview/docs) and [Aether Engine](https://hadean.com/spatial-simulation/). Both of them focus primarily on *spatial* simulations, meaning simulating entities existing in 2D or 3D space, with things like load distribution being based on position of entities in the world.

`outcome` is meant to be flexible, meaning it will support spatial simulation but also be able to handle non-spatial contexts just as well.

## How useful is it right now?

Right now a collection of experimental software is available, with some of the planned functionality already implemented.

Try running some of the [example scenarios](https://github.com/outcome-sim/outcome/tree/master/examples/simulation/) and follow the [getting started](getting-started/getting-started.html) guide to see what sort of features are available so far.

See [project overview](project-overview.md) and [the status page](https://theoutcomeproject.com/status/) to learn more about different *pieces of the puzzle* that are being worked on and updates on the latest progress.


## Can I make a multiplayer game with this?

Yes. Once the software gets mature enough and provides a stable API you will be able to create all sorts of interactive experiences with it.

The main *selling point* of `outcome`, in terms of using it for creating multiplayer experiences, is the possibility for creating very large game worlds with hundreds, even thousands, of concurrently connected players.

## Can I do science with this?

Sure. This project may become quite useful for studying complex emergent systems. As it grows it will probably become more and more useful for researchers. It's still not there yet though.

You're more than welcome to chime in and help drive the project in a more science-friendly direction!


## What does "reusing other people's models" mean?

It means that, due to modularity of the system, it's easier to stick different solutions together and expect them to work. If you wanted to simulate a whole city, you shouldn't have to model things like pedestrian behavior or weather systems from scratch.

Solutions that enable multiple people to work together on different parts of simulation models are still few and far in between. Projects like this one can start to attempt to change that.
