# SETS <!-- omit in toc -->

## Table of Contents <!-- omit in toc -->

- [Introduction](#introduction)
- [Understanding Sets and Hashing](#understanding-sets-and-hashing)
- [Creating and Accessing Sets](#creating-and-accessing-sets)
- [Set Operations (Union, Intersection, Difference)](#set-operations-union-intersection-difference)
- [Example](#example)
- [Problem to Solve](#problem-to-solve)
- [Possible Solution](#possible-solution)

## Introduction

A Set is an unordered collection data type that is iterable, mutable, and has no duplicate elements. Python’s set class represents the mathematical notion of a set. The major advantage of using a set, as opposed to a list, is that it has a highly optimized method for checking whether a specific element is contained in the set. This is achieved through a process called hashing.

## Understanding Sets and Hashing

Sets are used when the existence of an object in a collection is more important than the order or how many times it occurs. Using sets can eliminate duplicate entries. Set objects also support mathematical operations like union, intersection, difference, and symmetric difference.

Hashing is the process of mapping an item to an index location using a hashing function. Since the function does not require searching through the data structure, hashing can result in an O(1) performance in the best case. However, hashing can lead to conflicts where two items result in the same hash value. There are methods to resolve these conflicts, such as open addressing and chaining.

## Creating and Accessing Sets

In Python, sets are written with curly brackets. Here's how:

```python
# create a set
fruits = {"apple", "banana", "cherry"}

# access items
for x in fruits:
  print(x)  # prints each fruit in the set
```

## Set Operations (Union, Intersection, Difference)

![Venn diagram of union, intersection, and difference set operations](/images/sets_uid.png)
<small><em><sub>Image credit: AJ201, Stack Overflow</sub></em></small>

Sets can perform operations such as union and intersection:

``` python
# create two sets
fruits = {"apple", "banana", "cherry"}
citrus = {"orange", "lemon", "grapefruit", "banana"}

# union operation
print(fruits.union(citrus))  # prints: {'orange', 'grapefruit', 'cherry', 'apple', 'lemon', 'banana'}

# intersection operation
print(fruits.intersection(citrus))  # prints: {'banana'}

# difference operation
print(fruits.difference(citrus))  # prints: {'apple', 'cherry'}
```

## Example

Let's use a set to find the unique elements in a list:

```python
# create a list with duplicate elements
numbers = [1, 2, 2, 3, 4, 4, 5, 6, 6, 7, 7, 8, 9, 9]

# convert the list to a set to remove duplicates
unique_numbers = set(numbers)

print(unique_numbers)  # prints: {1, 2, 3, 4, 5, 6, 7, 8, 9}
```

## Problem to Solve

Now it's your turn! Given two lists, find the elements that are common to both lists (the intersection). Try to solve this problem using sets.

## Possible Solution

```python
# create two lists
list1 = [1, 2, 3, 4, 5, 6, 7, 8, 9]
list2 = [2, 4, 6, 8, 10, 12, 14]

# convert lists to sets
set1 = set(list1)
set2 = set(list2)

# find the intersection
intersection = set1.intersection(set2)

print(intersection)  # prints: {8, 2, 4, 6}
```

<p align="center">
  <a href="welcome.md">Back to Home</a> &nbsp; | &nbsp; <a href="trees.md">Next: Trees</a>
</p>