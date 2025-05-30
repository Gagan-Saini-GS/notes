# Unit-2

## **What is an Object in Python?**

- In Python, **everything is an object** — integers, strings, lists, functions, even classes.
- An **object** is a **collection of data (attributes)** and **behavior (methods)**.

```python
x = 10
print(type(x))  # Output: <class 'int'>
```

---

## **Object-Oriented Programming (OOP)**

Python follows **OOP principles**:

1. **Encapsulation** – Bundling data and methods.
2. **Inheritance** – Reusing code via parent-child relationships.
3. **Polymorphism** – Same interface, different behavior.
4. **Abstraction** – Hiding implementation details.

---

## **Creating and Using Objects**

### ✅ Define a Class (Blueprint)

```python
class Car:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model

    def display(self):
        print(f"{self.brand} {self.model}")
```

### ✅ Create Object (Instance of Class)

```python
car1 = Car("Toyota", "Camry")
car1.display()  # Output: Toyota Camry
```

- `car1` is an **object** of class `Car`.
- `brand` and `model` are **attributes**.
- `display()` is a **method**.

---

## **Object Attributes**

### ✅ Instance Attributes

- Defined using `self` in the constructor.
- Unique to each object.

```python
car2 = Car("Honda", "Civic")
print(car2.brand)  # Honda
```

### ✅ Class Attributes

- Shared among all instances.

```python
class Car:
    wheels = 4  # Class attribute

print(Car.wheels)  # 4
```

---

## **Built-in Functions for Objects**

| Function                 | Purpose                    |
| ------------------------ | -------------------------- |
| `type(obj)`              | Returns the type of object |
| `id(obj)`                | Returns memory address     |
| `isinstance(obj, Class)` | Checks object type         |
| `dir(obj)`               | Lists attributes/methods   |

---

## **Object Lifecycle**

### ✅ Object Creation

- Done using a constructor: `__init__()`

### ✅ Object Destruction

- Python automatically deletes objects with zero references.
- `__del__()` is a destructor method (rarely used).

```python
class Demo:
    def __del__(self):
        print("Object destroyed")
```

---

## **Everything is an Object**

```python
print(type(5))           # <class 'int'>
print(type("hello"))     # <class 'str'>
print(type([1, 2, 3]))    # <class 'list'>
print(type(len))         # <class 'builtin_function_or_method'>
```

---

## **Standard Types in Python**

Python provides several **built-in (standard) data types**:

### ✅ 1. **Numeric Types**

- `int`: Integer (e.g. `5`, `-3`, `100`)
- `float`: Floating point number (e.g. `3.14`, `-0.1`)
- `complex`: Complex numbers (e.g. `3 + 4j`)

### ✅ 2. **Sequence Types**

- `str`: String (`"Hello"`)
- `list`: Mutable ordered collection (`[1, 2, 3]`)
- `tuple`: Immutable ordered collection (`(1, 2, 3)`)

### ✅ 3. **Set Types**

- `set`: Unordered collection of unique elements (`{1, 2, 3}`)
- `frozenset`: Immutable version of set

### ✅ 4. **Mapping Type**

- `dict`: Key-value pairs (`{"name": "Alice", "age": 25}`)

### ✅ 5. **Boolean Type**

- `bool`: True or False

### ✅ 6. **Binary Types**

- `bytes`, `bytearray`, `memoryview`

---

## **Other Built-in Types**

### ✅ 1. **NoneType**

- Represents the absence of a value: `None`

### ✅ 2. **File Objects**

- Represent file streams (obtained via `open()`)

### ✅ 3. **Range Type**

- Represents an immutable sequence of numbers:

```python
r = range(1, 5)  # Output: 1, 2, 3, 4
```

---

## **Internal Types**

Python internally uses **classes to represent types**. Examples:

| Type     | Class Internally     |
| -------- | -------------------- |
| Integer  | `<class 'int'>`      |
| String   | `<class 'str'>`      |
| List     | `<class 'list'>`     |
| Function | `<class 'function'>` |
| Module   | `<class 'module'>`   |

You can confirm using:

```python
type(5)           # <class 'int'>
type("hello")     # <class 'str'>
type([1, 2, 3])   # <class 'list'>
```

---

## **Standard Type Operators**

Operators that work with standard types:

### ✅ Numeric Types:

```python
+  -  *  /  //  %  **   # arithmetic
```

### ✅ String Operators:

```python
+ (concatenation)
* (repetition)
in / not in (membership)
```

### ✅ List/Set/Tuple Operators:

```python
+  *   in   not in
```

### ✅ Dictionary Operators:

```python
in   not in   # check keys
```

---

## **Standard Type Built-in Functions**

### ✅ Common Built-in Functions:

| Function                     | Description                      |
| ---------------------------- | -------------------------------- |
| `len()`                      | Length of the object             |
| `type()`                     | Type of the object               |
| `str()`                      | Converts to string               |
| `int()`, `float()`           | Convert to integer/float         |
| `list()`, `tuple()`, `set()` | Convert between types            |
| `max()`, `min()`             | Largest/smallest item            |
| `sum()`                      | Sum of items (numeric types)     |
| `sorted()`                   | Returns a sorted list            |
| `id()`                       | Returns memory address of object |

### ✅ Example:

```python
x = [1, 2, 3]
print(len(x))         # 3
print(type(x))        # <class 'list'>
print(sum(x))         # 6
```

---

## **Categorizing the Standard Types**

### ✅ 1. **Mutable Types** (Can be changed after creation)

- `list`, `dict`, `set`, `bytearray`

### ✅ 2. **Immutable Types** (Cannot be changed)

- `int`, `float`, `str`, `tuple`, `frozenset`, `bytes`

| Category | Examples            |
| -------- | ------------------- |
| Numeric  | int, float, complex |
| Sequence | str, list, tuple    |
| Set      | set, frozenset      |
| Mapping  | dict                |
| Boolean  | bool                |
| Binary   | bytes, bytearray    |

---

## **Unsupported Types**

While Python is dynamically typed, it **does not support** some operations/types found in other languages:

### ❌ Unsupported Concepts in Python:

| Concept              | Not Supported in Python     |
| -------------------- | --------------------------- |
| `char` type          | No distinct character type  |
| `++`, `--` operators | Not available               |
| `do...while` loop    | No such loop structure      |
| Pointers             | Not exposed to user         |
| Function Overloading | Not supported natively      |
| Compile-time Typing  | Python is dynamically typed |

---

### ✅ Summary Table

| Category | Type Examples             | Mutable?           |
| -------- | ------------------------- | ------------------ |
| Numeric  | `int`, `float`, `complex` | ❌ No              |
| Sequence | `str`, `list`, `tuple`    | `list` ✅ Yes      |
| Set      | `set`, `frozenset`        | `set` ✅ Yes       |
| Mapping  | `dict`                    | ✅ Yes             |
| Boolean  | `bool`                    | ❌ No              |
| Binary   | `bytes`, `bytearray`      | `bytearray` ✅ Yes |

---

## **Introduction to Numbers in Python**

Python supports **numeric data types** used for mathematical operations.

🔢 The **three main numeric types**:

1. `int` – Integer numbers
2. `float` – Floating-point numbers (decimals)
3. `complex` – Complex numbers (with real and imaginary parts)

All numeric types are **immutable** (their value cannot change once assigned).

### **1. Integers (`int`)**

#### ✅ Definition

Whole numbers (positive, negative, or zero) without a decimal point.

#### ✅ Examples

```python
a = 10
b = -3
c = 0
print(type(a))  # <class 'int'>
```

#### ✅ Integer Operations

```python
x = 5 + 3      # 8
y = 10 // 3    # 3 (Floor Division)
z = 2 ** 3     # 8 (Exponentiation)
```

#### ✅ No Size Limit

Python integers can grow arbitrarily large:

```python
x = 123456789123456789123456789
```

### **2. Floating-Point Real Numbers (`float`)**

#### ✅ Definition

- Numbers with a decimal point or in exponential (scientific) notation.

#### ✅ Examples

```python
a = 3.14
b = -0.001
c = 2.0
d = 1.5e3     # 1500.0 (Scientific notation)
```

#### ✅ Float Operations

```python
x = 3.5 + 2.1       # 5.6
y = 10 / 4          # 2.5 (true division)
z = round(3.14159, 2)  # 3.14
```

#### ⚠️ Floating-point precision is **not always exact** due to binary representation:

```python
print(0.1 + 0.2)  # 0.30000000000000004
```

### **3. Complex Numbers (`complex`)**

#### ✅ Definition

- Numbers with a **real part and imaginary part**.
- Represented as `a + bj` (where `j` is the imaginary unit).

#### ✅ Example

```python
z = 2 + 3j
print(z.real)  # 2.0
print(z.imag)  # 3.0
print(type(z)) # <class 'complex'>
```

#### ✅ Complex Arithmetic

```python
a = 2 + 3j
b = 1 + 1j
c = a + b      # (3+4j)
d = a * b      # (-1+5j)
```

### **Built-in Functions for Numbers**

| Function        | Description                   |
| --------------- | ----------------------------- |
| `abs(x)`        | Absolute value                |
| `pow(x, y)`     | x raised to the power y       |
| `round(x, n)`   | Rounds x to n decimal places  |
| `int(x)`        | Converts x to integer         |
| `float(x)`      | Converts x to float           |
| `complex(x, y)` | Creates complex number x + yj |

### **Type Conversion**

```python
x = int(5.6)         # 5
y = float(3)         # 3.0
z = complex(2, 3)    # (2+3j)
```

---

## **Operators in Python**

Operators are special symbols that perform operations on variables and values.

### ✅ 1. **Arithmetic Operators**

Used for mathematical calculations.

| Operator | Description    | Example  |
| -------- | -------------- | -------- |
| `+`      | Addition       | `a + b`  |
| `-`      | Subtraction    | `a - b`  |
| `*`      | Multiplication | `a * b`  |
| `/`      | Division       | `a / b`  |
| `//`     | Floor Division | `a // b` |
| `%`      | Modulus        | `a % b`  |
| `**`     | Exponentiation | `a ** b` |

### ✅ 2. **Comparison (Relational) Operators**

Used to compare values. Return `True` or `False`.

| Operator | Description           | Example  |
| -------- | --------------------- | -------- |
| `==`     | Equal to              | `a == b` |
| `!=`     | Not equal to          | `a != b` |
| `>`      | Greater than          | `a > b`  |
| `<`      | Less than             | `a < b`  |
| `>=`     | Greater than or equal | `a >= b` |
| `<=`     | Less than or equal    | `a <= b` |

### ✅ 3. **Logical Operators**

Used to combine multiple conditions.

| Operator | Description | Example           |
| -------- | ----------- | ----------------- |
| `and`    | Logical AND | `a > 2 and b < 5` |
| `or`     | Logical OR  | `a > 2 or b < 5`  |
| `not`    | Logical NOT | `not(a > 2)`      |

### ✅ 4. **Assignment Operators**

| Operator | Description         | Example   |
| -------- | ------------------- | --------- |
| `=`      | Assign              | `x = 10`  |
| `+=`     | Add and assign      | `x += 5`  |
| `-=`     | Subtract and assign | `x -= 3`  |
| `*=`     | Multiply and assign | `x *= 2`  |
| `/=`     | Divide and assign   | `x /= 4`  |
| `%=`     | Modulo and assign   | `x %= 2`  |
| `**=`    | Power and assign    | `x **= 3` |
| `//=`    | Floor divide assign | `x //= 2` |

### ✅ 5. **Bitwise Operators**

Operate at the binary level.

| Operator | Description | Example    |     |     |
| -------- | ----------- | ---------- | --- | --- |
| `&`      | Bitwise AND | `a & b`    |     |     |
| \`       | \`          | Bitwise OR | \`a | b\` |
| `^`      | Bitwise XOR | `a ^ b`    |     |     |
| `~`      | Bitwise NOT | `~a`       |     |     |
| `<<`     | Left Shift  | `a << 2`   |     |     |
| `>>`     | Right Shift | `a >> 2`   |     |     |

### ✅ 6. **Membership Operators**

Check for membership in sequences like lists or strings.

| Operator | Description        | Example            |
| -------- | ------------------ | ------------------ |
| `in`     | True if exists     | `"a" in "cat"`     |
| `not in` | True if not exists | `"x" not in "dog"` |

### ✅ 7. **Identity Operators**

| Operator | Description             | Example      |
| -------- | ----------------------- | ------------ |
| `is`     | True if same object     | `a is b`     |
| `is not` | True if not same object | `a is not b` |

---

## **Built-in Functions in Python**

Python provides many built-in functions to perform common operations.

### ✅ **Common Built-in Functions**

| Function                    | Description                |
| --------------------------- | -------------------------- |
| `print()`                   | Outputs to console         |
| `type()`                    | Returns the type of object |
| `id()`                      | Memory address of object   |
| `len()`                     | Number of elements         |
| `abs()`                     | Absolute value             |
| `max()`                     | Largest item               |
| `min()`                     | Smallest item              |
| `sum()`                     | Sum of elements            |
| `sorted()`                  | Returns sorted list        |
| `round()`                   | Rounds a float to n digits |
| `input()`                   | Reads input from user      |
| `int()`, `float()`, `str()` | Type conversions           |

### ✅ Example Usage:

```python
x = -10
print(abs(x))         # 10

nums = [4, 2, 7]
print(max(nums))      # 7
print(sum(nums))      # 13

s = "hello"
print(len(s))         # 5
```

### ✅ `help()` Function

Used for built-in documentation.

```python
help(str)    # Shows documentation for string methods
```

---

## **1. Strings**

A **string** is an **immutable sequence** of Unicode characters.

### ✅ Creation

```python
s = "Hello"
t = 'World'
multiline = """This is
a multiline string"""
```

### ✅ String Indexing and Slicing

```python
s = "Python"
print(s[0])      # 'P'
print(s[-1])     # 'n'
print(s[1:4])    # 'yth'
print(s[::-1])   # 'nohtyP' (reversed)
```

### ✅ String Methods

| Method         | Description                  |
| -------------- | ---------------------------- |
| `lower()`      | Convert to lowercase         |
| `upper()`      | Convert to uppercase         |
| `strip()`      | Remove whitespace            |
| `replace(a,b)` | Replace substring            |
| `split()`      | Split into list by delimiter |
| `join()`       | Join list into string        |
| `find()`       | Find position of substring   |
| `count()`      | Count occurrences            |

```python
s = "Hello World"
print(s.lower())     # hello world
print(s.count("l"))  # 3
```

## **2. Lists**

A **list** is a **mutable sequence** of values. It can hold **mixed data types**.

### ✅ Creation

```python
my_list = [1, 2, 3]
mixed = [1, "hello", 3.5]
nested = [[1, 2], [3, 4]]
```

### ✅ Indexing and Slicing

```python
print(my_list[0])     # 1
print(my_list[-1])    # 3
print(my_list[1:])    # [2, 3]
```

### ✅ List Methods

| Method        | Description                       |
| ------------- | --------------------------------- |
| `append()`    | Add item to end                   |
| `insert(i,x)` | Insert x at index i               |
| `remove(x)`   | Remove first occurrence of x      |
| `pop(i)`      | Remove and return item at index i |
| `sort()`      | Sort the list                     |
| `reverse()`   | Reverse the list                  |
| `extend()`    | Append elements from another list |

```python
lst = [3, 1, 2]
lst.sort()
print(lst)  # [1, 2, 3]
```

### ✅ List Comprehensions

```python
squares = [x**2 for x in range(5)]
```

## **3. Tuples**

A **tuple** is an **immutable sequence** of values.

### ✅ Creation

```python
t = (1, 2, 3)
single = (5,)   # Note the comma for a single element tuple
```

### ✅ Indexing and Slicing

```python
print(t[1])     # 2
print(t[:2])    # (1, 2)
```

### ✅ Tuple Methods

| Method     | Description         |
| ---------- | ------------------- |
| `count(x)` | Count of x in tuple |
| `index(x)` | First index of x    |

```python
t = (1, 2, 3, 2)
print(t.count(2))   # 2
```

## **Differences Between List and Tuple**

| Feature    | List         | Tuple           |
| ---------- | ------------ | --------------- |
| Mutability | Mutable      | Immutable       |
| Syntax     | `[1, 2]`     | `(1, 2)`        |
| Methods    | More methods | Fewer methods   |
| Use Case   | General use  | Fixed structure |

## **Common Sequence Operations**

| Operation     | Example          | Result          |
| ------------- | ---------------- | --------------- |
| Concatenation | `"a" + "b"`      | `'ab'`          |
| Repetition    | `[1] * 3`        | `[1, 1, 1]`     |
| Membership    | `2 in [1, 2, 3]` | `True`          |
| Iteration     | `for i in "abc"` | `a b c`         |
| Slicing       | `s[1:3]`         | elements 1 to 2 |

---

## **1. Sequences Overview**

A **sequence** is an **ordered collection of elements** in Python. Common sequence types include:

| Type   | Mutable | Example     |
| ------ | ------- | ----------- |
| String | ❌ No   | `"Python"`  |
| List   | ✅ Yes  | `[1, 2, 3]` |
| Tuple  | ❌ No   | `(1, 2, 3)` |

All sequences support common operations like indexing, slicing, iteration, etc.

## **2. Strings in Python**

A **string** is a **sequence of Unicode characters**. Strings are **immutable**.

### ✅ Declaration:

```python
s1 = "Hello"
s2 = 'World'
s3 = """Multiline
String"""
```

### ✅ String Indexing and Slicing:

```python
s = "Python"
s[0]      # 'P'
s[-1]     # 'n'
s[1:4]    # 'yth'
```

## **3. Strings and Operators**

Python allows several operators to work with strings.

### ✅ Common Operators:

| Operator | Description             | Example                                |
| -------- | ----------------------- | -------------------------------------- |
| `+`      | Concatenation           | `"Hello " + "World"` → `"Hello World"` |
| `*`      | Repetition              | `"Hi" * 3` → `"HiHiHi"`                |
| `in`     | Membership test         | `"a" in "apple"` → `True`              |
| `not in` | Negated membership test | `"z" not in "apple"` → `True`          |

## **4. String-only Operators**

These operators or expressions are **specific to strings**:

- **Concatenation**: Combines two strings: `"Hello" + "World"`
- **Repetition**: Repeats a string: `"ha" * 3 → "hahaha"`
- **Membership**: Tests character existence: `'a' in 'banana' → True`

Other types (e.g., integers) do not support these behaviors in the same way.

## **5. Built-in String Functions**

These are general-purpose Python built-ins that work with strings:

| Function  | Description                      | Example                    |
| --------- | -------------------------------- | -------------------------- |
| `len(s)`  | Returns length of string         | `len("abc") → 3`           |
| `str(x)`  | Converts to string               | `str(123)` → `'123'`       |
| `ord(c)`  | Unicode of character             | `ord('A')` → `65`          |
| `chr(i)`  | Character from Unicode           | `chr(65)` → `'A'`          |
| `repr(x)` | Returns printable representation | `repr("a\nb")` → `'a\\nb'` |

## **6. String Built-in Methods**

Python provides **many powerful methods** to work with strings:

### ✅ Case Conversion:

| Method         | Description              |
| -------------- | ------------------------ |
| `lower()`      | Converts to lowercase    |
| `upper()`      | Converts to uppercase    |
| `capitalize()` | First letter capitalized |
| `title()`      | Title-case string        |
| `swapcase()`   | Swap upper ↔ lower case  |

### ✅ Searching and Replacing:

| Method         | Description                      |
| -------------- | -------------------------------- |
| `find()`       | Returns first index or `-1`      |
| `index()`      | Like `find()`, but raises error  |
| `replace()`    | Replaces substring               |
| `count()`      | Number of times substring occurs |
| `startswith()` | Checks prefix                    |
| `endswith()`   | Checks suffix                    |

### ✅ Formatting and Splitting:

| Method     | Description                         |
| ---------- | ----------------------------------- |
| `split()`  | Splits by delimiter (returns list)  |
| `join()`   | Joins list into a string            |
| `strip()`  | Removes leading/trailing whitespace |
| `lstrip()` | Removes left spaces                 |
| `rstrip()` | Removes right spaces                |

### ✅ Example Code:

```python
s = "  Hello World  "
print(s.strip())          # 'Hello World'
print(s.lower())          # '  hello world  '
print(s.replace("World", "Python"))  # '  Hello Python  '
print("hello".upper())    # 'HELLO'
```

## **7. Special Features of Strings**

### ✅ 1. **Immutability**

- Strings **cannot be changed** after creation.

```python
s = "Hello"
s[0] = "h"   # ❌ Error
```

### ✅ 2. **Iteration**

- Strings are iterable:

```python
for char in "abc":
    print(char)
```

### ✅ 3. **Slicing**

- Powerful feature to access substrings:

```python
s = "Python"
s[::-1]      # Reverses the string → 'nohtyP'
```

### ✅ 4. **Escape Characters**

| Escape Code | Meaning      |
| ----------- | ------------ |
| `\n`        | New line     |
| `\t`        | Tab          |
| `\\`        | Backslash    |
| `\'`        | Single quote |
| `\"`        | Double quote |

```python
print("Hello\nWorld")
```

### ✅ 5. **Raw Strings**

- Use prefix `r` to disable escape sequences:

```python
print(r"C:\new_folder\text.txt")
```

## ✅ Summary Table

| Feature             | Example                 |
| ------------------- | ----------------------- |
| Indexing            | `"hello"[0] → 'h'`      |
| Slicing             | `"hello"[1:4] → 'ell'`  |
| Concatenation       | `"hi" + "there"`        |
| Repetition          | `"ha" * 2 → 'haha'`     |
| Membership          | `'a' in 'apple' → True` |
| Method Usage        | `"text".upper()`        |
| String Immutability | Changing char → Error   |

---

## **`Gagan Saini`**
