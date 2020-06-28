# Simulation model

At the heart of any simulation there usually lies some form of a [model](https://en.wikipedia.org/wiki/Conceptual_model) that defines the relations and rules that apply to objects existing within that simulation.

In our case the model not only provides the initial layout of entities, components, events, etc., but is also read, and mutated, at runtime.



## Assembling the model

Main approach championed by the engine is one focused on *incremental assembly*, meaning building up the model through the process of executing commands on already existing components.

*Incremental assembly* is not the only way. One can also define the model in a more static fashion, for example using `yaml` or `json` structured data files.


## Components' logic models

[Built-in logic processor](logic-processor.md) makes use of the global model to store instruction information. Definitions of models of individual components contain logic information in the form of lists of commands.


## *Lazy loading* from disk

The engine will not attempt to load all the files within a scenario into memory and store within the global model object. This would cause problems with larger datasets.

Instead the model is understood more broadly to include the project (scenario, module) files stored on disk. Internally, the model object stores paths to all the files found within the scenario.


## Synchronization between nodes

As the model serves as a *kernel* holding all the important simulation rules, it has to be globally accessible and globally synchronized.

In a distributed setting with multiple separate nodes, the global model is one of the few things these nodes share in common. As such, it serves as main source of truth when it comes to both entity/component *prototypes* and executable logic attached to components.

Since the model itself can be mutated at runtime, the system is able to centrally handle any changes and ensure proper propagation in case of such changes.
