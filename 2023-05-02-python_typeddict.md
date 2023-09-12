---
title: Python TypedDict defectiveness regarding immutable object key and arbitrary str keys
layout: default
date: 2023-05-02 00:00:00
categories: category
tags:
- GitHubPages
---

Python accepts any immutable object as dictionary keys, such as datetime.datetime or int.  
However, how do you define TypedDict type hints about immutable object keys and arbitrary str keys?

# Example
```python
from typing import TypedDict
import datetime
import re

class Immutable_Object_Keys(TypedDict):
    datetime.datetime: int  # how do you define types on datetime.datetime objects?
    any_intergers: int  # how do you define types on int objects?
    r'\d\d\d\d': int  # how do you define types on any 4-digits str keys?
  
sample_dict:Immutable_Object_Keys = {
    datetime.datetime.now():1,
    datetime.datetime(2023,5,1,0,0):2,
    3:3,
    9:9,
    '2023':6,
    '2022':5
}
```