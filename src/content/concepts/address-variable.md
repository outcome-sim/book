# Addresses and variables

All the data that exists within the scope of a simulation is organized into *variables*, which are referenced using *addresses*.

Since variables don't exist in a regular global state, and are instead stored on the level of individual entities, and are also organized around components, address format includes all that additional information.

## Different types of variables

Working with variables we use the notion of *variable types* that specify the kinds of data stored by specific variables. For example variable of type `int` stores an integer number, while variable of type `str_list` stores a list of character strings.

Current implementation of the engine supports 4 basic variable types: `str`, `int`, `float` and `bool`, along with list and grid types for each of those: `str_list`, `int_list`, `float_list`, `bool_list`, `str_grid`, `int_grid`, `float_grid`, `bool_grid`. Basic variable types may be expanded in the future to include different sizes for numeric variables, e.g. `float128`, `uint8`.

## Address as a unique reference

Addresses are used for referencing variables. Any full address is a unique reference to a specific variable stored within the scope of a simulation instance. This is an important feature in a distributed setting — we don't really need to know on which node the variable is currently stored, as long as we know the address we will be able to access it.

Each address is made up of three distinct parts, referencing respectively: entity, component and variable.

Here is an example of a full address:
```
:monster03:health:int:main
```

The the above address references some integer named `main`, existing as part of `health` component, which is attached to entity identified as `monster03`.

## Address and execution scope

Since the *runtime's logic processor* (which we will learn more about in later chapters) executes logic within certain *scopes*, we need to be able to use scope-aware addresses.

When executing logic within the scope of some component, which itself exists within the scope of a certain entity, the engine will automatically use that scope to properly handle our "local addresses".

Think about the example address from the previous paragraph again. 

```
:monster03:health:int:main
```

Imagine we were defining some logic to be executed on a `health` component. No matter what logic it was, we wouldn't want to include specific entity reference, since our component could be attached to other `monster` entity — it has to remain *"entity instance agnostic"*, so to speak.

Writing our logic we would refer to the variable simply as `int:main`, or alternatively `health:int:main`. The latter could also be used to access that same variable from another component attached to the same monster entity.

## Addresses in queries

WIP