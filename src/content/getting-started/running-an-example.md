# Running an example

So you have installed `outcome` on you machine and can now invoke it from the command line. Great! Why not run take a quick dive into things by running an example.

Even though where `outcome` really shines is running distributed parallel simulations using multiple machines, there is nothing stopping us from running it on just a single machine locally. Indeed it's very easy to do:

```
outcome run <path-to-scenario>
```

The above command will spin up a simulation instance on our machine using the provided path to a scenario directory. By default it will start in an *interactive mode*, which can be seen as somewhat similar to a classic [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) — we will be able to step through the simulation and query data in-between the steps.

Now we only need an actual scenario we can run.


## Example scenarios 

[`outcome` code repository](https://github.com/outcome-sim/outcome) contains a series of [example scenarios](https://github.com/outcome-sim/outcome/tree/master/examples/simulation), all kept up to date so they can be run with the current version of the engine.

If you installed the engine by building it from source you should already have the repository cloned on your machine. Otherwise, download the repository, either by going to github and [getting a zip file package](https://github.com/outcome-sim/outcome/archive/master.zip) or running `git clone https://github.com/outcome-sim/outcome` from the command line.

Open the downloaded repository in the terminal, unpacking it first if necessary. Now try running one of the examples using `outcome run ./examples/simulations/<scenario_name>.toml`, replacing `<scenario_name>` with the name of an existing scenario file of course.

Below is a quick description of some of the provided example scenarios.


### `cubes`

One classic example is the `cubes` scenario. It models a world with a large plane on which multiple cubes are placed. Scenario-level setting let's us set the number of spawned cubes.

### `cubes-physics`

`cubes-physics` presents a similar scene to that from `cubes`, with one important difference: it includes a physics service. Scenario setting let's us define the starting layout of the cubes.


### `flock`

`flock` scenario sets up a 3d world with multiple bird entities, each following a few flocking behavior rules.


## Where are the visuals?

What we've been doing so far is not exactly full of visual clues. We spawned cubes yet we couldn't see them. How can we *see* what's going within our simulated world?

Well, command line is not really equipped to deliver a visual representation for anything. For that we will need to turn to different tools.

Keep in mind that `outcome` is designed to work on *multiple levels*, so to speak. We will always be expected to start out from the command line, and connect additional layers to that basic program. This is where the notion of a `server` comes in.

Changing our run command a little, we can make `outcome` start a new `server` for us:

```
outcome server --scenario ./examples/simulations/<scenario_name>.toml
```

Such `server` can be contacted by local or remote clients, that can query, and even mutate, simulation world data. This is how we will be able to create a visual representation of our worlds.


### Displaying simulated world in Unity3D

If you're familiar with the Unity game engine, you might want to consider checking out the [`outcome-unity-demo` unity project](https://github.com/outcome-sim/outcome-unity-demo). It contains scenes dedicated to some of the examples.


### Displaying simulated world using Bevy engine

If you already have Rust installed on your machine, consider giving [Bevy-based visualization demo](https://github.com/outcome-sim/outcome-bevy) a go.
