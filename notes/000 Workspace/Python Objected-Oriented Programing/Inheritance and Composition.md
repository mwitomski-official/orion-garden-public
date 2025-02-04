---
title: "2. Inheritance and Composition"
description: Put short description here
author: Mateusz Witomski | Orion
date: "2025-02-03 19:18"
type: programmingNote
tags:
  - programming
enableToc: true
openToc: true
---
## Inheritance and Composition

### How inheritance works in practice?

Look at the code below:
* Defined two base classes `Publication` and `Periodical`,
* Classes `Book`, `Magazine`, `Newspaper` inheritance from base classes,
* Class `Periodical` using inheritance from `Publication` and using method `super()` to initialize object  from it,
* If you want to inheritance from class you need to add it to the brackets like `Periodical(Publication)`, `class Book(Publication)` etc,

```Python
class Publication:
    def __init__(self, title, price):
        self.title = title
        self.price = price
       
class Periodical(Publication):
    def __init__(self, title, price, period, publisher):
        super().__init__(title, price)
        self.period = period
        self.publisher = publisher
        
class Book(Publication):
    def __init__(self, title, author, pages, price):
        super().__init__(title, price)
        self.author = author
        self.pages = pages

class Magazine(Periodical):
    def __init__(self, title, publisher, price, period):
        super().__init__(title, price, period, publisher)
        
class Newspaper(Periodical):
    def __init__(self, title, publisher, price, period):
        super().__init__(title, price, period, publisher)

b1 = Book("Brave New World", "Aldous Huxley", 311, 29.0)
n1 = Newspaper("NY Times", "New York Times Company", 6.0, "Daily")
m1 = Magazine("Scientific American", "Springer Nature", 5.99, "Monthly")

print(b1.author)
print(n1.publisher)
print(b1.price, m1.price, n1.price)

# Output: 
# Aldous Huxley
# New York Times Company
# 29.0 5.99 6.0
```





> [!note]+ INFO
> You can insert what you want


Example code block

```python
planets[0:3]
```

```python fold:"This is collapsed" 
planets[0:3]
```

### What is an abstract class?

An abstract class is a class that **cannot be instantiated**, meaning that **we cannot create an object of the abstract class**. 
Instead, **we can only create objects of its derived classes**. 

An abstract class **can have abstract methods**, which are methods **without implementation**. 
* These methods are meant to be implemented by the derived classes, and they provide a common interface for all derived classes. 
* The derived classes are required to implement all the abstract methods of the abstract class, or else they too will be considered abstract classes. We can create an abstract class using the `abc` built-in library
~ [1]

```Python
from abc import ABC, abstractmethod

class GraphicShape(ABC):
    def __init__(self):
        super().__init__()
        
    @abstractmethod
    def calcArea(self):
        pass
        
class Circle(GraphicShape):
    def __init__(self, radius):
        self.radius = radius
    def calcArea(self):
        return 3.14 * (self.radius ** 2)

class Square(GraphicShape):
    def __init__(self, side):
        self.side = side

    def calcArea(self):
        return self.side * self.side

# g = GraphicShape()
c = Circle(10)
print(c.calcArea())
s = Square(12)
print(s.calcArea())

# Output: 314.0, 144
```
### Difference between abstract class and interface in python (to check)

| Abstract Class                                                                             | Interface                                                                                |
| ------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------- |
| An abstract features developer’s class can consist of abstract as well as concrete methods | All methods of an interface are abstract                                                 |
| It is used when there are some common feature shared by all objects                        | It is used when all the feature need to be implemented differently for different objects |
| Its developer responsibility to create a child class for the features of an abstract class | Any 3rd person will responsible for creating a child class                               |
| It is comparatively fast                                                                   | It is comparatively slow                                                                 |
~ [2]


## References

1.  [Abstract Classes in Python (51/100 Days of Python)](https://martinxpn.medium.com/abstract-classes-in-python-51-100-days-of-python-94a80879ca6f)
2. [Difference between abstract class and interface in Python](https://www.geeksforgeeks.org/difference-between-abstract-class-and-interface-in-python/)