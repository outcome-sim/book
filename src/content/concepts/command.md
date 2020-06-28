# Command

Command, abbreviated to cmd, is a small executable instruction built into the simulation engine.

Commands can do very different things, from simple mathematical operations to including scripts.

All commands accept some kinds of arguments.  

## Declaration using map or string

User often has a choice to use either a map representation or a string representation of a command. Here's a very simple example of both
```yaml
cmds:
# string
- print str/something
# map
- cmd: print
  addr: str/something
```

Not all commands support both representation modes. Some commands such as `lua_script` only support the map representation.

## Required arguments

Required arguments are also called *positional* arguments. Commands can have different numbers of required arguments. `print` only requires a single argument, for example.

String and map representations have slightly different requirements when it comes to positional vs optional arguments. For string representation positional arguments should always be placed right after the command and before any optional arguments.
```
command <positional-1> <positional-2> [OPTIONS]
```

## Optional arguments

As the name suggests, these are the arguments that are not required, but instead *optional*.

For string representations optional arguments follow a syntax inspired the general practice of [conventional GNU/POSIX syntax](https://www.gnu.org/software/libc/manual/html_node/Argument-Syntax.html). Don't worry if that isn't at all familiar, the rules are very simple:

- we use `-` to declare a short option, e.g. `-f`
- we use `--` to declare a long option, e.g. `--false`
- options can take in values, e.g. `-f some_value` or `--false some_value`
- options can be without values, these are so called "flags", e.g. `-t`
  - short flags can be combined, e.g. `-ft`


## Speed vs complexity

For the most part, commands are meant to be simplest possible implementations of some specific actions. They are usually meant to do one task, and to do it well.

For more complex algorithms we shall use scripts. They can be slower but we can do even more interesting computation with them.

## Execution flow

Commands are bound to component states. Each component state contains a list of commands which constitute it's logic. When a component state is triggered for execution, it's commands are executed one by one, starting with the first one on the list.

Execution flows from the first command to the last. This flow can be broken or changed. Any command can return a result that will signal breaking or jumping to another command on the list. This introduces the possibility for simple loops.

Command definitions can include options which will dictate their behavior in certain circumstances. This includes the possibility of breaking or changing the execution flow.

```
# this will break before printing anything
cmds:
- set string/name "pancakes"
- eval string/name == "cupcakes" --if-false break
- print "this should not get printed"
```

And here's an example of a _switch_ of sorts.

```
# this will change current component state based on the evaluated variable
# suppose string/name is currently "Horse"
cmds:
# first eval "fails"
- eval string/name == "Mouse" --if-true goto.mouse_state
# second eval changes current state to "horse_state"
- eval string/name == "Horse" --if-true goto.horse_state
```
