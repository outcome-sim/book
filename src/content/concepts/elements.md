# Elements

Elements are based on the concept of Finite State Machines (FSM). Each element has a set of states specified, at any moment only one of the states of the element can be “active”.

## What are states?

**Element state** is at it's core a list of commands (instructions). States can be invoked and run, meaning the commands inside it will be processed.

States also support **collections** of commands within the structure of the states themselves. We can have an element state that's composed of multiple **collections**. Collections can't be invoked directly as states can, though there is an option to switch between collections internally.

## Different types of elements for different tasks

There are a number of specific element types, all designed to represent specific things. All of the elements are designed using the same base structure of **states**. Indeed there is a generic element type which is the default element type. Other element types build on top of that, differing mostly in terms of how they are declared.

## Declarations

Different element types can have different rules for declaring things. This is because due to different purposes of the element types they need different things declared.

Details on how the different elements are declared are specified in the subsequent sub-chapters.

## Invoking the states

Element states can be used like crude version of [functions (subroutines)](https://en.wikipedia.org/wiki/Subroutine) in programming, in the sense that they can be externally invoked (*called*). This means that we can have one state executing a command which will start executing another state.

This idea of a state machine is useful here because the simulation invokes execution of the element states on a time tick basis, meaning it’s easy this way to have for example an element waiting

## Built-in states

There is a set of built-in ([hardcoded](https://en.wikipedia.org/wiki/Hard_coding)) states that all elements share.

Currently the built-in states for all elements are:
- `inactive` inactive state with no instructions, this state can be treated as "final" in the internal context of the element as there is no way to get out of it without an external action (like a state invoke) from another element

Different element types can also have built-in states specific to them. Listing of those built-in states is available for each element type specification in the coming sub-chapters.
