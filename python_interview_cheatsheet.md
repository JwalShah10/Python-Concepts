# Python Beginner Interview Cheatsheet

This cheatsheet contains a collection of common Python interview questions for beginners, along with explanations and code examples.

---

### Q: What are the basic data types in Python?

**A:** Python has several built-in data types. The most common ones are:

*   **Text Type:** `str`
*   **Numeric Types:** `int`, `float`
*   **Sequence Types:** `list`, `tuple`
*   **Mapping Type:** `dict`
*   **Set Types:** `set`
*   **Boolean Type:** `bool`

#### Code Explanation and Output

```python
# String
my_string = "Hello"
print(f"'{my_string}' is a {type(my_string)}")
# Output: 'Hello' is a <class 'str'>

# Integer
my_int = 10
print(f"{my_int} is an {type(my_int)}")
# Output: 10 is an <class 'int'>

# Float
my_float = 10.5
print(f"{my_float} is a {type(my_float)}")
# Output: 10.5 is a <class 'float'>

# List
my_list = [1, 2, 3]
print(f"{my_list} is a {type(my_list)}")
# Output: [1, 2, 3] is a <class 'list'>

# Tuple
my_tuple = (1, 2, 3)
print(f"{my_tuple} is a {type(my_tuple)}")
# Output: (1, 2, 3) is a <class 'tuple'>

# Dictionary
my_dict = {'a': 1, 'b': 2}
print(f"{my_dict} is a {type(my_dict)}")
# Output: {'a': 1, 'b': 2} is a <class 'dict'>

# Set
my_set = {1, 2, 3}
print(f"{my_set} is a {type(my_set)}")
# Output: {1, 2, 3} is a <class 'set'>

# Boolean
my_bool = True
print(f"{my_bool} is a {type(my_bool)}")
# Output: True is a <class 'bool'>
```

---

### Q: What is the difference between a list and a tuple?

**A:** The main difference is that **lists are mutable**, while **tuples are immutable**.

*   **Mutable** means that you can change the object after it has been created (e.g., add, remove, or change elements).
*   **Immutable** means that you cannot change the object after it has been created.

Because they are immutable, tuples are hashable, which means they can be used as keys in a dictionary. Lists cannot. Tuples are also generally faster than lists.

#### Code Explanation and Output

```python
# Lists are mutable
my_list = [1, 2, 3]
print(f"Original list: {my_list}")
my_list[0] = 99
print(f"Modified list: {my_list}")

# Tuples are immutable
my_tuple = (1, 2, 3)
print(f"Original tuple: {my_tuple}")
try:
    my_tuple[0] = 99
except TypeError as e:
    print(f"Error when modifying tuple: {e}")
```

#### Code Output

```
Original list: [1, 2, 3]
Modified list: [99, 2, 3]
Original tuple: (1, 2, 3)
Error when modifying tuple: 'tuple' object does not support item assignment
```

---

### Q: What are `*args` and `**kwargs`?

**A:** `*args` and `**kwargs` are special syntax used in function definitions to pass a variable number of arguments to a function.

*   `*args` is used to pass a variable-length, **non-keyworded** argument list. It collects extra positional arguments into a **tuple**.
*   `**kwargs` is used to pass a variable-length, **keyworded** argument list. It collects extra keyword arguments into a **dictionary**.

#### Code Explanation and Output

```python
def my_function(a, b, *args, **kwargs):
    print(f"a: {a}")
    print(f"b: {b}")
    print(f"args: {args}")
    print(f"kwargs: {kwargs}")

# Call the function with various arguments
my_function(1, 2, 3, 4, 5, name="Jules", city="Paris")
```

#### Code Output

```
a: 1
b: 2
args: (3, 4, 5)
kwargs: {'name': 'Jules', 'city': 'Paris'}
```
---

### Q: What is a list comprehension?

**A:** A list comprehension is a concise and readable way to create a new list from an existing iterable (like a list, tuple, or range). The syntax is `[expression for item in iterable if condition]`.

#### Code Explanation and Output

```python
# Traditional way to create a list of squares
squares = []
for i in range(5):
    squares.append(i * i)
print(f"Traditional way: {squares}")

# Using a list comprehension
squares_comp = [i * i for i in range(5)]
print(f"List comprehension: {squares_comp}")

# List comprehension with a condition
even_squares = [i * i for i in range(10) if i % 2 == 0]
print(f"Even squares: {even_squares}")
```

#### Code Output

```
Traditional way: [0, 1, 4, 9, 16]
List comprehension: [0, 1, 4, 9, 16]
Even squares: [0, 4, 16, 36, 64]
```
---

### Q: What is the difference between `==` and `is`?

**A:**
*   The `==` operator compares the **values** of two objects (value equality).
*   The `is` operator checks if two variables point to the **same object in memory** (identity equality).

#### Code Explanation and Output

```python
list_a = [1, 2, 3]
list_b = [1, 2, 3]
list_c = list_a

# == compares values
print(f"list_a == list_b: {list_a == list_b}")  # True, because values are the same

# is compares memory location
print(f"list_a is list_b: {list_a is list_b}")  # False, because they are different objects in memory
print(f"list_a is list_c: {list_a is list_c}")  # True, because list_c points to the same object as list_a
```

#### Code Output
```
list_a == list_b: True
list_a is list_b: False
list_a is list_c: True
```
---

### Q: What is a lambda function?

**A:** A lambda function is a small, anonymous function defined with the `lambda` keyword. It can take any number of arguments, but can only have one expression. The syntax is `lambda arguments: expression`.

They are often used when a simple function is needed for a short period, such as an argument to a higher-order function like `map()`, `filter()`, or `sorted()`.

#### Code Explanation and Output

```python
# A regular function
def add(x, y):
    return x + y
print(f"Regular function: {add(2, 3)}")

# A lambda function
add_lambda = lambda x, y: x + y
print(f"Lambda function: {add_lambda(2, 3)}")

# Using lambda with sorted()
points = [(1, 2), (3, 1), (5, 4), (2, 0)]
sorted_points = sorted(points, key=lambda point: point[1])
print(f"Points sorted by the second element: {sorted_points}")
```

#### Code Output
```
Regular function: 5
Lambda function: 5
Points sorted by the second element: [(2, 0), (3, 1), (1, 2), (5, 4)]
```
