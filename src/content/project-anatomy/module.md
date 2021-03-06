# Module

Module, mod for short, is a collection of data files. It’s helpful to think of mods as packages - they allow for modularity, in the sense that we can put different collections of mods together and achieve different runnable scenarios.

## Inside a project

Mods always exist in dedicated `mods` directory inside the project's top directory.

## File structure

Each mod exists as it's own directory structure. Inside the mod directory there has to exists the module manifest.

There are not many strict requirements in terms of internal organization of files in a module other than the module manifest.

Here's a directory tree for an example module:

```
example_mod
├── module.toml
├── logic.outcome
├── test_data.yaml
└── json_data
     └── data_file.json
```

### Module manifest

Each mod needs a `module.yaml` file present in it's top directory.

```toml
[mod]
name = "example_mod" # unique name of the module, string without spaces
version = "0.1.0" # version of the module
engine = "0.1.3" # version(s) of the engine this module is compatible with
title = "Example module"
desc = "This module is an example"
desc_long = "This is just a testing module, not really usable. Keep on keeping on."
author = "John Doe"
website = "example.com"

[dependencies] # list of modules required for this module to work
another_mod = "0.1.1"
```