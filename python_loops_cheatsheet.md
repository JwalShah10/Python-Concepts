# Python Loops Cheatsheet

This cheatsheet provides a quick reference for common looping constructs in Python.

## `for` Loops

`for` loops are used for iterating over a sequence (that is either a list, a tuple, a dictionary, a set, or a string).

**1. Iterating over a sequence:**
```python
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)
# Output:
# apple
# banana
# cherry
```

**2. The `range()` function:**
To loop through a set of code a specified number of times, we can use the `range()` function.
```python
# Loop from 0 to 4
for i in range(5):
    print(i)
# Output: 0, 1, 2, 3, 4

# Loop from 2 to 5
for i in range(2, 6):
    print(i)
# Output: 2, 3, 4, 5

# Loop from 0 to 10 with a step of 3
for i in range(0, 11, 3):
    print(i)
# Output: 0, 3, 6, 9
```

**3. Iterating over a string:**
```python
for char in "hello":
    print(char)
# Output:
# h
# e
# l
# l
# o
```

**4. Iterating over dictionary items:**
```python
my_dict = {"name": "Alice", "age": 30}
for key, value in my_dict.items():
    print(f"{key}: {value}")
# Output:
# name: Alice
# age: 30
```

## `while` Loops

`while` loops are used to execute a block of statements as long as a condition is true.

**Basic `while` loop:**
```python
count = 0
while count < 5:
    print(count)
    count += 1
# Output:
# 0
# 1
# 2
# 3
# 4
```

**Using `else` with `while` loop:**
The `else` block is executed when the `while` loop condition becomes false.
```python
count = 0
while count < 3:
    print(count)
    count += 1
else:
    print("Loop finished")
# Output:
# 0
# 1
# 2
# Loop finished
```

## Loop Control Statements

Loop control statements change the execution of a loop from its normal sequence.

**1. `break` statement:**
The `break` statement terminates the loop containing it.
```python
for i in range(5):
    if i == 3:
        break
    print(i)
# Output:
# 0
# 1
# 2
```

**2. `continue` statement:**
The `continue` statement is used to skip the rest of the code inside a loop for the current iteration only.
```python
for i in range(5):
    if i == 3:
        continue
    print(i)
# Output:
# 0
# 1
# 2
# 4
```

**3. `pass` statement:**
The `pass` statement is a null operation; nothing happens when it executes. It is used as a placeholder.
```python
for i in range(5):
    if i == 3:
        pass # Placeholder for future code
    print(i)
# Output:
# 0
# 1
# 2
# 3
# 4
```

**4. `else` in Loops:**
Python loops can have an `else` clause that is executed after the loop finishes, but only if the loop was not terminated by a `break` statement.
```python
for i in range(3):
    print(i)
else:
    print("Loop finished without break")
# Output:
# 0
# 1
# 2
# Loop finished without break

for i in range(5):
    if i == 3:
        break
    print(i)
else:
    print("This will not be printed")
# Output:
# 0
# 1
# 2
```

## List Comprehensions

List comprehensions offer a concise way to create lists. They are often more readable and performant than using a `for` loop.

**Basic list comprehension:**
```python
# Create a list of squares from 0 to 9
squares = [x**2 for x in range(10)]
print(squares)
# Output: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

**List comprehension with a condition:**
```python
# Create a list of even numbers from 0 to 9
evens = [x for x in range(10) if x % 2 == 0]
print(evens)
# Output: [0, 2, 4, 6, 8]
```

**List comprehension with `if-else`:**
```python
# Create a list with 'even' or 'odd' for numbers 0 to 4
labels = ["even" if x % 2 == 0 else "odd" for x in range(5)]
print(labels)
# Output: ['even', 'odd', 'even', 'odd', 'even']
```

**Nested list comprehensions:**
```python
# Create a flattened list from a list of lists
matrix = [[1, 2], [3, 4], [5, 6]]
flattened = [num for row in matrix for num in row]
print(flattened)
# Output: [1, 2, 3, 4, 5, 6]
```
