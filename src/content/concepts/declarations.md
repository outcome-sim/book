# Declarations

Let's look at declarations first. 

Everything to exist within a simulation needs to be **declared** in a user file. We'll look into [what are modules](../data/module.md) themselves in a later chapter under Data Management. For now it's enough to know that a module is a collection of module files.

The module files used for initialization are really just lists of declarations. Declarations can vary in size and content, depending on the thing being declared.

Here is an example of a very short module file with a declaration of a property element inside.

```
# declaration_example.yaml
element:
- id: forest_coverage
  type: property
  entity: region
  prop_var: number
```

Notice how we had to define that we're going to declare `elements` in the first line.

## What are module files?

Module files are text files that are written in a specific way that can be transformed into program-readable data. Our simulation program can use that data to spawn a simulation instance.

> **info**
> [Parsing](https://en.wikipedia.org/wiki/Parsing) is a process of analyzing a set of symbols, in our case a text file (module file), based on a set of predifined rules. The rules for parsing the module files are predefined and they have to be followed if we want our files to be usable with the existing programs that can run Outcome simulations. Right now this general idea of what parsing is should suffice. We'll look deeper into it in a [later chapter](../processing/parsing.md).

There are two file formats for the module files we can use:
- **`.yaml`**
- `.json`

> **info**
> Due to better readability and support for comments (lines starting with `#` that are ignored during the parsing process), **yaml** is the recommended format and will be used throughout this book.

### Data structure within the module file

Module files are structured in a very specific way. They are basically a list of [**key-value pairs**](https://en.wikipedia.org/wiki/Attribute%E2%80%93value_pair). That's why we can use both `.json` and `.yaml` formats - contents of those files can be easily converted from one to another, despite their use of different [*syntax*](https://en.wikipedia.org/wiki/Syntax) to represent the data.

What's important about this key-value pair structuring is that we need to always follow this convention for our declarations.

## What is a declaration?

We take a declaration to be a listing, or a mention of some **object relevant to our simulation architecture**, inside a module file.

Here's the earlier example of a property element declaration, with a few comments added:
```
# here we specify that all entries below this line
# will be declarations of an element object
element:
  # declaration of the property element starts here
  - id: forest_coverage
    type: property
    entity: region
    var: number
  # declaration ends here
```

Another example showing a declaration of an entity:
```
entity:
  - id: 01001
    type: region
```

Yet another example this time showing some data declaration:
```
data:
  region:
    01001:
      prop/forest_coverage: 5.3
    01002:
      prop/forest_coverage: 10.1
    01003:
      prop/forest_coverage: 1
```
