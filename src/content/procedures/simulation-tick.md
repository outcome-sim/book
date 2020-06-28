# Processing single simulation tick

Processing simulation tick involves processing all of the little commands as declared for element. All those commands, as well as all the other data they will use during the processing, are already stored inside the simulation instance object as program-readable instructions and data structures.

## Processing order

Processing based on entity objects, ordered by the entity type (region, organization, global, universal).
Further down processing based on element objects, ordered by the element type (specifics tbd here).
Commands within the element state are processed one after another (top-down based on the declaration order).
