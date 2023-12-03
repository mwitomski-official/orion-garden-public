---
title: Tuples
description: This note provides a basic understanding of tuples in Python
author: Mateusz Witomski | Orion
date: 2023-11-07 01:10
type: programmingNote
tags:
  - programming
  - python
  - basics
enableToc: true
openToc: true
---
# Tuples

[🐍 Tuples](🐍%20Tuples.md) are almost exactly the same as lists.

1. The syntax for creating them uses parentheses instead of square brackets,
2. They cannot be modified (they are _[immutable](../../../dictionary/Programming/Mutability%20vs%20Immutability.md)_).
```python title:"Tuples"
t = (1, 2, 3, 4)
print(type(t))
# > <class 'tuple'>

# We can create tuple in this way also
t2 = 1, 2, 3, 4 
print(type(t2))
# > <class 'tuple'>

# Let's modify :)
# t[0] = 10 
# > TypeError: 'tuple' object does not support item assignment
```

3. [🐍 Tuples](🐍%20Tuples.md) are often used for functions that have multiple return values
```python ttile:"Tuples"
# Tuples are often used for functions that have multiple return values.
x = 0.125
# Method of float objects returns a numerator and a denominator in the form of a tuple
print(x.as_integer_ratio())
# > (1, 8)

# These multiple return values can be individually assigned as follows
numerator, denominator = x.as_integer_ratio()
print(numerator / denominator)
# > 0.125
```
## References
1. [Kaggle - Lists](https://www.kaggle.com/code/colinmorris/lists)