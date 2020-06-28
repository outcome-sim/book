# Scenario

Scenario wraps a collection of mods into one *simulation environment*, so to speak. It's a structure representing, well, a scenario, meaning a certain outline of the plot meant to unfold when the scenario is simulated. 

Scenario can be used to create a simulation instance.

## File structure

The scenario exists as it's own separate directory. Inside the scenario directory there has to be the scenario manifest. All modules should be placed inside the `mods` directory.

Here's a directory tree for an example scenario called `test_scenario`.

```
test_scenario
    ├── mods
    │   ├── module_one
    │   │   ├── data_test.yaml
    │   │   ├── json_data
    │   │   │    └── data_file.json
    │   │   ├── module.yaml
    │   │   ├── orgs.yaml
    │   │   └── regions.yaml
    │   ├── module_two
    │   │   └── module.yaml
    │   ├── module_three
    │   │   ├── comps.yaml
    │   │   ├── events.yaml
    │   │   └── module.yaml
    └── scenario.yaml
```

## Manifest file

Scenario manifest file is always named `scenario.yaml`.

```yaml
# those first three fields are required
name: "test_scenario" # scenario name, string without spaces
version: "0.1.0" # scenario version
engine: "0.1.0" # simulation engine version required by the scenario
# the rest is optional
title: "Test scenario"
desc: "Scenario for testing."
desc_long: "This is a long description of our test scenario.
            Notice how we can introduce a line break here.
            Check out YAML specification for more information
            on what you can do with strings."
author: "Adam Adamsky"
website: "theoutcomeproject.com"
# modules are loaded in the order presented here
modules:
- module_one: "0.2.0"
- module_two: "*"
settings: # settings are an easy way to tweak some crucial variables
  /uni/const/quantum_drive_tech_possible: false
```
