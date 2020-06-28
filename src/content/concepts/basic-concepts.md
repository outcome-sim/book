# Basic concepts

In this chapter we’ll look at some of the core concepts behind `outcome` simulations.

It's recommended to go through this chapter to get an understanding of the basic ideas around which the system is organized.

Descriptions in this chapter are mostly introductory. For more details on the individual concepts consult later chapters.


## At a glance

- simulation instance is essentially a collection entities, each with a collection of attached components
- data is stored in variables, which are referenced by globally unique addresses
- the engine features a built-in interpreter, logic execution happens on the component level and is based on clock-synchronized, event-triggered state machines
- globally synchronized model contains
- project files are organized into modules and scenarios
- external processes that query simulation data using provided APIs are called *services*
- ad
- arrangement of entities and services can be setup (and changed at runtime) to ensure efficient and performant computation, we call this *load balancing* 
