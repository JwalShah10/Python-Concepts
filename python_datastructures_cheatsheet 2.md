# Python Data Structures Cheat Sheet

This cheat sheet provides a quick reference for common Python data structures.

## Core Data Structures

### Lists

Mutable, ordered sequences of elements.

**Creation:**
```python
my_list = [1, 2, "three", 4.0]
```

**Common Operations:**
- `my_list.append(5)`: Add an item to the end.
- `my_list.insert(0, "zero")`: Insert an item at a specific index.
- `my_list.remove("three")`: Remove the first occurrence of an item.
- `my_list.pop()`: Remove and return the last item.
- `my_list[0]`: Access an item by index.
- `my_list[1:3]`: Slice a list.
- `len(my_list)`: Get the length of the list.

### Tuples

Immutable, ordered sequences of elements.

**Creation:**
```python
my_tuple = (1, 2, "three", 4.0)
```

**Common Operations:**
- `my_tuple[0]`: Access an item by index.
- `my_tuple[1:3]`: Slice a tuple.
- `len(my_tuple)`: Get the length of the tuple.

### Dictionaries

Mutable, unordered collections of key-value pairs.

**Creation:**
```python
my_dict = {"name": "Alice", "age": 30}
```

**Common Operations:**
- `my_dict["age"] = 31`: Add or update a key-value pair.
- `del my_dict["age"]`: Delete a key-value pair.
- `my_dict.get("name")`: Get the value for a key (returns `None` if key not found).
- `my_dict.keys()`: Get a view of all keys.
- `my_dict.values()`: Get a view of all values.
- `my_dict.items()`: Get a view of all key-value pairs.

### Sets

Mutable, unordered collections of unique elements.

**Creation:**
```python
my_set = {1, 2, 3, 4}
```

**Common Operations:**
- `my_set.add(5)`: Add an element.
- `my_set.remove(3)`: Remove an element (raises `KeyError` if not found).
- `my_set.discard(2)`: Remove an element if it is a member.
- `set1.union(set2)`: Return a new set with elements from both sets.
- `set1.intersection(set2)`: Return a new set with elements common to both sets.
