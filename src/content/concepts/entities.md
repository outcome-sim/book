# Entities

Entities define objects that share behavior (*instruction sets*) with other entities in their entity type group.

You might have noticed how we had to specify an `entity` entry in the example declaration on the previous page. Here it is again:
```
# declaration_example.yaml
element:
  - id: forest_coverage
    type: property
    # here's the entity entry
    entity: region
    prop_var: number
```

We have to specify an entity here because the property element can be declared for any of the entity types. This means that our newly declared property **element will be replicated for each entity type we specified in the entity entry**. This is the core idea behind entities - we're creating types of objects that will share the instruction sets, and ultimately actual *behavior patterns* (given the same input).


Entities are divided into 4 types:
- region
- organization
- global
- universal

Another way to think about entity types would be to consider them different “simulation levels”, each entity existing on one of these 4 simulation levels. Entities of each type are always given the same set of instructions. Following the “simulation level” analogy we could say that for example all region entities exist on the same “simulation level” (we could call it the “region simulation level”). Having the same set of instructions means their behavior will be appropriate for what they are actually representing (e.g. a region).

> **info**
**Note:** This doesn’t mean they all will always behave the same way - given different inputs, starting data and some amount of randomness the actual "output" for all same-level-entities will be quite different.

## Static entities

Entities exist as *static* objects within the simulation, meaning **they are to be created only once, and reused during the simulation run**.

An important question to ask is *"how would we add an entity during simulation run?"*. Answer is - we don't.

For the geographically defined entities, like regions, the solution is mostly straightforward - even the most radical changes can't change the premade entity set (like with the region entities), we just transform one entity into another.

For orgs (the non-geographically-defined entities) if we want to *add* new ones during the simulation run, we need to create a pool of blank ones beforehand and use those. We can't actually add new entities to the system once it's initialized. 
