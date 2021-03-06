# Basic Concepts

In this chapter we’ll take a step back, and look at some of the core concepts behind `outcome` simulations.

It's recommended to go through this chapter to get an understanding of the basic ideas around which the engine is organized.

Descriptions in this chapter are mostly introductory. For more details on the individual concepts consult later chapters.


## At a glance

- simulation state consists of the *model* (commonly shared, more static) and collection of *entities* (distributed, more dynamic), each entity having zero or more *components* attached to it
- data is stored as component-bound *variables*, which can be referenced using globally unique string *addresses*
- simulation models are represented using *scenarios*, each composed of multiple versioned *modules*
- external processes called collectively *services* query simulation data using the *client* API 
- simulations can be *dynamically scaled* at runtime to accomodate changes in computation and/or memory requirements
- the engine features a built-in interpreter, logic execution happens on the component level and is based on global-event-triggered state machines
