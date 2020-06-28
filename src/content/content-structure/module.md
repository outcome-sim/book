# Module

Module, mod for short, is a collection of data files. It’s helpful to think of mods as packages - they allow for modularity, in the sense that we can put different collections of mods together and achieve different runnable simulations.

For managing multiple mods within one “environment” we’re moving into the domain of [scenarios](./scenario.md).

## Module as part of scenario

Mods always exist in dedicated `mods` directory of *scenarios*.

## File structure

Each mod exists as it's own directory structure. Inside the mod directory there has to exists the module manifest.

There are not many strict requirements in terms of internal organization of files in a module other than the module manifest.

Here's a directory tree for an example module:

```
test_mod
├── data_test.yaml
├── json_data
│    └── data_file.json
├── module.yaml
├── orgs.yaml
└── regions.yaml
```

### Module manifest

Each mod needs a `module.yaml` file present in it's top directory.

```yaml
# the following three entries are required
name: "test_mod" # unique name of the module, string without spaces
version: "0.0.1" # version of the module
engine: "0.0.1" # version of the engine the module is compatible with
# the rest is optional
title: "Test mod"
desc: "Just testing."
desc_long: "This is just a testing module, not really usable."
author: "John Doe"
website: "example.com"
dependencies: # list of modules required for this module to work
- another_mod: "0.1.1"
```

### Flexibility within the mod

There is much flexibility when it comes to organization of user files inside a mod. This flexibility is possible because the files themselves specify everything inside them - the declarations made within module files don't need any additional context. Thus, structure of directories within the mod, even the names of the files are not an essential part of the module file processing.

Program reading a module will read all files recursively (given they have the proper `.yaml`/`.yml` extension).

Organization of files into directories can be useful, so can be certain approaches to naming the module files. This is left entirely to the user.
