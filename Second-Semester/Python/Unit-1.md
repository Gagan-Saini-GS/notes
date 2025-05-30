# Unit 1

## **Introduction to Python**

- **Python** is a high-level, interpreted, and general-purpose programming language.
- Developed by **Guido van Rossum** and released in **1991**.
- Known for its **simple syntax** and readability.
- Supports **multiple programming paradigms**: object-oriented, functional, procedural.
- Widely used in **web development, data science, AI, automation, scripting**, etc.

---

## **Origin**

- **Late 1980s**: Development began as a successor to the ABC language.
- Officially released in **1991** as Python 0.9.0.
- Name inspired by **Monty Python’s Flying Circus** (a British comedy group).
- Python 2.x released in 2000, Python 3.x (not backward compatible) in 2008.

---

## **Comparison with Other Languages**

| Feature     | Python             | C++            | Java                 |
| ----------- | ------------------ | -------------- | -------------------- |
| Syntax      | Simple, readable   | Complex        | Verbose              |
| Compilation | Interpreted        | Compiled       | Compiled to bytecode |
| Memory Mgmt | Automatic (GC)     | Manual         | Automatic (GC)       |
| Typing      | Dynamic            | Static         | Static               |
| Use Cases   | AI, Web, Scripting | Systems, Games | Enterprise Apps      |

- Python is often chosen for **faster development time** and ease of learning.
- Slower in execution than C/C++ but ideal for prototyping.

---

## **Comments in Python**

- Used to **explain code** and make it more readable.

- **Single-line comment**: Starts with `#`
  Example:

  ```python
  # This is a single-line comment
  print("Hello, World!")
  ```

- **Multi-line comments**: Usually written using triple quotes (`'''` or `"""`) but technically are multi-line strings.
  Example:

  ```python
  """
  This is a
  multi-line comment
  """
  print("Python")
  ```

---

## **Operators in Python**

### 1. **Arithmetic Operators**

`+`, `-`, `*`, `/`, `//`, `%`, `**`

### 2. **Comparison (Relational) Operators**

`==`, `!=`, `>`, `<`, `>=`, `<=`

### 3. **Logical Operators**

`and`, `or`, `not`

### 4. **Assignment Operators**

`=`, `+=`, `-=`, `*=`, `/=`, `//=`, `%=`, `**=`

### 5. **Bitwise Operators**

`&`, `|`, `^`, `~`, `<<` (left shift), `>>` (right shift)

### 6. **Membership Operators**

`in`, `not in`

### 7. **Identity Operators**

`is`, `is not`

---

## **Variables in Python**

- Variables are **containers for storing data values**.
- No need to declare a type; **dynamically typed**.

### Syntax:

```python
x = 5           # int
name = "Alice"  # string
pi = 3.14       # float
```

### Rules:

- Variable name must start with a **letter or underscore**.
- Cannot start with a **digit**.
- Cannot be a **keyword** (like `if`, `while`, `class`).
- Case-sensitive: `Name` and `name` are different.

### Multiple assignments:

```python
a, b, c = 1, 2, 3
x = y = z = 100
```

---

## **What is a Class?**

- A **class** is a **blueprint** for creating objects.
- It defines **attributes (variables)** and **methods (functions)** that the objects created from the class can use.

### **Creating a Class**

```python
class Student:
    def __init__(self, name, roll):
        self.name = name
        self.roll = roll

    def display(self):
        print(f"Name: {self.name}, Roll: {self.roll}")
```

- `class Student:` → Defines a class named `Student`.
- `__init__()` → Special method called a **constructor**, used to initialize object properties.
- `self` → Refers to the current object.

### **Creating Objects (Instances)**

```python
s1 = Student("Alice", 101)
s1.display()   # Output: Name: Alice, Roll: 101
```

### **Attributes**

- **Instance attributes**: Defined inside `__init__()` with `self`.
- **Class attributes**: Shared across all instances.

```python
class Demo:
    count = 0    # Class attribute

    def __init__(self):
        Demo.count += 1

print(Demo.count)  # Accessing class attribute
```

### **Methods**

- Functions defined inside a class.
- Always have `self` as the first parameter to access instance data.

```python
class Car:
    def start(self):
        print("Engine started")
```

### **Types of Methods**

| Method Type     | Description                                            |
| --------------- | ------------------------------------------------------ |
| Instance Method | Operates on instance attributes                        |
| Class Method    | Operates on class variables using `@classmethod`       |
| Static Method   | No access to class/instance data, uses `@staticmethod` |

```python
class Example:
    @classmethod
    def show_class(cls):
        print("Class Method")

    @staticmethod
    def show_static():
        print("Static Method")
```

### **Inheritance**

- A class can **inherit** properties and methods from another class.

```python
class Animal:
    def sound(self):
        print("Animal sound")

class Dog(Animal):
    def sound(self):
        print("Bark")

d = Dog()
d.sound()  # Output: Bark
```

### **Encapsulation**

- Wrapping data and code into a single unit (class).
- Use `_` (protected) or `__` (private) to control access.

### **Polymorphism**

- Ability to use a function/class in different ways.
- Example: Same method name behaves differently in parent and child classes.

### **Destructor**

- `__del__()` method: Called when an object is deleted.

```python
class Demo:
    def __del__(self):
        print("Destructor called")
```

---

## **Modules in Python**

### ✅ What is a Module?

- A **module** is a Python file (`.py`) that contains **functions, classes, and variables**.
- Helps in **code reusability and organization**.

### ✅ Creating a Module

```python
# mymodule.py
def greet(name):
    print(f"Hello, {name}!")
```

### ✅ Importing a Module

```python
import mymodule
mymodule.greet("Alice")
```

### ✅ Import Specific Function

```python
from mymodule import greet
greet("Alice")
```

### ✅ Built-in Modules

Python has many built-in modules:

```python
import math
print(math.sqrt(25))  # Output: 5.0
```

### ✅ Alias a Module

```python
import math as m
print(m.pi)
```

### ✅ List All Functions in a Module

```python
import math
print(dir(math))
```

---

## **Syntax and Style**

### ✅ Python Syntax Basics

- Python uses **indentation** (whitespace) to define blocks of code.
- No `{}` or `;` like C/C++.
- Indent level is usually **4 spaces**.

```python
if True:
    print("Indented block")
```

### ✅ Style Guidelines (PEP 8)

Python follows **PEP 8**, a style guide for writing clean code.

#### Key Points:

- Use **meaningful variable names**.
- Keep lines **<= 79 characters**.
- Use **4 spaces per indentation level**.
- Leave two blank lines between functions.
- Use **snake_case** for variables and functions.
- Use **CamelCase** for class names.

#### Bad vs Good:

```python
# ❌ Bad
def ADD(x,y): return x+y

# ✅ Good
def add(x, y):
    return x + y
```

---

## **Statements in Python**

### ✅ Types of Statements

1. **Expression Statement**
   Executes an expression:

   ```python
   a = 5 + 3
   ```

2. **Assignment Statement**

   ```python
   x = 10
   ```

3. **Conditional Statement**

   ```python
   if x > 0:
       print("Positive")
   ```

4. **Looping Statement**

   - `for`, `while` loops.

5. **Import Statement**

   ```python
   import math
   ```

6. **Function & Class Definition**

   ```python
   def greet(): pass
   class Car: pass
   ```

### ✅ Multiple Statements in One Line

```python
x = 5; y = 10; print(x + y)
```

### ✅ Line Continuation

Use `\` for breaking long lines:

```python
total = 1 + 2 + 3 + \
        4 + 5 + 6
```

Or use parentheses:

```python
total = (1 + 2 + 3 +
         4 + 5 + 6)
```

---

## **Variable Assignment**

### ✅ Basics

- Variables are **created when first assigned**.
- Python is **dynamically typed** (type inferred at runtime).

```python
x = 10         # int
name = "John"  # str
pi = 3.14      # float
```

### ✅ Multiple Assignments

```python
a, b, c = 1, 2, 3
x = y = z = 0
```

### ✅ Swapping Variables (Pythonic)

```python
a, b = b, a
```

---

## **Identifiers**

### ✅ What is an Identifier?

- The name used for **variables, functions, classes, modules**.

### ✅ Rules for Identifiers

- Can include **letters (a-z, A-Z), digits (0-9), and underscores**.
- Must **not start with a digit**.
- Cannot use **Python keywords** (`if`, `while`, `class`, etc.).
- **Case-sensitive** (`Name`, `name`, and `NAME` are all different).

### ✅ Valid vs Invalid Identifiers

| Valid     | Invalid   |
| --------- | --------- |
| my_var    | 2name     |
| \_temp    | def       |
| total_sum | user-name |
| Student1  | class     |

---

## **Basic Style Guidelines (PEP 8)**

Python follows **PEP 8** as the official style guide.

### ✅ Naming Conventions

| Type     | Convention     |
| -------- | -------------- |
| Variable | `snake_case`   |
| Function | `snake_case()` |
| Class    | `CamelCase`    |
| Constant | `ALL_CAPS`     |

### ✅ Indentation

- Use **4 spaces** per indentation level (do not mix tabs and spaces).

### ✅ Line Length

- Limit lines to **79 characters**.

### ✅ Blank Lines

- 2 blank lines **between top-level functions/classes**.
- 1 blank line **between methods inside a class**.

### ✅ Imports

- Import **one module per line**, at the **top of the file**.

```python
import os
import sys
```

---

## **Memory Management in Python**

### ✅ Key Concepts

- Python uses **automatic memory management** with a **built-in garbage collector**.
- It tracks and manages memory allocation using **reference counting** and **cyclic garbage collection**.

### ✅ Reference Counting

- Every object has a count of references pointing to it.
- When the count drops to **zero**, the object is **deallocated**.

```python
a = [1, 2, 3]   # Reference count = 1
b = a           # Reference count = 2
del a           # Reference count = 1
del b           # Reference count = 0 → object deleted
```

### ✅ Garbage Collection

- The `gc` module can be used to interact with the garbage collector.

```python
import gc
gc.collect()  # Manually triggers garbage collection
```

### ✅ Memory Leaks

- Can occur with **circular references** if not handled properly.
- Python’s garbage collector handles most cases automatically.

---

## **`Gagan Saini`**
