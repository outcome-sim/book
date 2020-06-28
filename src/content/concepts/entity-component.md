# Entities and components

In terms of core design aspects, `outcome` draws heavily from the ideas behind Entity-Component-System architecture, often shortened to ECS.

At it's most basic, any `outcome` simulation consists of a set of entities, each with a number of components attached to it. Result is a flexible arrangement of objects that can be used to accomplish many different tasks.

Exact arrangement of the entities and their components can be either very dynamic or more static. Entities can be created and destroyed, components can be attached and removed, or things can be established once in the beginning and not really change much during the course of the simulation.

Whether more dynamic or more static, the idea of entities and components is crucial to understand. It influences not only the data layout of a simulation, but also to a large extent the execution model itself.


## Entity

Entities are the fundamental objects in the system. The most important elements an entity holds internally are:
- data storage object, and
- component collection

We can spawn as many entities as needed. They can be created at the initial set up point, or later during the simulation.

An entity is described by it's *type* and it's *id*, which together form it's unique identifier. Here's an example entity signature:
```
:entity_type:entity_id
```

### Entity type

When it comes to entities, an entity _type_ helps define what components can be attached to an entity. Registering a component requires us to specify entity type for which it will be available.

As components will use entity-local addresses to get variables, we need this idea of matching types to be able to make some assumptions about what entity our component is attached to.

Each entity type introduces a new namespace for entities of that type. This means we can have entities `:yellow:banana` and `:green:banana` and they won't collide namespace-wise.


## Component

Component lies at the core of computation. Each component instance is assigned to a single entity.

Each component defines a set of it's own variables and contains a single state machine (see next sub-chapter).

### Component type

We can use component _type_ to create sets of components that will have common characteristics.

Declaration of a new component type can contain things that we would normally declare for components themselves. What we define here will act as *default* for any new component of that type we might declare elsewhere. This *default* can be overriden for any of the entries by just declaring that entry on the component.

Component type can be also used as a way of organizing components, and/or expanding the component namespace (like with entity type).

```yaml
# declare a new component type
component_type:
- id: decision
  vars:
  - id: template_var
  ...
  states:
  - id: template_state_1
  ...

# use the new component type
component:
- id: choice_213
  type: decision

# component `choice_213` has a var `template_var`
# /region/e_01001/decision/

```
