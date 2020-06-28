# Anthropocene

Anthropocene is a **game** that incorporates an interface for interacting with the simulation. It places player in a position of the *decision maker* of one of the organizations of their choosing.

## Play as any organization

There really is no limit to what organization player can play as.

This is really based on the idea that the **organizations are at the core decision makers**, which is itself a rather straightforward framework for implementing gameplay. Of course there is more to that, there are different kinds of decisions, and there is more to playing as an org than just the decisions - actually gathering and processing the data by the player to use to inform their decisions is a large part of the gameplay here.

## Content compatibility within the scope of the general architecture

Anthropocene is based on the *outcome architecture*, so that any content compatible with it can be imported into the game and vice-versa. So for example you could start a *play-through* within the game and play it for a while, and then export it and use *outcome.rs* or another tool to make some predictions about how the *outcome* of that playthrough could change based on some possible choices. Or start with a more analytical approach, find a scenario which would itself (simulated without your input) play out really unfavorably and get it into Anthropocene to see if you could maybe change the outcome.

That's just scratching the surface. Flexibility of using the data for different things, some more interactive some more analytical for example, spawns a nice array of possibilities.

## Implementation details

The part actually dealing with outcome simulation processing is based on OutcomeSharp.

The game itself is created using the Unity game engine, UI is for the most part done using Marklight (presentation framework for Unity).
