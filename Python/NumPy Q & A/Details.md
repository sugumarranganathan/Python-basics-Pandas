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

2. Compute min/max for each row of a NumPy 2D array

Consider:

import numpy as np

arr = np.array([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
])

Our array is:

1  2  3
4  5  6
7  8  9

We want minimum and maximum for each row.

min_per_row = np.amin(arr, axis=1)
max_per_row = np.amax(arr, axis=1)

print(min_per_row)
print(max_per_row)

Output:

[1 4 7]
[3 6 9]

===

Why axis=1?

This is very important.

        columns
       ↓  ↓  ↓
       1  2  3
       4  5  6
       7  8  9
       ↑
      rows

For each row, we move across the columns.

Therefore:

axis=1

means operate across columns / calculate separately for each row.

Remember
Code	Meaning
axis=0	Calculate for each column
axis=1	Calculate for each row

Modern NumPy code can also use:

np.min(arr, axis=1)
np.max(arr, axis=1)

====

3. What is ndarray in NumPy?

ndarray means:

N-dimensional array

It is the main array object in NumPy.

Example:

import numpy as np

arr = np.array([10, 20, 30])

Here:

type(arr)

gives:

numpy.ndarray
Why "N-dimensional"?

Because it can represent different dimensions.

3. What is ndarray in NumPy?

ndarray means:

N-dimensional array

It is the main array object in NumPy.

Example:

import numpy as np

arr = np.array([10, 20, 30])

Here:

type(arr)

gives:

numpy.ndarray
Why "N-dimensional"?

Because it can represent different dimensions.

====

4. How do you convert a Pandas DataFrame into a NumPy array?

Suppose:

import pandas as pd

df = pd.DataFrame({
    "Name": ["John", "Mary"],
    "Age": [25, 30]
})

DataFrame:

   Name  Age
0  John   25
1  Mary   30

You can convert it to NumPy using:

array = df.values

Or, preferably:

array = df.to_numpy()
Example
array = df.to_numpy()

print(array)

Output:

[['John' 25]
 ['Mary' 30]]
Important

Today, I recommend remembering:

df.to_numpy()

rather than only:

df.values

====

5. Difference between ndarray and array in NumPy

This question can be confusing.

ndarray is the actual NumPy array class/type.

np.array() is a function used to create an ndarray.

Example:

arr = np.array([1, 2, 3])

Here:

np.array()       → function
arr              → ndarray object

You can check:

type(arr)

Output:

<class 'numpy.ndarray'>
Think of it like this

| Term         | Meaning                        |
| ------------ | ------------------------------ |
| `np.array()` | Function that creates an array |
| `ndarray`    | NumPy's array object/class     |


So the original material saying "array is just shorthand for ndarray" is a little oversimplified.

====

6. Convert an array of indices to one-hot encoding

This is very important in Machine Learning.

Suppose we have:

indices = [1, 2, 0, 1]

And there are 3 classes:

0
1
2

One-hot encoding represents each class using 0 and 1.

Mapping
Class 0 → [1, 0, 0]

Class 1 → [0, 1, 0]

Class 2 → [0, 0, 1]

Therefore:

[1, 2, 0, 1]

becomes:

[
 [0, 1, 0],
 [0, 0, 1],
 [1, 0, 0],
 [0, 1, 0]
]

====

Code
import numpy as np

indices = [1, 2, 0, 1]
num_classes = 3

one_hot = np.eye(num_classes)[indices]

print(one_hot)

Output:

[[0. 1. 0.]
 [0. 0. 1.]
 [1. 0. 0.]
 [0. 1. 0.]]

What does np.eye(3) do?
np.eye(3)

creates:

1 0 0
0 1 0
0 0 1

Then:

[indices]

selects the required rows.

=====

7. What is vectorization in NumPy?

This is very important.

Without vectorization

Suppose we want to multiply every number by 2.

numbers = [1, 2, 3, 4, 5]

result = []

for x in numbers:
    result.append(x * 2)

We use a loop.

=====

With NumPy vectorization
import numpy as np

numbers = np.array([1, 2, 3, 4, 5])

result = numbers * 2

No explicit loop.

Output:

[ 2  4  6  8 10]

====

So what is vectorization?

Vectorization means performing an operation on an entire array at once instead of explicitly processing each element using a Python loop.

Why is it useful?

| Traditional loop                             | NumPy vectorization        |
| -------------------------------------------- | -------------------------- |
| More code                                    | Less code                  |
| Python loop                                  | Optimized array operations |
| Usually slower for large numerical workloads | Usually faster             |
| Element-by-element                           | Whole-array operation      |

====

8. Convert a numeric array to categorical/text values

Suppose:

arr = np.array([0, 1, 2, 1, 0])

We want:

0 → "Low"
1 → "Medium"
2 → "High"

One simple NumPy approach is:

categories = np.array(["Low", "Medium", "High"])

result = categories[arr]

print(result)

Output:

['Low' 'Medium' 'High' 'Medium' 'Low']

====

numeric → text mapping

Another approach using Pandas
import pandas as pd

arr = np.array([0, 1, 2, 1, 0])

result = pd.Categorical(
    arr,
    categories=[0, 1, 2]
)

print(result)

====

9. How do you reverse a NumPy array?

Original:

arr = np.array([1, 2, 3, 4, 5])

Reverse:

arr[::-1]

Output:

[5 4 3 2 1]

===

What does [::-1] mean?

Python slicing:

[start : stop : step]

Here:

[::-1]

means:

start → default
stop  → default
step  → -1

-1 means move backwards.

====

0. Difference between test[:,0] and test[:,[0]]

This is a very important interview question.

Suppose:

test = np.array([
    [10, 20, 30],
    [40, 50, 60],
    [70, 80, 90]
])
test[:, 0]
test[:, 0]

Output:

[10 40 70]

Shape:

(3,)

It becomes a 1D array.

====

test[:, [0]]
test[:, [0]]

Output:

[[10]
 [40]
 [70]]

Shape:

(3, 1)

It remains a 2D array.

=====

Compare

| Code           | Output shape | Type |
| -------------- | -----------: | ---- |
| `test[:, 0]`   |       `(3,)` | 1D   |
| `test[:, [0]]` |      `(3,1)` | 2D   |


Why does this matter?

Suppose you're working with Machine Learning.

Many ML functions expect:

(number of samples, number of features)

If you have one feature and 3 samples:

(3, 1)

is often what you need.

So:

test[:, [0]]

preserves the 2D structure.

=====

11. Difference between NumPy arrays and matrices

Historically NumPy had a special matrix type:

np.matrix()

The important difference is:

NumPy array
a = np.array([
    [1, 2],
    [3, 4]
])
Matrix
m = np.matrix([
    [1, 2],
    [3, 4]
])

The * operator behaves differently.

Array
a * a

means element-by-element multiplication:

1×1   2×2
3×3   4×4

Result:

[[1, 4],
 [9, 16]]

-----

Matrix
m * m

means matrix multiplication.

====

Today, what should you use?

Generally:

Use NumPy arrays (ndarray) rather than np.matrix.

For matrix multiplication with arrays, use:

a @ a

or:

np.matmul(a, a)

So remember:

a * b

→ element-wise multiplication

a @ b

→ matrix multiplication

====

12. np.mean() vs np.average()

Both can calculate an average.

np.mean()
arr = np.array([10, 20, 30])

np.mean(arr)

Output:

20.0

It calculates the normal arithmetic mean.

Formula:

(10 + 20 + 30) / 3
= 20

======

np.average()

It can also calculate the normal average:

np.average(arr)

Output:

20.0

But it has an additional feature:

=====

weights.

Example:

arr = np.array([10, 20, 30])

weights = np.array([1, 1, 3])

result = np.average(arr, weights=weights)

print(result)

The value 30 gets more importance because its weight is 3.

====

Difference

| `np.mean()`          | `np.average()`            |
| -------------------- | ------------------------- |
| Calculates mean      | Calculates average        |
| No weights parameter | Supports weights          |
| Simple average       | Weighted average possible |


np.mean() calculates the arithmetic mean, 
while np.average() can calculate a weighted average using the weights parameter.

====

13. flatten() vs ravel()

Suppose:

arr = np.array([
    [1, 2],
    [3, 4]
])

We want:

[1 2 3 4]

Both can do this.

flatten()
result = arr.flatten()

Output:

[1 2 3 4]

flatten() creates a copy.

====

ravel()
result = arr.ravel()

Output:

[1 2 3 4]

ravel() returns a view when possible, rather than always making a copy.

====

Why does this matter?

Suppose:

arr = np.array([
    [1, 2],
    [3, 4]
])

x = arr.ravel()

x[0] = 100

Because x may be a view of arr, the original array may also change:

[[100   2]
 [  3   4]]

With:

x = arr.flatten()

x is a separate copy, so changing x does not change arr.

Easy memory trick
flatten → COPY
ravel   → VIEW when possible

====

| #  | Question              | Key answer                                                          |
| -- | --------------------- | ------------------------------------------------------------------- |
| 1  | Why NumPy?            | Fast numerical computing and arrays                                 |
| 2  | Min/max each row      | `axis=1`                                                            |
| 3  | ndarray               | N-dimensional NumPy array                                           |
| 4  | DataFrame → NumPy     | `df.to_numpy()`                                                     |
| 5  | ndarray vs array      | `np.array()` creates an `ndarray`                                   |
| 6  | One-hot encoding      | `np.eye(num_classes)[indices]`                                      |
| 7  | Vectorization         | Operations on whole arrays without explicit Python loops            |
| 8  | Numeric → categorical | Map numbers to category labels                                      |
| 9  | Reverse array         | `arr[::-1]`                                                         |
| 10 | `[:,0]` vs `[:,[0]]`  | 1D vs 2D                                                            |
| 11 | Array vs matrix       | Prefer `ndarray`; `*` is element-wise, `@` is matrix multiplication |
| 12 | `mean` vs `average`   | `average` supports weights                                          |
| 13 | `flatten` vs `ravel`  | `flatten` copies; `ravel` views when possible                       |

=====

axis=0  → column-wise result
axis=1  → row-wise result

[:, 0]  → 1D
[:, [0]] → 2D

*       → element-wise multiplication
@       → matrix multiplication

flatten → copy
ravel   → view when possible

mean    → normal mean
average → weighted mean possible

=====







 
