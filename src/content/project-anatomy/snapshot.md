# Snapshot

Snapshot is a serialized state of the simulation. You can think of it as of freezing the whole thing at some one time instance, with all the information preserved.

Snapshot can be used to create a new simulation instance.

For practical purposes, snapshots function like game-saves. Even though we
can create a simulation instance from a snapshot, it's not the
same as if we used the data we normally use to create sim instances (modules
organized into scenarios). Snapshot can still be modified, of course,
but it's way less convenient to modify than a collection of versioned modules.

> <br>**TBD:** Snapshot could potentially optionally contain a collection of archived past simulation states.<br><br>

Snapshot is contained in a single file. Serialization format is YAML, which means it's human-readable and can be modified relatively easily. Snapshot files can be compressed.

Right now snapshot creation is not well optimized for large simulations. 
