1. Why do we use NumPy?
Simple meaning

NumPy = Numerical Python

We use NumPy mainly when we need to work with numbers, arrays, matrices, and mathematical calculations.

Without NumPy, Python lists can do basic calculations, but NumPy makes numerical operations much easier and faster.

Example without NumPy
numbers = [1, 2, 3, 4, 5]

result = []

for x in numbers:
    result.append(x * 2)

print(result)

Output:

[2, 4, 6, 8, 10]

===

With NumPy:

import numpy as np

numbers = np.array([1, 2, 3, 4, 5])

result = numbers * 2

print(result)

Output:

[ 2  4  6  8 10]

===

Why NumPy?

| Reason                  | Meaning                                  |
| ----------------------- | ---------------------------------------- |
| Fast                    | Numerical operations are very fast       |
| Arrays                  | Handles large arrays efficiently         |
| Mathematical operations | Easy calculations on entire arrays       |
| Less code               | No need for many loops                   |
| Matrices                | Useful for 2D and multi-dimensional data |
| Data Science            | Used heavily with Pandas, ML, AI         |
| Machine Learning        | Many ML algorithms use NumPy internally  |


==

NumPy is a Python library used for numerical computing. 

It provides efficient multidimensional arrays and mathematical functions for performing fast operations on large amounts of numerical data.

====
