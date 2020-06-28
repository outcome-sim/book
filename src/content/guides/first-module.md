# First module

*outcome 0.2.2*

In this short tutorial you will create a simple module, learning about the structure of a module, contents of the module manifest, the nature of declaration blocks and more.

## Module structure

[Internal structure of modules](../content-structure/module.md#file-structure) is almost completely arbitrary. You can organize your files as you want. This is because all module files (also called *user files*) are "the same" in terms of their internal structure. Inside the files we have declaration blocks that allow us to declare different kinds of elements. No external context is required.

The only element that's always required is the manifest. The manifest always exists in the top directory of the module.

A single module is itself a single directory with a module manifest `module.yaml` inside. Such a module with only the manifest present is a valid one, even though it's totally empty otherwise.

## Create module manifest

Let's start by creating a new directory and naming it: `first_module`.

**Remember that the name of the directory has to always match the name of the module as defined in the manifest.**

Module name is a string of characters without spaces. Doesn't really matter whether it's written as `first_module` or `FirstModule`; although it's useful to keep the convention the same for any single project you work on (e.g. a single module or scenario).

Next we'll create a new file. You can use any text editor you want. Call the file `module.yaml`. This is our module manifest. Paste the following lines into the new file and modify the entries as you see fit.
```
name: "first_module"
title: "First module"
desc: "First module created using the glorious tutorial."
author: "User"
version: "0.1.0"
engine: "*"
```
There are a few more entries we could use, like `desc_long` for long description and `website` to point anyone who uses our mod to the right place if they needed help or wanted to submit a fix. We also didn't declare `dependencies` which simply means there aren't any.

>If you use some sort of version control solution like `git` it's useful to include an online address of the repository in the `website` field.

## A new user file

Let's create a new file. Call it whatever you want, just make sure the extension is `.yaml` or `.yml`. I created a file named `examples.yaml`. The directory tree should look something like this
```
first_module
├── examples.yaml
└── module.yaml
```

## User file declaration blocks

We will include a couple things in our file:
- new entity type
- new component type
- new entity
- new component  

Each of these elements requires us to create a new *block*. Consider the following example.
```
new_block:
- element_1 # '-' means a list in yaml, so this is an element in the "new_block" list
- element_2 # '#' means a comment, so anything after it on that particular line is ignored:)
```

And here's what we're going to include in our file
```
entity_types:
- id: "region"

component_types:
- id: "property"

entities:
- id: "greenland"
  type: "region"

components:
# a component to track the bear population in a region
- id: bear_population
  type: property
  entity: region
  start_state: main
  # "tick" clock event is built-in, called on every clock tick
  trigger_event: tick
  vars:
  - pub int count = 2275
  states:
  # this is the only state in this component's state machine
  - id: main
    cmds:
    # it will simply print the "count" integer var every tick
    - print int/count
```

That should do it. There is only one problem though - we can't run a simulation with just a module.
Before we can run this and see how it prints the bear population count every tick we have one more step ahead of us.
We need to [create a *scenario*](./first-scenario.md).
