# Unit-4

## **File Handling in Python**

Python uses **file objects** to interact with files using built-in functions and methods.

### ✅ Opening a File

```python
file = open("example.txt", "r")
```

| Mode  | Description       |
| ----- | ----------------- |
| `'r'` | Read (default)    |
| `'w'` | Write (overwrite) |
| `'a'` | Append            |
| `'b'` | Binary mode       |
| `'+'` | Read and write    |

### ✅ Closing a File

```python
file.close()
```

Use `with` to auto-handle closing:

```python
with open("example.txt", "r") as f:
    data = f.read()
```

### **File Built-in Functions**

| Function           | Description                     |
| ------------------ | ------------------------------- |
| `open()`           | Opens a file                    |
| `input()`          | Gets user input                 |
| `eval()`           | Parses and evaluates expression |
| `str()` / `repr()` | Converts data to string         |

### **File Object Methods**

```python
f.read()       # Reads entire file
f.readline()   # Reads a single line
f.readlines()  # Reads lines into list

f.write("text")     # Writes to file
f.writelines(list)  # Writes list of strings

f.seek(offset)      # Moves cursor
f.tell()            # Returns cursor position
f.flush()           # Flushes buffer
```

### **File Object Attributes**

```python
f.name       # File name
f.mode       # Mode of opening
f.closed     # Boolean: True if closed
```

### **Standard Files**

Python provides standard input/output/error streams via the `sys` module:

```python
import sys

sys.stdin     # Standard input
sys.stdout    # Standard output
sys.stderr    # Standard error
```

### **Command-Line Arguments**

Use `sys.argv` to get command-line arguments:

```python
import sys
print("Script name:", sys.argv[0])
print("First argument:", sys.argv[1])
```

Run using:

```bash
python script.py arg1 arg2
```

---

## **File System Operations**

Python’s `os` and `shutil` modules let you work with the file system.

### ✅ Common `os` Functions:

```python
import os

os.getcwd()        # Get current directory
os.chdir("path")   # Change directory
os.listdir()       # List files
os.remove("file")  # Delete file
os.rename(old, new)
os.mkdir("dir")    # Create directory
os.rmdir("dir")    # Remove empty dir
```

---

## **File Execution**

Python scripts can be run:

- From the command line: `python script.py`
- From another script: `exec(open("file.py").read())`
- Using `subprocess` for external files

### **Persistent Storage Modules**

Python supports saving data between runs using modules like:

#### ✅ `pickle`

Serializes Python objects:

```python
import pickle

data = {'name': 'Alice', 'age': 25}

# Write
with open("data.pkl", "wb") as f:
    pickle.dump(data, f)

# Read
with open("data.pkl", "rb") as f:
    data = pickle.load(f)
```

#### ✅ `shelve`

Works like a dictionary but stores data in a file:

```python
import shelve

with shelve.open("mydata") as db:
    db["user"] = {"name": "Alice", "age": 25}
```

### **Regular Expressions** (Quick Intro)

Python’s `re` module handles regex:

```python
import re

text = "Email: abc123@mail.com"
match = re.search(r"\w+@\w+\.\w+", text)
print(match.group())   # abc123@mail.com
```

### **Exception Handling**

Used to handle runtime errors without crashing the program.

#### ✅ Try-Except Block

```python
try:
    x = 10 / 0
except ZeroDivisionError:
    print("Can't divide by zero!")
```

#### ✅ Catching All Errors

```python
try:
    ...
except Exception as e:
    print("Error:", e)
```

#### ✅ Finally Block

Always executes:

```python
try:
    f = open("file.txt")
finally:
    f.close()
```

#### ✅ Raising Exceptions

```python
raise ValueError("Invalid input")
```

### ✅ Summary

| Feature       | Module             | Purpose                          |
| ------------- | ------------------ | -------------------------------- |
| File Handling | Built-in           | Read/write text and binary files |
| Regex         | `re`               | Pattern matching and searching   |
| Exceptions    | Built-in           | Handle runtime errors gracefully |
| Command Line  | `sys`              | Get arguments from terminal      |
| File System   | `os`, `shutil`     | Manage files/folders             |
| Persistence   | `pickle`, `shelve` | Save Python objects              |

---

## **Regular Expression**

### **What is a Regular Expression?**

A **Regular Expression (RE)** is a pattern used to match text using special syntax.
It allows complex search and manipulation in strings.

Example:

```python
import re
pattern = r"\d{3}"
text = "My number is 123-456-7890"
re.findall(pattern, text)  # ['123', '456', '789']
```

### **Why Use Regular Expressions?**

- Validate user input (e.g., emails, phone numbers)
- Search/replace patterns in text
- Extract specific data
- Text processing (logs, data mining)

### **Basic Python RE Syntax (re module)**

Import the `re` module:

```python
import re
```

#### ✅ Common Functions:

| Function        | Description                             |
| --------------- | --------------------------------------- |
| `re.match()`    | Matches pattern at beginning            |
| `re.search()`   | Searches for first match in entire text |
| `re.findall()`  | Returns all non-overlapping matches     |
| `re.finditer()` | Returns an iterator of matches          |
| `re.sub()`      | Substitutes matched pattern             |
| `re.compile()`  | Compiles a regex pattern                |

### **Special Symbols & Characters**

#### ✅ A. **Character Classes**

| Pattern | Matches                       |
| ------- | ----------------------------- |
| `\d`    | Digit `[0-9]`                 |
| `\D`    | Non-digit                     |
| `\w`    | Word character `[a-zA-Z0-9_]` |
| `\W`    | Non-word character            |
| `\s`    | Whitespace                    |
| `\S`    | Non-whitespace                |
| `.`     | Any character except newline  |

#### ✅ B. **Quantifiers**

| Symbol  | Meaning               | Example                    |
| ------- | --------------------- | -------------------------- |
| `*`     | 0 or more repetitions | `a*` matches "", "a", "aa" |
| `+`     | 1 or more repetitions | `a+` matches "a", "aa"     |
| `?`     | 0 or 1 repetition     | `a?` matches "", "a"       |
| `{n}`   | Exactly n times       | `\d{4}` matches "2025"     |
| `{n,}`  | n or more times       | `a{3,}`                    |
| `{n,m}` | Between n and m times | `a{2,4}`                   |

#### ✅ C. **Anchors and Boundaries**

| Symbol | Matches           |
| ------ | ----------------- |
| `^`    | Start of line     |
| `$`    | End of line       |
| `\b`   | Word boundary     |
| `\B`   | Non-word boundary |

#### ✅ D. **Groups and Alternation**

| Pattern   | Description              |                  |                     |
| --------- | ------------------------ | ---------------- | ------------------- |
| `(abc)`   | Matches "abc" as a group |                  |                     |
| \`        | \`                       | Alternation (\`a | b\` matches a or b) |
| `(?:...)` | Non-capturing group      |                  |                     |

Example:

```python
re.findall(r"(cat|dog)", "cat and dog")  # ['cat', 'dog']
```

#### ✅ E. **Escaping Special Characters**

To match special characters like `.`, `?`, use backslash `\`:

```python
re.search(r"\.", "3.14")  # matches "."
```

### **Examples of RE Patterns**

| Task                 | Pattern             |
| -------------------- | ------------------- |
| Match email          | `\w+@\w+\.\w+`      |
| Match phone          | `\d{3}-\d{3}-\d{4}` |
| Match digits only    | `^\d+$`             |
| Match alphabets      | `^[a-zA-Z]+$`       |
| Match date           | `\d{2}/\d{2}/\d{4}` |
| Match hex color code | `#[0-9a-fA-F]{6}`   |

### **Using `re` in Python — Examples**

```python
import re

text = "Email: user@example.com"
match = re.search(r"\w+@\w+\.\w+", text)
print(match.group())  # user@example.com

# Find all words
print(re.findall(r"\b\w+\b", "Python is fun!"))  # ['Python', 'is', 'fun']

# Substitute
text = re.sub(r"Python", "Java", "Python is awesome")
print(text)  # Java is awesome
```

### ✅ Summary: Useful Regex Cheatsheet

| Symbol  | Meaning             |     |
| ------- | ------------------- | --- |
| `\d`    | Digit               |     |
| `\w`    | Word character      |     |
| `\s`    | Whitespace          |     |
| `.`     | Any character       |     |
| `*`     | 0+ repeats          |     |
| `+`     | 1+ repeats          |     |
| `?`     | 0 or 1              |     |
| `[]`    | Character set       |     |
| `()`    | Grouping            |     |
| `{n,m}` | Repetition          |     |
| `^ $`   | Start/end of string |     |
| \`      | \`                  | Or  |

---

## **Exceptions**

### **What Are Exceptions?**

An **exception** is an error that occurs during the execution of a program.
It **disrupts the normal flow** of the program unless it is properly handled.

#### ✅ Example:

```python
print(10 / 0)
```

Will result in:

```
ZeroDivisionError: division by zero
```

### **Why Handle Exceptions?**

- To **avoid program crashes**
- To **gracefully handle errors**
- To provide **custom error messages**

### **Exceptions in Python**

Python uses the **try-except** block to catch and handle exceptions.

#### ✅ Syntax:

```python
try:
    # Code that may raise exception
except ExceptionType:
    # Code to handle the exception
```

### **Detecting and Handling Exceptions**

#### ✅ Basic Try-Except

```python
try:
    x = int("abc")
except ValueError:
    print("Cannot convert string to integer")
```

#### ✅ Handling Multiple Exceptions

```python
try:
    a = 5 / 0
except ZeroDivisionError:
    print("Division by zero")
except ValueError:
    print("Value error")
```

### **Using `else` and `finally` Blocks**

- `else`: Executes if no exception occurs.
- `finally`: Executes **always**, whether exception occurs or not.

#### ✅ Example:

```python
try:
    x = 10
except:
    print("Error")
else:
    print("No error occurred")
finally:
    print("This will always run")
```

### **Exceptions as Strings (Old Concept)**

Earlier versions of Python (Python 2) allowed using **strings** as exceptions:

```python
raise "Error message"   # Deprecated in Python 3
```

👉 In modern Python, **exceptions must derive from `BaseException`**.

### **Raising Exceptions**

You can manually raise exceptions using `raise`.

```python
raise ValueError("Invalid value")
```

#### ✅ Raising Custom Exception

```python
def check_age(age):
    if age < 0:
        raise ValueError("Age cannot be negative")

check_age(-1)
```

### **Assertions**

An **assertion** checks whether a condition is `True`.
If not, it raises an `AssertionError`.

#### ✅ Syntax:

```python
assert condition, "Error message"
```

#### ✅ Example:

```python
x = -5
assert x >= 0, "x must be non-negative"
```

Useful for **debugging** and **unit testing**.

### **Standard Exceptions in Python**

Python provides many built-in exception classes:

| Exception           | Description                             |
| ------------------- | --------------------------------------- |
| `Exception`         | Base class for all exceptions           |
| `ArithmeticError`   | Base class for numeric errors           |
| `ZeroDivisionError` | Division by zero                        |
| `ValueError`        | Invalid value                           |
| `TypeError`         | Wrong data type used                    |
| `IndexError`        | Index out of range                      |
| `KeyError`          | Dictionary key not found                |
| `FileNotFoundError` | File does not exist                     |
| `IOError`           | I/O operation failed                    |
| `ImportError`       | Module not found                        |
| `AttributeError`    | Invalid attribute access                |
| `NameError`         | Variable not defined                    |
| `AssertionError`    | Assertion failed                        |
| `RuntimeError`      | Generic error not caught by other types |

### ✅ Custom Exception Class

You can define your own exception:

```python
class MyError(Exception):
    pass

raise MyError("This is a custom error")
```

### Summary

| Concept             | Purpose                         |
| ------------------- | ------------------------------- |
| `try-except`        | Handle runtime exceptions       |
| `else`              | Executes if no error            |
| `finally`           | Always executes                 |
| `raise`             | Manually raise exceptions       |
| `assert`            | Debug-time condition checking   |
| Built-in Exceptions | Catch common programming errors |

---

## **`Gagan Saini`**
