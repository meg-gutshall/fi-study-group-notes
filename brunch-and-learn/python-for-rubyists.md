# Python for Rubyists

> **Beth Schofield on 06/13/20**

The study group is set up comparing Ruby on the left side and Python on the right.

## Data Types

| Data Type | Ruby | Python |
| :--- | :--- | :--- |
| String | X | X |
| True | X | X |
| False | X | X |
| Nil | X | See note 1 |
| Integer | X | X |
| Float | X | X |
| Complex |   | X |
| Tuple |   | X, ordered, immutable |
| Symbol | X |   |
| Array | X |   |
| List |   | X, ordered, mutable |
| Hash | X |   |
| Dictionary |   | X, See note 2 |
| Set |   | X, See note 3 |

Note 1: Not a type in Python, nil is called none instead

Note 2: Unordered, 

Note 3: Sets only contain unique data

No symbols in Python

### Accessing Data in Collections



## Formatting

Naming conventions: [https://visualgit.readthedocs.io/en/latest/pages/naming\_convention.html](https://visualgit.readthedocs.io/en/latest/pages/naming_convention.html)

String formatting in Python: [https://realpython.com/python-string-formatting/\#2-new-style-string-formatting-strformat](https://realpython.com/python-string-formatting/#2-new-style-string-formatting-strformat)

* The indentation has meaning in Python
  * You can actually get `IndentationError: expected an indented block`
* Conditionals have colons on the end
* Two ways to use string interpolation
* Commenting is the same as Ruby \(`#`\)

## Object Orientation

### OO in Ruby

In Ruby, a private method can be accessed \(called\) by other methods in the same class but not accessed directly \(i.e. run in the console\).

### OO in Python

* A private method has an underscore in front of it
* A class method has a decorator above it
  * `@classmethod` needs to appear before **each** class method

## Spinning Up a Web App

* Flask and Django are popular Python APIs
  * Flask is more lightweight
  * Flask is to Sinatra as Django is to Rails
* Insert `breakpoint()` in the code for debugging

## Other Notes

### Big Draws

* Python's ability to manipulate data and work with numbers

