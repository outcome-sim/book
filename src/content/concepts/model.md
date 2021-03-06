# Simulation model

At the heart of any simulation there usually lies some form of a [model](https://en.wikipedia.org/wiki/Conceptual_model) that defines the relations and rules that apply to objects existing within that simulation.

In our case the model not only provides the initial layout of entities, components, events, etc., but is also read, and mutated, at runtime.


## Assembling the model

One approach championed by the engine is *incremental assembly*, meaning building up the model at runtime. This can be done either by using the engine's built-in logic processor, or by feeding commands remotely through a client connection.

Another more classic approach is to define the model in a static fashion, for example using `yaml` or `json` structured data files. 


## Service processes as part of the model

Service processes that will be working on the simulation data through the client interface can also be considered part of the model. As such, it's good practice for services to be provided as open source, even if their internals are closed source and the service itself is only a wrapper with basic client functionality.

When including a totally "black-box" service binary, make sure that documentation is available on how it operates and how it's meant to interact with the engine.


## Components' logic models

[Built-in logic processor](logic-processor.md) makes use of the global model to store instruction information. Definitions of models of individual components contain logic information in the form of lists of commands.


## *Lazy loading* from disk

The engine will not attempt to load all the files within a scenario into memory and store within the global model object. This would cause problems with larger datasets.

Instead the model is understood more broadly to include the project (scenario, module) files stored on disk. Internally, the model object stores paths to all the files found within the scenario.


## Synchronization between nodes

As the model serves as a *kernel* holding all the important simulation rules, it has to be globally accessible and globally synchronized.

In a distributed setting with multiple separate nodes, the global model is one of the few things these nodes share in common. As such, it serves as main source of truth when it comes to both entity/component *prototypes* and executable logic attached to components.

Since the model itself can be mutated at runtime, the system is able to centrally handle any changes and ensure proper propagation in case of such changes.
