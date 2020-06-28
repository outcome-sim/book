# State machine

Approach based on [finite state machines](https://en.wikipedia.org/wiki/Finite-state_machine) is an important feature of the system. It defines the style in which all the computation is handled.

While it is a fairly low-level model for computation, it remains a fairly intuitive one. There are only a handful of rules we need to remember:

- only one state is active at any given moment
- we can transition between the states during the course of the simulation
- state transitions can be triggered both internally (from within the state machine) and externally (by another state machine)


## Where do the state machines exist

State machines are tied to components. Every component contains a single state machine. Indeed we could say that every component **is** a state machine.

When components are discussed the notion of the state machine is usually present, but without specifically calling it a "state machine".

## States

Each state machine can have an arbitrary number of states defined.

Each state on a state machine can contain a number of [commands](./command.md), which are small executable instructions.

By default every component has a single empty state, called `none`. The `none` state is incapable of transitioning to any other state. In that case the transition can only be invoked from outside the state machine.

## Trigger events

Directly related to the notion of "clock ticks" is the notion of *clock events*. Each single processing turn is called a "tick". Clock events are "events" that get triggered every 'n' ticks.

Each component state machine contains a notion of *trigger (clock) event*. It simply means that the component state machine will be processed only once the proper clock event is triggered.

For example we could have a `day` clock event that is triggered once every 24 ticks. If we created a component state machine with the `day` clock event trigger, it would only get processed once every 24 simulation ticks.
