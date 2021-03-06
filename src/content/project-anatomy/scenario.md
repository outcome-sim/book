# What is a scenario

Scenario represents a single *case* that can be run. It's a simulation setup that specifies how the initial state should look like. 

Scenarios are defined using `.toml` manifest files. 




Multiple different scenarios can exist inside a single project directory. This way they can *share* whatever modules are stored within the bounds of that project. 

><br>**NOTE:** The engine will replicate the whole project structure across nodes. For heavier projects with multiple scenarios having barely anything in common in terms of shared modules and services, it may be wise to split them into separate projects.<br><br>

## Scenario manifest

The manifest file specifies:
- information about the scenario, including name and version information,
- modules to be included,
- services to be run alongside,
- initial settings to be performed,
- workers to connect to when starting a distributed cluster
- coordinator address



Scenario can be used to create a simulation instance.


