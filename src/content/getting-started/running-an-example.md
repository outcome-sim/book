# Running an example

So you have installed `outcome` on you machine and can now invoke it from the command line. Great! Why not run take a quick dive into things by running an example.

Even though `outcome` is designed around running distributed simulations with multiple machines, there is nothing stopping us from running it on just a single machine locally. Indeed it's very easy to do:

```
outcome run <path-to-scenario>
```

The above command will spin up a simulation instance on our machine using the provided path to a scenario directory. By default it will start in an *interactive mode*, which can be seen as somewhat similar to a classic [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) — we will be able to step through the simulation and query data in-between the steps.

Now we only need an actual scenario we can run.
