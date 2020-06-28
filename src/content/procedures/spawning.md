# Spawning

Spawning simulation related objects can be done using either bare paths or lesser objects as input. Some examples are:
- spawning simulation instance from path
- spawning simulation instance from scenario object
- spawning scenario object from path



## Spawning simulation instance

Spawning a new simulation instance is a process beginning with a reference to a scenario and ending with a proper simulation instance. Such newly created simulation instance can be passed to a processing procedure (see [processing single simulation tick](simulation-tick.md)).

The simulation instance is stored as an object within the program which spawned it, and with subsequent processing procedure it itself is modified based on the computed changes.

### Reference to the scenario

Reference to scenario is provided as a path to an actual directory where the scenario is (though since the default location of the `scenarios` directory is fixed just providing the name is also possible).

### Parsing the scenario

[Parsing](parsing.md) includes reading all the data from the referenced scenario directory and processing it based on the parsing rules.

Parsing process ends with

### Initialization

Here things get initialized into actual objects in the program's memory.