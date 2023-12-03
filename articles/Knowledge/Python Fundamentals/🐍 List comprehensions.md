---
title: List comprehensions
description: Put short description here
author: Mateusz Witomski | Orion
date: 2023-11-12 20:40
type: programmingNote
tags:
  - programming
  - "#python"
  - basics
enableToc: true
openToc: true
---
# 🐍 List comprehensions

## General

> [!note]+ INFO
> This is second part of tutorial [🐍 Loops](🐍%20Loops.md)

**List comprehensions** provide **a concise way** to **create lists**. Common applications are to make new lists where each element is the result of some operations applied to each member of another sequence or iterable, or to create a subsequence of those elements that satisfy a certain condition. **(2)**

```python title:"Comparation of approaches"
# With a list comprehension
squares = [n**2 for n in range(10)]
print("With a list comprehension:\n", squares)

# Without a list comprehension
squares = []
for n in range(10):
    squares.append(n**2)
print("Without a list comprehension:\n", squares)

# Lambda
squares = list(map(lambda x: x**2, range(10)))
print("Lambda:\n", squares)

# > With a list comprehension: 
# >  [0, 1, 4, 9, 16, 25, 36, 49, 64, 81] 
# > Without a list comprehension: 
# >  [0, 1, 4, 9, 16, 25, 36, 49, 64, 81] 
# > Lambda: 
# >  [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

Also, we can also use the condition `if`, let's assume that we want to create a collection of automobile manufacturers beginning with `A`

```python
automobile_manufacturers = ['Ford', 'Chrysler', 'Toyota', 'Honda', 'Nissan', 'Volkswagen', 'Mercedes', 'BMW', 'Audi', 'Renault', 'Citroën', 'Alfa Romeo']
automobile_manufacturers = [car for car in automobile_manufacturers if car[0] == 'A']
print("Cars:\n", automobile_manufacturers)

# > Cars: 
# >  ['Audi', 'Alfa Romeo']
```

> [!info]+ SQL 🤔
>  If you're familiar with [[SQL]], you might think of this as being like a ``"WHERE"`` clause

## Modification of items on the list

Here's an example of filtering with an `if` condition _and_ applying some transformation - `upper()` + sign `!` - to the loop variable:

```python
automobile_manufacturers = ['Ford', 'Chrysler', 'Toyota', 'Honda', 'Nissan', 'Volkswagen', 'Mercedes', 'BMW', 'Audi', 'Renault', 'Citroën', 'Alfa Romeo']
automobile_manufacturers = [car.upper() + '!' for car in automobile_manufacturers if car[0] == 'A']
print("Cars:\n", automobile_manufacturers)

# > Cars: ['AUDI!', 'ALFA ROMEO!']
```

> [!warning]+ To improve readability
> People usually write these on a single line, but you might find the structure clearer when it's split up over 3 lines - (operation, for, if)

> [!info] SQL 🤔
> Continuing the SQL analogy, you could think of these three lines as `SELECT`, `FROM`, and `WHERE`

```Python title:"3 lines"
[
    # SQL => SELECT 
    planet.upper() + '!' 
    # SQL => FROM 
    for planet in planets 
    # SQL => WHERE
    if len(planet) < 6
]
```

## List comprehensions combined with functions

List comprehensions combined with functions like `min`, `max`, and `sum` can lead to impressive one-line solutions for problems that would otherwise require several lines of code.

```python title:"Expanded version of function to count negatives on given list"
def count_negatives(nums):
    """Return the number of negative numbers in the given list.
    
    >>> count_negatives([5, -1, -2, 0, 3])
    2
    """
    n_negative = 0
    for num in nums:
        if num < 0:
            n_negative = n_negative + 1
    return n_negative

print(count_negatives([5, -1, -2, 0, 3]))

# > 2
```

And now let's compare these **short versions**:

**First**:

```python
def count_negatives(nums):
    return len([num for num in nums if num < 0])
    
print(count_negatives([5, -1, -2, 0, 3]))

# > 2
```

**Second:**

> [!seealso]+ Check it!
>  **Reminder**: in the [🐍 Booleans and Conditionals](🐍%20Booleans%20and%20Conditionals.md) exercises, we learned about a quirk of  Python where it calculates something like `True + True + False + True` to be equal to `3`.

```python
def count_negatives(nums):
    # Reminder: in the "booleans and conditionals" exercises, we learned about a quirk of 
    # Python where it calculates something like True + True + False + True to be equal to 3.
    return sum([num < 0 for num in nums])
    
print(count_negatives([5, -1, -2, 0, 3]))

# > 2
```

## Which way is best?

Which of these solutions is the "best" is entirely subjective. Solving a problem with less code is always nice, but it's worth keeping in mind the following lines from The Zen of Python **(3)**:

> Readability counts.  
> Explicit is better than implicit.

So, use these tools to make compact readable programs. But when you have to choose, favor code that is easy for others to understand.
## References
1.  [Kaggle - Loops and List Comprehensions](https://www.kaggle.com/code/colinmorris/loops-and-list-comprehensions),
2. [Data Structures](https://docs.python.org/3/tutorial/datastructures.html),
3. [The Zen of Python](https://en.wikipedia.org/wiki/Zen_of_Python)