---
title: Collections
description: This note provides a basic understanding of collections in Python
author: Mateusz Witomski | Orion
date: 2023-11-07 00:09
type: programmingNote
tags:
  - programming
  - python
  - basics
enableToc: true
openToc: true
---
# 🐍 Collections

## Lists

Lists are "*[mutable](../../../dictionary/Programming/Mutability%20vs%20Immutability.md)*", meaning they can be modified "in place".

### Basics

1. A list can contain **a mix of different types** of variables: 
```python title:Different Types
example_list = ["String value", 33, help]
print(example_list)

# > ['String value', 33, Type help() for interactive help, or help(object) for help about object.]
```

2.  [Slicing](Slicing) - If I leave out the start index, it's assumed to be 0. So I could rewrite the expression above as:
```python title:Slicing
example_list = [1, 2, 3, 4, 5, 6]

# Display first 2 items -> [0:2]
print(example_list[:2])

# > [1, 2]
```

3. [Slicing](Slicing) - If I leave out the end index, it's assumed to be the length of the list:
```python title:Slicing
example_list = [1, 2, 3, 4, 5, 6]

# Give me all item from index 2 onward
print(example_list[2:])

# > [3, 4, 5, 6]
```

4. [Slicing](Slicing) - Below, other examples like *all except the first and last*, *last 3 items*
```python title:Slicing
example_list = [1, 2, 3, 4, 5, 6]

# Display all except the first and last
print(example_list[1:-1])

# Display last 3 items
print(example_list[-3:])

# > [2, 3, 4, 5]
# > [4, 5, 6]
```

### Main functions

| Function | Description                        | Example      |
| -------- | ---------------------------------- | ------------ |
| len      | Gives the length of a list         | len(list)    |
| sorted   | Returns a sorted version of a list | sorted(list) |

### Main methods

| Method | Description                                    | Example           |
| ------ | ---------------------------------------------- | ----------------- |
| append | Modifies a list by adding an item to end       | list.append(item) |
| pop    | Removed and returns the last element of a list | list.pop()        |
| index  | Returns index of element from a list           | list.index(item)  |

To search item in the list we can use operator **in**

```python title:"Operator in"
example_list = [1, 2, 3, 4, 5, 6]
print(1 in example_list)
print(100 in example_list)

# > True
# > False
```

## References
1. [Kaggle - Lists](https://www.kaggle.com/code/colinmorris/lists),
2. [🐍 Kaggle Lab - Collections](../../../Labs/Python%20Fundamentals/🐍%20Kaggle%20Lab%20-%20Collections.md)