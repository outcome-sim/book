# Running simulation on a server

An exciting possibility would be setting up a simulation runner as a server. We could communicate with such server using simple REST API.

There are several usecases that come to mind. Most of them though are different takes on the idea of providing IO channels (input and output) for agents ("decision makers") within the simulation. Other than that, simply the possibility of being able to have simulation runner hosted on a remote machine is desirable, both in terms of scalability possibilities and sheer processing power that could be used (running simulations on rented high-performance machines).

## External agent input with AI

Having a server infrastructure with which we can communicate using simple messages opens an interesting realm of experimentation, which is the realm of *([weakly](https://en.wikipedia.org/wiki/Weak_AI)) artificially intelligent* agents. Having access to both the simulation data (inspecting the simulation state using the API) as well the organization agent input ("making the choices" for the in-simulation agents, again externally through the API) would open possibilities for creating many kinds of AI agents. Those AI agents could either be "dumb" expert systems based on rigid rules (similar to the simulation rules themselves) or, maybe more significantly, could be learning agents which would learn to better respond to the situations presented to them as they were "playing the game".

## External agent input with human players

The simple infrastructure design as mentioned above, would also create a possibility for making a multiplayer-game-like system.

The actual implementations for this are many, and wouldn't have to actually aspire to be like contemporary strategy games at all. For example, one could envision a web-based game where players could collectively make decisions to be carried out by an organization by voting. Or a website where one could generate an alternate reality that would play out along side one's real life without much input from anyone at all (this could be done at slower speeds, like simulation month in a day).
