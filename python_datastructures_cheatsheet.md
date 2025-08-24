# Python Data Structures Cheatsheet

This cheatsheet provides a quick reference for common Python data structures and their operations.

## Lists

Lists are mutable, ordered sequences of elements. They can hold items of different data types.

**Creation:**
```python
# Empty list
my_list = []

# List with initial elements
my_list = [1, "hello", 3.14]
```

**Common Operations:**

*   **Accessing elements:**
    ```python
    my_list = [10, 20, 30, 40, 50]
    print(my_list[0])   # Output: 10
    print(my_list[-1])  # Output: 50
    print(my_list[1:3]) # Output: [20, 30]
    ```
*   **Adding elements:**
    ```python
    my_list = [1, 2]
    my_list.append(3)      # my_list is now [1, 2, 3]
    my_list.insert(1, 4)   # my_list is now [1, 4, 2, 3]
    my_list.extend([5, 6]) # my_list is now [1, 4, 2, 3, 5, 6]
    ```
*   **Removing elements:**
    ```python
    my_list = [1, 4, 2, 3, 5, 6]
    my_list.remove(4)      # my_list is now [1, 2, 3, 5, 6]
    popped_element = my_list.pop(2) # popped_element is 3, my_list is now [1, 2, 5, 6]
    del my_list[0]         # my_list is now [2, 5, 6]
    ```
*   **Other useful methods:**
    ```python
    my_list = [3, 1, 4, 1, 5, 9]
    my_list.sort()         # my_list is now [1, 1, 3, 4, 5, 9]
    my_list.reverse()      # my_list is now [9, 5, 4, 3, 1, 1]
    print(len(my_list))    # Output: 6
    print(my_list.count(1))# Output: 2
    ```
