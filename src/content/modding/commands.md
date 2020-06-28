<style>
table {
    width:100%;
}
</style>

# Commands API

> <br>**NOTE:** this API is still very unstable, it's a proof of concept. It will change drastically.<br><br>

This page includes a list of commands available to the user.

Formats for the string and map representations:
```
# string
- command <required> [OPTIONS]
# map
- cmd: <cmd_name>
  <required_name>: <required_value>
  <option_name>: <option_value>
```




## `print`

Print value from address.

```
# string
- print <addr> [OPTIONS]
# map
- cmd: print
  addr: <address>
```


## `add`

Increment var at address by the given value.

```
# string
- add <addr> <value> [OPTIONS]
# map
- cmd: add
  addr: <address>
  value: <value>
```

## `set`

Set var at address to the value from another address.

```
# string
- set <target:address> <source:address> [OPTIONS]
# map
- cmd: set
  target: <address>
  source: <address>
```

## `eval`


```
# string
- eval <addr:address> <test_value> [OPTIONS]
# map
- cmd: eval
  addr: <address>
  test_value: <value>
```


## `calc`

Set var at address to the result of a calculated expression.

```
# string
- calc <target:address> <expr:expression> [OPTIONS]
# map
- cmd: calc
  target: <address>
  expr: <expression>
```
