# Unit-3

## **Lists and Dictionaries**

These are two **fundamental** and **frequently tested** data structures in Python — one for **ordered collections** (Lists) and one for **key-value pairs** (Dictionaries).

### 🔹 **1. Lists in Python**

A **list** is a **mutable, ordered collection** of elements. Lists can contain elements of **mixed data types**.

#### ✅ Creating Lists

```python
numbers = [1, 2, 3]
fruits = ["apple", "banana", "cherry"]
mixed = [1, "two", 3.0, [4, 5]]
empty = []
```

#### ✅ Indexing and Slicing

```python
fruits = ["apple", "banana", "cherry"]
print(fruits[0])      # 'apple'
print(fruits[-1])     # 'cherry'
print(fruits[1:3])    # ['banana', 'cherry']
```

#### ✅ List Methods

| Method         | Description                           |
| -------------- | ------------------------------------- |
| `append(x)`    | Adds item `x` to the end              |
| `insert(i, x)` | Inserts `x` at index `i`              |
| `remove(x)`    | Removes first occurrence of `x`       |
| `pop([i])`     | Removes and returns item at index `i` |
| `sort()`       | Sorts the list (in-place)             |
| `reverse()`    | Reverses the list (in-place)          |
| `extend(lst)`  | Appends another list to this one      |
| `clear()`      | Removes all elements                  |
| `index(x)`     | Returns the index of first `x`        |
| `count(x)`     | Returns count of `x`                  |

#### ✅ List Operations

| Operation     | Description           | Example                          |
| ------------- | --------------------- | -------------------------------- |
| Concatenation | Combine two lists     | `[1, 2] + [3, 4] → [1, 2, 3, 4]` |
| Repetition    | Repeat elements       | `[0] * 4 → [0, 0, 0, 0]`         |
| Membership    | Check if value exists | `2 in [1, 2, 3] → True`          |
| Iteration     | Loop through list     | `for x in list:`                 |

#### ✅ List Comprehension

A compact way to build lists.

```python
squares = [x**2 for x in range(5)]     # [0, 1, 4, 9, 16]
```

#### ✅ Nested Lists

```python
matrix = [[1, 2], [3, 4]]
print(matrix[1][0])   # 3
```

### 🔹 **2. Dictionaries in Python**

A **dictionary** is an **unordered collection** of **key-value pairs**. Keys must be unique and immutable.

#### ✅ Creating Dictionaries

```python
student = {
    "name": "Alice",
    "age": 21,
    "marks": 95
}
```

#### ✅ Accessing and Modifying Values

```python
print(student["name"])         # Alice

student["age"] = 22            # Update value
student["college"] = "MCA"     # Add new key
```

#### ✅ Dictionary Methods

| Method               | Description                                |
| -------------------- | ------------------------------------------ |
| `get(key[,default])` | Returns value, or default if key not found |
| `keys()`             | Returns all keys                           |
| `values()`           | Returns all values                         |
| `items()`            | Returns list of (key, value) pairs         |
| `update(d2)`         | Updates dict with another dict             |
| `pop(key)`           | Removes key and returns its value          |
| `clear()`            | Removes all items                          |

#### ✅ Example

```python
info = {"name": "John", "age": 25}
print(info.get("name"))       # John
print(info.get("grade", "N/A"))  # N/A

for k, v in info.items():
    print(k, "→", v)
```

#### ✅ Dictionary Keys

- Must be immutable: strings, numbers, tuples (not lists or dicts).
- Keys are unique: duplicates overwrite.

#### ✅ Nested Dictionaries

```python
students = {
    "101": {"name": "Alice", "marks": 88},
    "102": {"name": "Bob", "marks": 92}
}
print(students["101"]["name"])   # Alice
```

#### ✅ Dictionary Comprehension

```python
squares = {x: x*x for x in range(1, 4)}  # {1:1, 2:4, 3:9}
```

### 🔹 List vs Dictionary – Comparison Table

| Feature  | List                      | Dictionary                          |
| -------- | ------------------------- | ----------------------------------- |
| Ordered? | ✅ Yes (since Python 3.7) | ✅ Yes (insertion order maintained) |
| Mutable? | ✅ Yes                    | ✅ Yes                              |
| Access   | By index                  | By key                              |
| Syntax   | `[1, 2, 3]`               | `{"a": 1, "b": 2}`                  |
| Use Case | Ordered data              | Key-value mapping                   |

### ✅ Quick Revision

```python
# List
fruits = ["apple", "banana"]
fruits.append("mango")

# Dictionary
data = {"name": "John", "age": 30}
data["city"] = "Delhi"
```

---

### 🔹 1. **Special Features of Lists**

Python lists are highly versatile. Here's what makes them special:

#### ✅ A. **Heterogeneous Elements**

Lists can store any data type:

```python
lst = [1, "hello", 3.14, [2, 4], (5, 6)]
```

#### ✅ B. **Dynamic Sizing**

No need to predefine size. Lists can grow or shrink:

```python
lst = [1, 2]
lst.append(3)  # [1, 2, 3]
```

#### ✅ C. **Nesting**

Lists can hold other lists (2D or multi-dimensional structures):

```python
matrix = [[1, 2], [3, 4]]
```

#### ✅ D. **Mutability**

Lists are mutable:

```python
lst = [1, 2, 3]
lst[0] = 10    # [10, 2, 3]
```

#### ✅ E. **List Comprehension**

Concise way to build lists:

```python
squares = [x**2 for x in range(5)]
```

### 🔹 2. **Tuples in Python**

A **tuple** is an immutable sequence. Once created, you can't modify it.

```python
t = (1, 2, 3)
```

### 🔹 3. **Tuple Operators**

Tuples support a subset of sequence operations:

| Operator      | Example           | Result                     |
| ------------- | ----------------- | -------------------------- |
| Indexing      | `t[0]`            | First element              |
| Slicing       | `t[1:3]`          | Elements from index 1 to 2 |
| Concatenation | `(1, 2) + (3, 4)` | `(1, 2, 3, 4)`             |
| Repetition    | `(1,)*3`          | `(1, 1, 1)`                |
| Membership    | `2 in (1, 2, 3)`  | `True`                     |
| Iteration     | `for x in t:`     | Loops through items        |

### 🔹 4. **Tuple Built-in Functions**

| Function     | Description                | Example                  |
| ------------ | -------------------------- | ------------------------ |
| `len(t)`     | Number of elements         | `len((1, 2, 3)) → 3`     |
| `max(t)`     | Largest element            | `max((3, 1, 5)) → 5`     |
| `min(t)`     | Smallest element           | `min((3, 1, 5)) → 1`     |
| `sum(t)`     | Sum of numeric elements    | `sum((1, 2, 3)) → 6`     |
| `tuple(seq)` | Converts sequence to tuple | `tuple([1, 2]) → (1, 2)` |
| `count(x)`   | Occurrences of x           | `(1, 2, 2).count(2) → 2` |
| `index(x)`   | First index of x           | `(1, 2, 3).index(2) → 1` |

### 🔹 5. **Special Features of Tuples**

#### ✅ A. **Immutability**

Tuples cannot be changed after creation:

```python
t = (1, 2, 3)
# t[0] = 5 → ❌ Error
```

#### ✅ B. **Heterogeneous**

Can store any data types:

```python
t = (1, "hello", [2, 3], (4, 5))
```

#### ✅ C. **Faster Than Lists**

Tuples are more memory and performance efficient due to immutability.

#### ✅ D. **Safe for Constants**

Use tuples to represent fixed data:

```python
DAYS = ("Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun")
```

#### ✅ E. **Can Be Dictionary Keys**

Unlike lists, tuples can be used as dictionary keys:

```python
d = { (1, 2): "value" }
```

### 🔹 Comparison Table: Lists vs Tuples

| Feature        | List           | Tuple         |
| -------------- | -------------- | ------------- |
| Mutability     | Mutable        | Immutable     |
| Syntax         | `[1, 2, 3]`    | `(1, 2, 3)`   |
| Methods        | More           | Fewer         |
| Performance    | Slower         | Faster        |
| Used for       | Dynamic data   | Constant data |
| Dictionary Key | ❌ Not allowed | ✅ Allowed    |

### ✅ Summary

```python
# List
lst = [1, 2, 3]
lst.append(4)

# Tuple
t = (1, 2, 3)
print(t[0])

# Convert
tuple_from_list = tuple([1, 2])
list_from_tuple = list((1, 2))
```

---

## **Conditionals and Loops**

Covers: `if`, `else`, `while`, `for`, `break`, `continue`, `pass`, and `else` with loops.

### 🔹 1. **The `if` Statement**

Used to make decisions based on a condition.

```python
x = 10
if x > 0:
    print("Positive number")
```

### 🔹 2. **The `else` Statement**

Executes a block of code **when `if` condition is false**.

```python
x = -5
if x > 0:
    print("Positive")
else:
    print("Non-positive")
```

### 🔹 3. **The `elif` Statement**

Used for **multiple conditions**.

```python
x = 0
if x > 0:
    print("Positive")
elif x == 0:
    print("Zero")
else:
    print("Negative")
```

### 🔹 4. **The `while` Loop**

Repeats **as long as a condition is true**.

```python
count = 1
while count <= 5:
    print(count)
    count += 1
```

#### ✅ Infinite Loop Example

```python
while True:
    print("Runs forever unless broken")
```

### 🔹 5. **The `for` Loop**

Used to **iterate over a sequence** (like list, tuple, string).

```python
for i in range(5):
    print(i)
```

### ✅ Examples:

```python
for char in "MCA":
    print(char)

for fruit in ["apple", "banana"]:
    print(fruit)
```

### 🔹 6. **The `break` Statement**

Terminates the loop **immediately**.

```python
for i in range(5):
    if i == 3:
        break
    print(i)   # Output: 0 1 2
```

### 🔹 7. **The `continue` Statement**

Skips the current iteration and continues with the next.

```python
for i in range(5):
    if i == 2:
        continue
    print(i)   # Output: 0 1 3 4
```

### 🔹 8. **The `pass` Statement**

Used as a **placeholder** for future code.

```python
for i in range(3):
    pass  # Does nothing

if True:
    pass  # Useful in function/class definitions
```

### 🔹 9. **The `else` Clause with Loops**

An `else` block can follow a `for` or `while` loop.
It executes **only if the loop completes without a `break`.**

#### ✅ Example with `for`:

```python
for i in range(5):
    print(i)
else:
    print("Loop completed")
```

#### ✅ Example with `break`:

```python
for i in range(5):
    if i == 3:
        break
    print(i)
else:
    print("Loop completed")  # Will not execute
```

### 🔹 Summary Table

| Statement     | Description                         |
| ------------- | ----------------------------------- |
| `if`          | Executes block if condition is true |
| `else`        | Executes if `if` condition is false |
| `elif`        | Adds more conditions                |
| `while`       | Repeats while condition is true     |
| `for`         | Iterates over sequence              |
| `break`       | Exits the loop early                |
| `continue`    | Skips current iteration             |
| `pass`        | Does nothing (placeholder)          |
| `else` (loop) | Runs if no `break` occurred in loop |

### ✅ Sample Program

```python
for i in range(1, 6):
    if i == 3:
        continue
    print(i)
else:
    print("No break occurred")
```

---

## **`Gagan Saini`**
