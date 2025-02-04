---
title: OOP - Refresher
description: Put short description here
author: Mateusz Witomski | Orion
date: 2025-02-03 07:35
type: programmingNote
tags:
  - programming
enableToc: true
openToc: true
---
## OOP - Refresher

### What is the basic definition of a class?

```python
# TODO: create a basic class
class Book:
  def __init__(self, title):
    self.title = title

# TODO: create instances of the class
book1 = Book("Brave New World")
book2 = Book("War and Peace")
```

#### What does the __init__ function do?

When the class is created, line 7, then the function **init** is then called to initialize the new object with information, and it is called  before any of the other functions that you've defined in the class - initializer function.

> [!note]+ INFO
> You can insert what you want


### Single underscore vs Double underscore

| Feature                                                                | Single Underscore (_)   | Double Underscore (__)                                                                                       |
| ---------------------------------------------------------------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------ |
| Usage                                                                  | Generally used for:     | Used for [name mangling](https://x.com/i/grok?text=name%20mangling)                                          |
| - Temporary variables                                                  | Yes                     | No                                                                                                           |
| - Unused variables                                                     | Yes                     | No                                                                                                           |
| - [Private attributes](https://x.com/i/grok?text=Private%20attributes) | Conventionally          | Technically                                                                                                  |
| Name Mangling                                                          | No                      | Yes                                                                                                          |
| Purpose                                                                | Indicates to developers | [Prevents name clashes in subclasses](https://x.com/i/grok?text=Prevents%20name%20clashes%20in%20subclasses) |
|                                                                        | not to use directly     | by [renaming attributes](https://x.com/i/grok?text=renaming%20attributes)                                    |
| Example                                                                | `_variable`             | `__variable`                                                                                                 |
| Resulting Name                                                         | `_variable`             | `_ClassName__variable`                                                                                       |
- **Single Underscore ( _ ):**
    - Often used as a convention to denote that a method or attribute should be treated as [non-public](https://x.com/i/grok?text=non-public) but can still be accessed.
    - Can be used in [loops](https://x.com/i/grok?text=loops) or as a [placeholder for values](https://x.com/i/grok?text=placeholder%20for%20values) that are not used.
- **Double Underscore ( __ ):**
    - Implements **name mangling**, which means Python changes the variable name to include the class name to avoid [accidental overwriting](https://x.com/i/grok?text=accidental%20overwriting) in subclasses

Example code block

```python
planets[0:3]
```

```python fold:"This is collapsed" 
planets[0:3]
```

### How to compare a specific instance to a known type?

```Python
# TODO: use isinstance to compare a specific instance to a known type
print(isinstance(b1, Book))
print(isinstance(n1, Newspaper))
print(isinstance(n2, Book))
print(isinstance(n2, int))
```

## Quiz

| Question                                                                                                                          | Answear                                                                                                                                                           |
| --------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| What is the purpose of the `self` parameter within instance methods of a class?                                                   | to refer to the instance of the class on which the method is called                                                                                               |
| What is the primary purpose of the `init` method?                                                                                 | to **initialize** the instance content such as properties and variables                                                                                           |
| What is the primary difference between the `type()` function and the `isinstance()` function when checking the type of an object? | `type()` returns the specific class or type of an object, <br><br>while `isinstance()` checks if an object is an instance of a particular class or its subclasses |
| What is the correct code to determine if an instance of a class is either a `MyClass` object or a descendant of one?              | `result = isinstance(my_obj, MyClass)`                                                                                                                            |
| What is an instance method?                                                                                                       | a method that can be called on a specific instance of a class                                                                                                     |
| What is an instance attribute in Python?                                                                                          | a variable that holds data specific to an instance of a class                                                                                                     |
| What is the key difference between class variables and instance variables?                                                        | Class variables are shared among all instances of the class, while instance variables are unique to each instance.                                                |

## References
1.  [Python Documentation - Private Variables and Class-local References](https://docs.python.org/3/tutorial/classes.html#private-variables-and-class-local-references)
2.  [Python Documentation - Naming Conventions](https://www.python.org/dev/peps/pep-0008/#naming-conventions)