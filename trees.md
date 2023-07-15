# TREES <!-- omit in toc -->

## Table of Contents <!-- omit in toc -->

- [Introduction](#introduction)
- [Understanding Trees (Binary Trees)](#understanding-trees-binary-trees)
- [Implementing a Tree in Python](#implementing-a-tree-in-python)
- [Tree Traversal Methods (In-order, Pre-order, Post-order)](#tree-traversal-methods-in-order-pre-order-post-order)
  - [In-order Traversal](#in-order-traversal)
  - [Pre-order Traversal](#pre-order-traversal)
  - [Post-order Traversal](#post-order-traversal)
- [Example](#example)
- [Problem to Solve](#problem-to-solve)
- [Possible Solution](#possible-solution)

## Introduction

Trees are a type of data structure that, like linked lists, connect nodes together using pointers. However, unlike linked lists, a tree can connect to multiple different nodes. In this tutorial we'll go over the basics of trees, how to implement them in Python, and how to traverse them.

## Understanding Trees (Binary Trees)

A binary tree is a tree that links to no more than two other nodes. The top node is called the root node. The nodes that connect to no other nodes are called leaf nodes. A node that has connected nodes is called a parent node. The nodes connected to the parent are called child nodes. The nodes to the left and right of any parent node form a subtree. There is always only one root node. It is common for child nodes to also point back up to the parent node, similar to a linked list.

![Visualization of Basic Terminology of Binary Search Trees.](/images/binary_tree.png)
<small><em><sub>Image credit: Towards Data Science</sub></em></small>

## Implementing a Tree in Python

In Python, a binary tree can be implemented as a class with a nested Node class. The Node class contains three attributes: data (the value), left (pointer to the left node), and right (pointer to the right node). The Tree class contains methods for inserting data into the tree and traversing the tree.

```python
class BST:
    class Node:
        def __init__(self, data):
            self.data = data
            self.left = None
            self.right = None

    def __init__(self):
        self.root = None
```

## Tree Traversal Methods (In-order, Pre-order, Post-order)

Tree traversal is the process of visiting (checking or updating) each node in a tree data structure, exactly once. Unlike linked lists or arrays which have a linear order, trees may be traversed in multiple ways. They can be traversed in depth-first or breadth-first order. Here, we will discuss three types of depth-first orders: In-order, Pre-order, and Post-order.

### In-order Traversal

In an in-order traversal, the left subtree is visited first, then the root and later the right subtree.

```python
def _traverse_forward(self, node):
    if node is not None:
        yield from self._traverse_forward(node.left)
        yield node.data
        yield from self._traverse_forward(node.right)
```

### Pre-order Traversal

In a pre-order traversal, the root node is visited first, then the left subtree and finally the right subtree.

```python
def preorder_traversal(self, node, visited_nodes):
    if node is not None:
        visited_nodes.append(node.data)
        self.preorder_traversal(node.left, visited_nodes)
        self.preorder_traversal(node.right, visited_nodes)
    return visited_nodes
```

### Post-order Traversal

In a post-order traversal, the root node is the last to be visited. First we traverse the left subtree, then the right subtree and finally the root node.

```python
def postorder_traversal(self, node, visited_nodes):
    if node is not None:
        self.postorder_traversal(node.left, visited_nodes)
        self.postorder_traversal(node.right, visited_nodes)
        visited_nodes.append(node.data)
    return visited_nodes
```

## Example

Let's take an example of a binary search tree. We will insert the following numbers into our tree: 15, 10, 24, 3, 14, 33. The resulting tree will look like this:

```markdown
    15
   /  \
 10    24
 / \     \
3   14    33
```

We can traverse this tree in in-order (3, 10, 14, 15, 24, 33), pre-order (15, 10, 3, 14, 24, 33), or post-order (3, 14, 10, 33, 24, 15).

## Problem to Solve

Now that you understand the basics of binary trees and how to implement them in Python, try to solve the following problem:

Given a binary search tree, write a function to find the second largest number in the tree. You can assume that the tree has at least two nodes.

Remember, in a binary search tree, the largest number is always the rightmost node, and the second largest number is either the parent of the rightmost node (if the rightmost node has no left child), or the rightmost node in the left subtree of the rightmost node (if it exists). Try to solve this problem using the tree traversal methods you've learned.

## Possible Solution

```python
def find_second_largest(bst):
    node = bst.root
    while node:
        # Case: node has right child but the right child has no children, 
        # then the current node is the second largest
        if node.right and not node.right.right and not node.right.left:
            return node.data
        # Case: node has no right child but has left child, 
        # then the largest in the left subtree is the second largest
        elif not node.right and node.left:
            node = node.left
            while node.right:
                node = node.right
            return node.data
        node = node.right
```
