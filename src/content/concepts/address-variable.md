# Addresses and variables

All the data that exists within the scope of a simulation is organized into *variables*, which are referenced using *addresses*.

Since variables don't exist in a regular global state, and are instead stored on the level of individual entities, and are also organized around components, address format includes all that additional information.

## Different types of variables

Working with variables we use the notion of *variable types* that specify the kinds of data stored by specific variables. For example variable of type `int` stores an integer number, while variable of type `str_list` stores a list of character strings.

Current implementation of the engine supports 4 basic variable types: `str`, `int`, `float` and `bool`, along with list and grid types for each of those: `str_list`, `int_list`, `float_list`, `bool_list`, `str_grid`, `int_grid`, `float_grid`, `bool_grid`. Basic variable types may be expanded in the future to include different sizes for numeric variables, e.g. `float128`, `uint8`.

## Address as a unique reference

Addresses are used for referencing variables. Any full address is a unique reference to a specific variable stored within the scope of a simulation instance. This is an important feature in a distributed setting — we don't really need to know on which node the variable is currently stored, as long as we know the address we will be able to access it.

Each address is made up of three distinct parts, referencing respectively: entity, component and variable. Each of those three parts can be further broken down into two smaller chunks, broadly defined as *type* and *id*, though as we will learn later this means slightly different things for each of the parts.

Here is an example of a full address:
```
:monster:m03:property:health:int:main
```

The same address but with a more visual breakdown into the three different parts:
```
:[monster:m03]:[property:health]:[int:main]
```

So the the above address references some integer named `main`, existing as part of component of type `property` named `health`, which is attached to entity of type `monster` named `m03`.

## Address and execution scope

Since the *embedded interpreter*, which we will learn more about in later chapters, executes logic within certain *scopes*, we need to be able to use scope-aware addresses.

When executing logic within the scope of some component, which itself exists within the scope of a certain entity, the engine will automatically use that scope to properly handle our "local addresses".

Let's use the address from the previous paragraph as an example. Imagine we were defining some logic to be executed on a `property:health` component. No matter what kind of logic we're dealing with (don't worry, we will dive into all that in a later section) we wouldn't want to include specific entity reference, since our component could be attached to other `monster` type entities — it has to remain *"entity instance agnostic"*, so to speak.

Writing our logic we would refer to the variable simply as `int:main`, or alternatively `property:health:int:main`. The latter could also be used to access that same variable from another component attached to the same monster entity.

## Address as signature and "match pattern"

Sometimes we will need to reference things like component types. For that we shall use certain combinations of the different address parts. These combinations are not usable as variable references. We call those *signatures*.

Again, following the earlier monster health example, signature of a `property` component type looks like this:
```
:monster:*:property:*
```

First of all, as you can see we use a `*` star symbol to signalize a *wildcard*, or in other words — an *unknown*. Since component types have to be bound to specific entity types, the signature specifies an entity type, but omits specifying

 of all, we always include both chunks of a single address part. That's why we include the

Based on the above it's not hard to imagine how we shall form a signature of an entity type:
```
:monster:*
```

Notion of *wildcards*, or *unknowns*, is also used for simple pattern matching. Querying a simulation instance for health of all monsters we could simply use:
```
:monster:*:property:health:int:main
```

On the level of the engine library, this is called *expanding* the address. *Expanding* the above pattern simply means creating a collection of matching addresses, like so:
```
:monster:m02:property:health:int:main
:monster:m03:property:health:int:main
:monster:big_m01:property:health:int:main
```   

## Dynamic address using part substitution
