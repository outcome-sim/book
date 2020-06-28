# Let's make a clock

*endgame 0.1.3, outcome 0.2.2*

[https://github.com/theoutcome/clock_tutorial](https://github.com/theoutcome/clock_tutorial)

Building on what you've learned so far, let's create a clock.

Our clock will consist of hours, days, months and years. Once we build an appropriate module for the clock,
we will also configure `endgame` to display our clock in the prompt of the interactive runner, like so:
```
You're now in interactive mode.
See possible commands with "help". Exit using "quit" or ctrl-d.

Loading config settings from file (found interactive.yaml)
[1-1-2015 1:00]
[1-1-2015 2:00]
[1-1-2015 3:00]
[1-1-2015 4:00]
[1-1-2015 5:00]
(...)
```

## Clock module

Let's create a new scenario called `clock_tutorial`.

>**HINT:** You can use `endgame` to initialize a scenario for you if you don't want to
create the files manually.

WIP



## `endgame` configuration

We can change what `endgame` displays in the interactive runner's prompt.
To do this we will need to include the following in the `interactive.yaml` config
file:
```
prompt_format: "{}-{}-{} {}:00"
prompt_vars:
- /uni/uni/generic/clock/str/day
- /uni/uni/generic/clock/str/month
- /uni/uni/generic/clock/str/year
- /uni/uni/generic/clock/str/hour
```

>**REMINDER:** `endgame` by default loads configuration from a file called
 `interactive.yaml` from inside the directory where it's run from. If the file
 doesn't exist you can just create it. Alternatively use `cfg-save` while in
 the interactive mode to export current config to file.

Now you can either quit and start the interactive runner again, or just use the
`cfg-reload` command. The second option is useful because you don't have to exit
the current simulation run in order to change the prompt. Instead you can
tweak the config and reload it inside the interactive runner at any time.

Note that if any of the addresses listed in `prompt_vars` is not reachable
then the prompt will ignore the custom format entirely and default to showing
the usual tick count number.
