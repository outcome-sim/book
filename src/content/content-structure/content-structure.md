# Content structure

Data management is about handling, organizing and distributing the data that is used to create and run simulations. The main features relevant here are `mods`, `scenarios` and `snapshots`.

Put in one sentence:

_Mod is a collection of files, scenario is a collection of mods, snapshot is a serialized simulation instance state._

In this chapter we'll go through those features in more detail.


## File formats

The format of choice with this project is [YAML](https://en.wikipedia.org/wiki/YAML). Supported filename extensions include both `.yaml` and `.yml`. YAML is used for all module files, as well as all manifest files for modules, scenarios, etc. YAML was chosen because it's much more readable than JSON or XML.

There are also other file formats that are supported, though specifically designated for storing data. For example `.json` and `.png` files can be used. See the API section on `data` blocks for more information and examples.

## Semantic versioning

Versioning is used throughout content features for a number of things, including modules, scenarios, and the the engine itself. It makes things easier to track as changes are made over time.

One look at any scenario manifest already gives as a bunch of version information for different things:

```yaml
(...)
version: "0.1.0"
engine: "^0.2.0"
modules:
- module_one: "0.1.1" # require this exact version
- module_two: "*" # require any version of the module
- module_three: "2.1.*" # can also be written using '~' as "~2.1.1" or simply "2.1"
- module_four: "1.*.*" # can also be written using '^' as "^1.3.0" or simply "1"
(...)
```

All versioning is following the so called [Semantic Versioning](https://semver.org/) format. While it's not crucial to always follow the versioning spec, it's useful to know the basics. The above block gives a few examples. You can play with an [online semver calculator](https://semver.npmjs.com) if you're totally new to this.
