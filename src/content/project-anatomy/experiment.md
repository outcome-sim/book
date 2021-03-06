# Automated experiments

Being able to simulate complex systems interactively is one thing. Trying to assess impact of certain smaller changes to the system and discovering regularities is another.

Doing this requires being able to rerun certain parts of simulation many times over, introducing small changes every number of runs. It also requires capturing the experiment data in a controlled way so that we capture only the interesting bits anad leave out anything we don't need.

*Experiments* allow just that. 

## Experiment structure

An experiment is defined with a single manifest file. 

Captured data can be redirected to a specified target directory. 




It's based the following ideas:

- complex dynamic systems don't yield consistent results, but
- restricting the length of the simulation makes for more consistent results, also
- we can run our simulation multiple times and try to spot correlations in the data