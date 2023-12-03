---
title: Kaggle Lab - Loops and List Comprehensions
description: Put short description here
author: Mateusz Witomski | Orion
date: 2023-11-12 21:53
type: programmingNote
tags:
  - programming
enableToc: true
openToc: true
---
# Kaggle Lab - Loops and List Comprehensions

## Task 1 - Have you ever felt debugging involved a bit of luck?

The following program has a bug. Try to identify the bug and fix it.

```python
def has_lucky_number(nums):
    """Return whether the given list of numbers is lucky. A lucky list contains
    at least one number divisible by 7.
    """
    for num in nums:
        if num % 7 == 0:
            return True
        else:
            return False
```

When I run it then I got: Incorrect: Got a return value of `None` given `nums=[]`, but expected a value of type `bool`. (Did you forget a `return` statement?)

### Solution

Remember that `return` causes a function to exit immediately. So our original implementation always ran for just one iteration. We can only return `False` if we've looked at every element of the list (and confirmed that none of them are lucky). Though we can return early if the answer is `True`:

```python
def has_lucky_number(nums):
    for num in nums:
        if num % 7 == 0:
            return True
    # We've exhausted the list without finding a lucky number
    return False
```

Here's a one-line version using a list comprehension with Python's `any` function (you can read about what it does by calling `help(any)`):

```python
def has_lucky_number(nums):
    return any([num % 7 == 0 for num in nums])
```

## Task 2 - Look at the Python expression below. What do you think we'll get when we run it?

When you've made your prediction, uncomment the code and run the cell to see if you were right. Implement a function that reproduces this behavior, returning a list of booleans corresponding to whether the corresponding element is greater than n.

### Solution

```python
def elementwise_greater_than(L, thresh):
    """Return a list with the same length as L, where the value at index i is 
    True if L[i] is greater than thresh, and False otherwise.
    
    >>> elementwise_greater_than([1, 2, 3, 4], 2)
    [False, False, True, True]
    """
    return [l > thresh for l in L]
    

L=[1, 2, 3, 4]
thresh=2

print(elementwise_greater_than(L, thresh))

# > [False, False, True, True]
```

## Task 3 - Complete the body of the function below according to its docstring

**Hint:** This is a case where it may be preferable to iterate over the _indices_ of the list (using a call to `range()`) rather than iterating over the elements of the list itself. 
When indexing into the list, be mindful that you're not "falling off the end" (i.e. using an index that doesn't exist).
### Solution

```python
def menu_is_boring(meals):
    """Given a list of meals served over some period of time, return True if the
    same meal has ever been served two days in a row, and False otherwise.
    """
    # Iterate over all indices of the list, except the last one
    for i in range(len(meals)-1):
        print(i)
        print(meals[i], ' == ', meals[i+1])
        if meals[i] == meals[i+1]:
            return True
    return False


meals=['Spam', 'Eggs', 'Spam', 'Spam', 'Bacon', 'Spam']
print(menu_is_boring(meals))

# > 0 Spam == Eggs 
# > 1 Eggs == Spam 
# > 2 Spam == Spam 
# > True
```

### How?

The key to our solution is the call to `range`. `range(len(meals))` would give us all the indices of `meals`. If we had used that range, the last iteration of the loop would be comparing the last element to the element after it, which is... `IndexError`! `range(len(meals)-1)` gives us all the indices except the index of the last element.

But don't we need to check if `meals` is empty? Turns out that `range(0) == range(-1)` - they're both empty. So if `meals` has length 0 or 1, we just won't do any iterations of our for loop.
## References
1. [Exercise: Loops and List Comprehensions](https://www.kaggle.com/code/mateuszwitomski/exercise-loops-and-list-comprehensions/edit)