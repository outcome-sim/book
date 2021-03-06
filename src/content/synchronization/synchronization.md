# All About Synchronization

One of the core tasks of the engine is allowing for synchronized processing of stored simulation state. 

Synchronization here means orchestrating multiple different programs, be they running locally or remotely, each processing it's own *piece* of the overall simulated world. It's also about handling multiple separate worker nodes, each storing and doing work on it's own part of the larger simulated world.
