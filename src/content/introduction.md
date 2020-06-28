# Introduction to the project

This page serves as a quick introduction to the project. It's written in a form of a list of answers to some of the frequently asked questions.


## What is this project about?

It's about creation of user friendly solutions for simulation model design and processing. It's about discovering possibilities for collaboration on different kinds of simulations, from multiplayer game worlds to models of cities and economies.

At a more basic level it's also about discovering a good minimal simulation architecture that's useful, extendable and easy to use.


## What could it be compared to, in terms of already existing projects?

Currently there are not that many projects aiming at making distributed simulations for games and science easier and more accessible.

One commercial project that exists in this space, which is actually using a similar underlying design approach, is [*SpatialOS*](https://documentation.improbable.io/spatialos-overview/docs). That said, they are still very much a *black box* company with no interest in sharing their technology with the community.


## How useful is it right now?

Right now the project consists of a proposed system for how collaborative simulation-modeling could happen, as well as experimental software implementing things that are necessary for this to happen.

If you're ready to build from source (Rust programming language) you can already run some of the software.

See [project overview](project-overview.md) for more information about the , and [the project status page](https://theoutcomeproject.com/status/) to learn more about what's being actively worked on right now.


## Can I make a multiplayer game with this?

Yes. Once the software gets mature enough and provides a stable API you will be able to create all sorts of interactive experiences with it.

The main *selling point* in terms of using `outcome` to create multiplayer experiences, is the possibility for creating very large game worlds with hundreds, even thousands, of concurrently connected players.

## Can I do science with this?

Sure. This project may become quite useful for studying complex emergent systems. As it grows it will probably become more and more useful for researchers. It's still not there yet though. 


## What does "reusing other people's models" mean?

It means that, due to modularity of the system, it's easier to stick different solutions together and expect them to work. If you wanted to simulate a whole city, you shouldn't have to model things like pedestrian behavior or weather systems from scratch.

Solutions that enable multiple people to work together on different parts of simulation models are still few and far in between. Projects like this one can start to attempt to change that.
