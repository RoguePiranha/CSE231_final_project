# STACKS

## - Introduction

A Stack is a linear data structure that follows a particular order in which operations are performed. The order may be LIFO(Last In First Out) or FILO(First In Last Out). Mainly the following three basic operations are performed in the stack:

- Push: Adds an item in the stack. If the stack is full, then it is said to be an Overflow condition.
- Pop: Removes an item from the stack. The items are popped in the reversed order in which they are pushed. If the stack is empty, then it is said to be an Underflow condition.
- Peek or Top: Returns the top element of the stack.
- isEmpty: Returns true if the stack is empty, else false.

## - Understanding Stacks

Think of a stack of books. You can only take a book from the top of the stack (pop operation), and when you add a new book, it always goes on top (push operation). This is the principle of a Stack in programming as well.

## - Implementing a Stack in Python

In Python, we can use the built-in data type 'list' to simulate a Stack. Here's how:

```python
stack = []  # create an empty stack

# push operation
stack.append('A')  # stack is now: ['A']
stack.append('B')  # stack is now: ['A', 'B']
stack.append('C')  # stack is now: ['A', 'B', 'C']

# pop operation
print(stack.pop())  # prints: 'C'
print(stack.pop())  # prints: 'B'
print(stack.pop())  # prints: 'A'
```

## - Stack Operations (Push, Pop, Peek)

In the above example, we used the 'append' method for the push operation and 'pop' method for the pop operation. To implement the peek operation (get the top item of the stack without removing it), we can use list indexing:

```python
stack.append('A')
stack.append('B')
print(stack[-1])  # prints: 'B'
```

## - Example

Let's use a stack to check for balanced parentheses in an expression:

```python
def is_balanced(expression):
    stack = []
    for char in expression:
        if char in "([{":
            stack.append(char)
        else:
            if not stack:
                return False
            current_char = stack.pop()
            if current_char == '(':
                if char != ")":
                    return False
            if current_char == '[':
                if char != "]":
                    return False
            if current_char == '{':
                if char != "}":
                    return False
    if stack:
        return False
    return True

# test the function
print(is_balanced("(a[b]{c})"))  # prints: True
print(is_balanced("(a[b]{c)"))  # prints: False
```

## - Problem to Solve

Now it's your turn! Write a function that takes a string as input and returns True if the string is a palindrome and False otherwise. A palindrome is a word, number, phrase, or other sequence of characters which reads the same backward as forward, such as madam or racecar.

## - Possible Solution


```python
def is_palindrome(string):
    stack = []
    for char in string:
        stack.append(char)
    for char in string:
        if char != stack.pop():
            return False
    return True
```
