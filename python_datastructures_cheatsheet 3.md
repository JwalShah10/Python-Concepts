# Python Data Structures Cheat Sheet

This cheat sheet provides a quick reference for common Python data structures.

## Core Data Structures

### Lists

Mutable, ordered sequences of elements.

**Creation and Operations:**
```python
# Creation
my_list = [1, 2, "three", 4.0]
print(my_list)
# Output: [1, 2, 'three', 4.0]

# Append
my_list.append(5)
print(my_list)
# Output: [1, 2, 'three', 4.0, 5]

# Insert
my_list.insert(0, "zero")
print(my_list)
# Output: ['zero', 1, 2, 'three', 4.0, 5]

# Remove
my_list.remove("three")
print(my_list)
# Output: ['zero', 1, 2, 4.0, 5]

# Pop
print(my_list.pop())
# Output: 5
print(my_list)
# Output: ['zero', 1, 2, 4.0]

# Access by index
print(my_list[0])
# Output: 'zero'

# Slicing
print(my_list[1:3])
# Output: [1, 2]

# Length
print(len(my_list))
# Output: 4

# Sort (on a list of numbers)
num_list = [4, 1, 3, 2]
num_list.sort()
print(num_list)
# Output: [1, 2, 3, 4]

# Reverse
num_list.reverse()
print(num_list)
# Output: [4, 3, 2, 1]
```

### Tuples

Immutable, ordered sequences of elements.

**Creation and Operations:**
```python
# Creation
my_tuple = (1, 2, "three", 4.0)
print(my_tuple)
# Output: (1, 2, 'three', 4.0)

# Access by index
print(my_tuple[0])
# Output: 1

# Slicing
print(my_tuple[1:3])
# Output: (2, 'three')

# Length
print(len(my_tuple))
# Output: 4
```

### Dictionaries

Mutable collections of key-value pairs. Insertion order is preserved in Python 3.7+.

**Creation and Operations:**
```python
# Creation
my_dict = {"name": "Alice", "age": 30}
print(my_dict)
# Output: {'name': 'Alice', 'age': 30}

# Add/Update
my_dict["age"] = 31
my_dict["city"] = "New York"
print(my_dict)
# Output: {'name': 'Alice', 'age': 31, 'city': 'New York'}

# Delete
del my_dict["age"]
print(my_dict)
# Output: {'name': 'Alice', 'city': 'New York'}

# Pop
city = my_dict.pop("city")
print(city)
# Output: New York
print(my_dict)
# Output: {'name': 'Alice'}

# Get
print(my_dict.get("name"))
# Output: Alice
print(my_dict.get("country")) # Returns None
# Output: None

# Keys, Values, Items
my_dict["age"] = 31 # Add age back
print(list(my_dict.keys()))
# Output: ['name', 'age']
print(list(my_dict.values()))
# Output: ['Alice', 31]
print(list(my_dict.items()))
# Output: [('name', 'Alice'), ('age', 31)]
```

### Sets

Mutable, unordered collections of unique elements.

**Creation and Operations:**
```python
# Creation
my_set = {1, 2, 3, 4}
print(my_set)
# Output: {1, 2, 3, 4}

# Add
my_set.add(5)
print(my_set)
# Output: {1, 2, 3, 4, 5}

# Remove
my_set.remove(3)
print(my_set)
# Output: {1, 2, 4, 5}

# Discard
my_set.discard(2)
print(my_set)
# Output: {1, 4, 5}

# Set Operations
set1 = {1, 2, 3}
set2 = {3, 4, 5}

# Union
print(set1.union(set2))
# Output: {1, 2, 3, 4, 5}

# Intersection
print(set1.intersection(set2))
# Output: {3}

# Difference
print(set1.difference(set2))
# Output: {1, 2}

# Symmetric Difference
print(set1.symmetric_difference(set2))
# Output: {1, 2, 4, 5}
```

## Advanced Data Structures

### Strings

Immutable sequences of characters.

**Creation and Operations:**
```python
# Creation
my_string = "  Hello, World!  "
print(my_string)
# Output: '  Hello, World!  '

# Access by index
print(my_string[2])
# Output: 'H'

# Slicing
print(my_string[2:7])
# Output: 'Hello'

# Length
print(len(my_string))
# Output: 17

# Case conversion
print(my_string.upper())
# Output: '  HELLO, WORLD!  '
print(my_string.lower())
# Output: '  hello, world!  '

# Strip whitespace
print(my_string.strip())
# Output: 'Hello, World!'

# Split
my_string_clean = my_string.strip()
print(my_string_clean.split(','))
# Output: ['Hello', ' World!']

# Join
words = ["Python", "is", "fun"]
print(" ".join(words))
# Output: Python is fun
```

### `collections.namedtuple`

Tuple subclasses with named fields.

**Creation and Operations:**
```python
from collections import namedtuple

Point = namedtuple("Point", ["x", "y"])
p = Point(10, 20)
print(p)
# Output: Point(x=10, y=20)

# Access by name
print(p.x)
# Output: 10

# Access by index
print(p[0])
# Output: 10
```

### `collections.defaultdict`

A dictionary subclass that calls a factory function for missing keys.

**Creation and Operations:**
```python
from collections import defaultdict

# Using int as the default factory
dd = defaultdict(int)
dd["a"] = 1
print(dd["a"])
# Output: 1

# Accessing a missing key creates it with the default value (0 for int)
print(dd["b"])
# Output: 0
print(dd)
# Output: defaultdict(<class 'int'>, {'a': 1, 'b': 0})

# Using list as the default factory
list_dd = defaultdict(list)
list_dd["a"].append(1)
list_dd["a"].append(2)
print(list_dd["a"])
# Output: [1, 2]
print(list_dd["b"]) # Creates an empty list for 'b'
# Output: []
print(list_dd)
# Output: defaultdict(<class 'list'>, {'a': [1, 2], 'b': []})
```

### `collections.Counter`

A dictionary subclass for counting hashable objects.

**Creation and Operations:**
```python
from collections import Counter

# Create a counter from a string
c = Counter("gallahad")
print(c)
# Output: Counter({'a': 3, 'l': 2, 'g': 1, 'h': 1, 'd': 1})

# Get the count of an element
print(c["a"])
# Output: 3

# Get the 2 most common elements
print(c.most_common(2))
# Output: [('a', 3), ('l', 2)]

# Create a counter from a list
word_counts = Counter(["apple", "banana", "apple", "orange", "banana", "apple"])
print(word_counts["apple"])
# Output: 3
print(word_counts)
# Output: Counter({'apple': 3, 'banana': 2, 'orange': 1})
```

### `collections.deque`

A list-like container with fast appends and pops on either end.

**Creation and Operations:**
```python
from collections import deque

# Creation
d = deque(["a", "b", "c"])
print(d)
# Output: deque(['a', 'b', 'c'])

# Append to the right
d.append("d")
print(d)
# Output: deque(['a', 'b', 'c', 'd'])

# Append to the left
d.appendleft("z")
print(d)
# Output: deque(['z', 'a', 'b', 'c', 'd'])

# Pop from the right
print(d.pop())
# Output: 'd'
print(d)
# Output: deque(['z', 'a', 'b', 'c'])

# Pop from the left
print(d.popleft())
# Output: 'z'
print(d)
# Output: deque(['a', 'b', 'c'])
```
