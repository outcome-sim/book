# Anatomy of a Project

When it comes to handling, organizing and distributing the project data used to create and run simulations, main  are `modules` (`mods`), `scenarios` and `projects`.

Mods are collections of files recognized by the engine. Ideally, a single mod encapsulates some specific functionality in a way that enables use with more than a single scenario, and in different combinations.

Scenarios assemble mods into coherent, runnable models.

Projects are the modelling *workspaces*. Single project contains a single common `mods` directory along with one or more scenario manifests.


## File structure

The project exists as it's own separate directory. Inside the project directory there has to be at least one scenario manifest. All modules should be placed inside the `mods` directory.

Here's a directory tree for an example project:

```
example_project
    ├── mods
    │   ├── module_one
    │   │   ├── module.toml
    │   │   ├── data_test.yaml
    │   │   ├── more_data.yaml
    │   │   └── json_data
    │   │        └── data_file.json
    │   ├── module_two
    │   │   └── module.toml
    │   ├── module_three
    │   │   ├── module.toml
    │   │   ├── comps.toml
    │   │   └── events.toml
    ├── scenario1.toml
    └── scenario2.toml
```

## File formats

Manifest files for both scenarios and modules are written in the [TOML](https://en.wikipedia.org/wiki/TOML) format. File extension for TOML format is `.toml`. TOML was chosen because it's much more readable than JSON or XML.

For non-manifest files there are a few supported file formats. Currently the main structured data format supported by the engine is YAML (`yaml`, `yml`). For storing data that will be loaded at runtime, formats like `.json` or `.png` files can be used. 

## Semantic versioning

Consistent versioning is used for a number of things, including modules, scenarios, and the engine itself. It makes things easier to track as changes are made over time.

```toml
[scenario]
name = "hello_world"
version = "0.1.1"
engine = "^0.1.3"

[mods]
hello_world = "*"
```


Versioning scheme follows the [Semantic Versioning](https://semver.org/) format. While it's not crucial to always follow the versioning spec, it's useful to know the basics.  If you're totally new to this, you can try playing around with an [online semver calculator](https://semver.npmjs.com) to get familiar with the different syntax rules for version requirements.
