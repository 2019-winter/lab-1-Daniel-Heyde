---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Name(s)
Daniel Heyde


**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.

## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**


Is there a good guide for NumPy in particular?



## Exercises 1-7
For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.


## Exercise 1

```python
import numpy as np
a = np.ones((6, 4), dtype=int) * 2
a
```

## Exercise 2

```python
b = np.ones((6, 4), dtype=int)
np.fill_diagonal(b, 3)
b
```

## Exercise 3

```python
a * b
# * is element by element multiplication
# dot is matrix multiplication so the inner dimensions must match
```

## Exercise 4

```python
print(np.dot(a.transpose(), b))
print(np.dot(a, b.transpose()))

# the resulting arrays are of different sizes because the 
# dot product's result takes on a shape based on the outer dimensions
```

## Exercise 5

```python
def old_macdonald():
    print("EIEIO")
    
old_macdonald()
```

## Exercise 6

```python
import random

def print_rand_arr():
    arr = []
    for i in range(random.randint(1, 10)):
        arr.append(random.randint(-15, 15))
    print(arr)
    print(np.mean(arr))
    print(np.sum(arr))
    return arr

print_rand_arr()
print_rand_arr()
print_rand_arr()
```

## Exercise 7

```python
def count_ones(arr):
    count = 0
    for i in range(len(arr)):
        if (arr[i] == 1):
            count+=1
    return count

def count_ones_where(arr):
    ones = np.where(1, arr, None)
    return len(ones)

print(count_ones([1, 2, 1, 3, 4, 1]))
print(count_ones_where([1, 2, 1, 3, 4, 1]))
```

## Excercises 8-???
While the Marsland book avoids using another popular package called Pandas, we will use it at times throughout this course. Please read and study [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html) before proceeding to any of the exercises below.


## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
import pandas as pd
a = pd.DataFrame(np.ones((6, 4)) * 2)
```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
b = pd.DataFrame(np.ones((6, 4)), dtype=int)
b.iloc[range(4), range(4)] = 3
b
```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.

```python
pd.DataFrame.multiply(a, b)
# same answer as above, the matrices sizes arent compatible for dot product matrix multiplication
```

## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
def count_ones(df):
    count = 0
    for i in range(len(df)):
        if (df.iloc[i, 0] == 1):
            count+=1
    return count

def count_ones_where(df):
    ones = df.where(df == 1, 0)
    return ones.sum()[0]

print(count_ones(pd.DataFrame([1, 2, 1, 3, 4, 1])))
print(count_ones_where(pd.DataFrame([1, 2, 1, 3, 4, 1])))
```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = pd.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
titanic_df.name
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
## YOUR SOLUTION HERE
titanic_df.set_index('sex',inplace=True)
titanic_df.loc['female']
len(titanic_df.loc['female'])
```

## Exercise 14
How do you reset the index?

```python
titanic_df.reset_index()
```

```python

```
