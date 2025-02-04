---
title: "Stocks"
description: Put short description here
author: Mateusz Witomski | Orion
date: "2025-02-03 19:07"
type: fleetingNote
tags: 
enableToc: true
openToc: true
---
## Task Stocks

```Python
# Python Object Oriented Programming by Joe Marini course example
# Programming challenge: define a class to represent a stock symbol

# Challenge: create a class to represent stock information.
# Your class should have properties for:
# Ticker (string)
# Price (float)
# Company (string)
# And a method get_description() which returns a string in the form
# of "Ticker: Company -- $Price"

class Stock:
    def get_description(self):
        return f"{self.ticker}: {self.company} -- ${self.price}"

  
    def __init__(self, ticker, price, company):
        self.ticker = ticker
        self.price = price
        self.company = company
```

## References