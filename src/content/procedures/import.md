# Import previously saved simulation state

We can use existing snapshot to recreate the state of the simulation instance that was used to create that snapshot.

## Import process

The process is a bit more complex than the exporting process, mostly because the snapshot data file itself doesn't hold the data needed to recreate simulation instance. What it contains is a copy of the sim instance's Database object, which can be used only after the simulation instance itself is spawned.

To be able to recreate the state of things as they were when the snapshot was created, it needs to have the information about what *simulation instructions* are needed spawn the simulation instance - so it needs a list of module files. To achieve this the snapshot includes a copy of the whole scenario that was used for the original simulation instance used when the snapshot was created.
