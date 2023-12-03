---
title: Loops
description: Put short description here
author: Mateusz Witomski | Orion
date: 2023-11-12 19:46
type: programmingNote
tags:
  - programming
  - "#python"
  - basics
enableToc: true
openToc: true
---
# 🐍 Loops

## For loop

> [!info]+ Loop over it!
> Basically, if it can be thought of as a group of things, you can probably loop over it.

The `for` loop specifies
- the variable name to use (in this case, `planet`),
- the set of values to loop over (in this case, `planets`),
- You use the word `in` to link them together.

Example below, `end` parameter will be used to print list data on the same line. 

```python title:"Simple list iteration"
planets = ['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']
for planet in planets:
    print(planet, end= ', ') # print all on same line

# > Mercury, Venus, Earth, Mars, Jupiter, Saturn, Uranus, Neptune,
```

The object to the right of the `in` **can be any object that supports iteration**. 

### Iteration for a tuple

Example below, iteration over the elements of a [tuple](🐍%20Tuples.md): 

```python title:"Simple tuple iteration"
multiplicands = (2, 2, 2, 2, 2, 2)
product = 1
for mult in multiplicands:
    product = product * mult
print(product)

print(2**6) # The power of 2 to 6

# > 64
# > 64
```
### Iteration for a string

We are able to loop through each character in a string like below:

```python title:"Simple string iteration"
s = 'steganograpHy is the practicE of conceaLing a file, message, image, or video within another fiLe, message, image, Or video.'
msg = ''
# print all the uppercase letters in s, one at a time
for char in s:
    if char.isupper():
        print(char, end='')

# > HELLO
```
### Function range

`range()` is a function that **returns a sequence of numbers**.

For example, if we want to repeat some action `3` times:

```python
for i in range(3):
    print("> Doing important work. i =", i)

# > Doing important work. i = 0 
# > Doing important work. i = 1 
# > Doing important work. i = 2 
```

## While loop

The other type of loop in Python is a `while` loop, which iterates **until some condition is met**.
	The argument of the `while` loop is evaluated as **a boolean statement**, and **the loop is executed until the statement evaluates to False**.

```python title:"Example of while loop"
i = 0
while i < 3:
    print(i, end=' ')
    i += 1 # increase the value of i by 1

# > 0 1 2
```
## References
1. [Kaggle - Loops and List Comprehensions](https://www.kaggle.com/code/colinmorris/loops-and-list-comprehensions)