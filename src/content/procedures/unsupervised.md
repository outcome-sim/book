# Unsupervised simulation run

It's a full (complete) simulation run processed "autonomously", meaning there was no external input provided during the simulation run.

Unsupervised simulation runs are not common for either a game setting or a simulation including externally provided agent input (see [server mode](server-mode.md)).

Unsim runs are used for situations where simulation speed is of the essence - providing input or reading arbitrary data during the simulation would slow it down. It's also usually done multiple times, either in parallel or in succession.

Running multiple unsupervised simulations is the basis for [proofs](proofs.md).

Unsupervised simulations require a specified *end condition*, which can be a simulation end date or another condition based on some concrete variable's value.
