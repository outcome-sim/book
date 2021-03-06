# Creating a new scenario

At the start of this chapter we've set out to create a simple *"hello world"* model. To accomplish this we will need to learn how to create a scenario from scratch. Dont worry, it's not as scary as it sounds.


## `new` subcommand


Creating a new scenario is as simple as typing the following in the command line:

```
outcome new hello_world
```

The `new` subcommand creates a new scenario with the specified name. If we rely on the defaults, `new` will populate the newly created scenario directory with the following files:

```
hello_world
├── mods
│   └── start
│       ├── mod.outcome
│       └── mod.toml
└── scenario.toml
```


## Let's make it our own

The `scenario.toml` manifest file contains basic information about the scenario, such as it's name, description and author.

Spin up your favourite text editor and change up the contents of that file. Here's an example of how it might look like after a quick redo:

```
[scenario]
name = "hello_world"
version = "0.1.0"
author = "Neo"
engine = "*"


[mods]
hello = "0.1.0"
world = "0.1.0"
```

Note the two new additions to the `mods` section. What's up with that?


## Scenario modules

Each scenario is made up of modules. This fact lets us build complex scenarios from already existing building blocks. 

In our case of a simple hello world scenario we don't have to split our model into two separate modules. But we will do it anyway. For science!

As you will see, this way we will reveal a few interesting points about the module system.

