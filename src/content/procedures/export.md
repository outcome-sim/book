# Export current simulation state

It's always possible to export current simulation state to file. For this we use the [Snapshot](../data/snapshot.md).

## Export process

The program goes through the whole Database of the simulation instance and saves all the data into a file.

It also copies the scenario that was used for spawning our current simulation instance. It will be needed if we ever wanted to import that snapshot later. The whole scenario is copied over to the snapshot directory.

## (experimental) Attaching collection of previous simulation states

Possibility for attaching to the snapshot a collection of previous states of the simulation is being considered for being implemented.

Such an approach has a few problems:
- the longer the simulation run, the bigger the snapshot
- need for specifying only a limited set of previous sim states data to be saved (otherwise there would be too much data)

The biggest obstacle to saving the previous simulation states into one big "archive" is the sheer size of such snapshot, and saving/loading times related to having to deal with that much data.
