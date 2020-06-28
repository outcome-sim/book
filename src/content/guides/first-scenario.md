# First scenario

*outcome 0.2.2*

[https://github.com/theoutcome/first_scenario](https://github.com/theoutcome/first_scenario)

In this short tutorial you will create a very simple scenario, using the module created in the [first module](./first-module.md) tutorial.

## Creating scenario manifest

Scenario can be defined as a "collection of modules". That's because scenario itself will not provide any data other than the scenario manifest. Hence there is really not much to creating a scenario other than creating a proper manifest.

Of course, we also have to include a `mods` directory and include in it all the modules we will declare in the manifest.

Scenario manifest defines the scenario's list of modules, and specifies a bunch of other things. Here's what we'll be creating today:
```
name: "first_scenario"
title: "First scenario"
desc: "Scenario for testing."
author: "User"
version: "0.1.0"
engine: "*"
# modules are loaded in the order presented here
modules:
- first_module: "0.1.0"
```

[As mentioned in an earlier chapter under *content structure*](../content-structure/scenario.md), only the `name`, `version` and `engine` fields are required, we can omit any of the others and still have a working scenario.

## Including the `first_module` mod

We need a copy of `first_module` inside scenario's `mods` directory.

>**REMINDER:** the name of the module directory has to match the name specified in
the module manifest. In out case that name is `first_module`.


## Running the scenario

Scenario is treated as a *simulation model* and can be used to create a simulation instance.

Next up, we'll learn how to use `endgame` command-line tool to run our newly created scenario.
