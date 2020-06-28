# Parsing and Linting

**Parsing** is a fancy word for **interpreting**, or **analysis based on some concrete rules**. During the parsing phase the input data (module files) is read and transformed into data structure the program can directly understand.

**Linting** is a process of checking the input data for errors. Linting can be implemented using parsing functions, which already support throwing errors and warnings - that's why the base implementation libraries don't offer linting functions themselves.


## Parsing input

Parsing procedures are able to take two kinds of input:
- string paths to relevant files
- lesser objects (already parsed earlier)

Some examples would be:
- simulation instance from path
- simulation instance from scenario object
- scenario object from path


## Parsing into objects

Parsing process returns objects that can be referenced and used later. 
