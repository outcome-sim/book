# Entities and components

In terms of core design aspects, `outcome` draws heavily from the ideas behind Entity-Component architectures.

At it's most basic, any `outcome` simulation consists of a set of entities, each with a number of components attached to it. Result is a flexible arrangement of composable objects.

Entities can be created and destroyed at runtime, similar to components which can be attached and removed at any point during the course of the simulation.

Entities are relatively self-contained data structures, meant for quick transfer between machines.


## Entity

![](/assets/entity-img-test.png)

Entities are the building blocks of the simulation. As such, they are used for building larger systems *from the ground up*.

While entities can be used to implement actor-like behavior, they are not actors in the classical actor-system sense. 

The most important elements an entity holds internally are:
- data store, and
- component collection

We can spawn as many entities as needed. They can be created during initialization, or at any later time during the simulation.

Simulation model contains a notion of a *prefab*, which is a recipe of sorts for creating a new entity. *Prefab* specifies what components an entity should be made out of.

At the moment of spawning, each new entity gets a globally unique integer identifier. Entities can optionally be given string identifiers as well, making it easier to access certain data from outside of the simulation.


## Component

Components 
