# Introduction to Lua scripting

*outcome 0.2.2*

*WIP*

Regular commands include most basic operations we would want to do on our data.
Simple calculations, evaluations, getting and setting variables can all be done
without using any complex scripts.  

Whenever we have the need to include more complex algorithms however, we have
the ability to include Lua scripts in our models.

To make use of Lua scripts you will need to master at least the basics of Lua.
If you didn't have any contact with programming up until now, don't be discouraged.
You will be able to follow this tutorial just fine.


### What is Lua

<a href="https://en.wikipedia.org/wiki/Lua_(programming_language)">
Lua is a lightweight programming language</a> designed primarily for embedded use
in applications, one of the most widely used scripting languages.

If you don't know much about Lua there are lots of resources to learn from online.


### Performance question

Lua itself is highly optimized and really quite fast. But the Lua scripts
we include in our components will always be slower than the bare commands.
This is something to keep in mind while designing your model.

Ideally we will only want to use Lua for **complex tasks that occur
infrequently** during the processing. Having a complex Lua script execute many
times every simulation tick can have a noticeable effect on performance.


## Declaring a simple `lua_script`

Here's a *map representation* of a simple `lua_script` cmd.

```yaml
- cmd: lua_script
  src: |
    print("Hello world!")
```


## `inputs` and `outputs`

The scripts we pass to our `lua_script` command don't have access to any of the
variables we can normally access. Instead we're required to specify what data
they will get and what data we will get out from them after they're finished
executing. It really is a quite simple arrangement.

Inputs are passed to the script as it's *global variables*. Outputs are


```yaml
- cmd: lua_script
  inputs:
    # lua global named "string_var" will be set to the value of `str/local_string`
    string_var: str/local_string
  outputs:
    string_var: str/string_var
  src: |
    print("Hello world!")
```
