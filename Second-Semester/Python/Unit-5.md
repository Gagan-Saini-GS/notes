# Unit-5

## Database In Python

### **Introduction to Database Interaction**

Python can connect to databases (like **MySQL**, **SQLite**, **PostgreSQL**, etc.) using libraries that provide SQL capabilities.

For basic learning and projects, **SQLite** is widely used because it's **serverless, file-based**, and comes built-in with Python.

### **Connecting to a SQL Database**

#### ✅ Using SQLite (Built-in in Python)

```python
import sqlite3

# Connect to database (creates file if not exists)
conn = sqlite3.connect("mydatabase.db")

# Create cursor object
cursor = conn.cursor()
```

### **Creating Tables**

```python
cursor.execute("""
CREATE TABLE IF NOT EXISTS students (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    age INTEGER
)
""")
conn.commit()
```

### **Inserting Data**

```python
cursor.execute("INSERT INTO students (name, age) VALUES (?, ?)", ("Alice", 22))
conn.commit()
```

Use `?` placeholders to avoid SQL injection.

### **Reading Data**

```python
cursor.execute("SELECT * FROM students")
rows = cursor.fetchall()

for row in rows:
    print(row)
```

- `fetchall()` → gets all rows
- `fetchone()` → gets the first matching row

### **Updating Records**

```python
cursor.execute("UPDATE students SET age = ? WHERE name = ?", (23, "Alice"))
conn.commit()
```

### **Deleting Records**

```python
cursor.execute("DELETE FROM students WHERE name = ?", ("Alice",))
conn.commit()
```

### **Closing the Connection**

```python
conn.close()
```

Always close the connection to save resources and prevent data corruption.

### **Using try-except for Safe Database Interaction**

```python
try:
    conn = sqlite3.connect("mydatabase.db")
    cursor = conn.cursor()
    cursor.execute("SELECT * FROM students")
    print(cursor.fetchall())
except sqlite3.Error as e:
    print("Database error:", e)
finally:
    conn.close()
```

### **Using MySQL (optional for advanced users)**

For MySQL, install `mysql-connector-python`:

```bash
pip install mysql-connector-python
```

#### ✅ Sample Code:

```python
import mysql.connector

conn = mysql.connector.connect(
    host="localhost",
    user="root",
    password="yourpassword",
    database="yourdb"
)

cursor = conn.cursor()
cursor.execute("SELECT * FROM tablename")
for row in cursor.fetchall():
    print(row)

conn.close()
```

### ✅ Summary: Key Steps to Connect to SQL in Python

| Step                | Command                                      |
| ------------------- | -------------------------------------------- |
| Import Library      | `import sqlite3` or `import mysql.connector` |
| Connect to Database | `sqlite3.connect("file.db")`                 |
| Create Cursor       | `cursor = conn.cursor()`                     |
| Execute SQL         | `cursor.execute(SQL_QUERY)`                  |
| Commit Changes      | `conn.commit()`                              |
| Fetch Data          | `cursor.fetchall()` or `fetchone()`          |
| Close Connection    | `conn.close()`                               |

---

## Operations

### **Creating Tables in SQL using Python**

Creating tables involves executing a `CREATE TABLE` SQL statement via Python's database library (like `sqlite3` or `mysql.connector`).

#### ✅ Example with SQLite:

```python
import sqlite3

# Connect to the database
conn = sqlite3.connect("college.db")
cursor = conn.cursor()

# Create table
cursor.execute("""
CREATE TABLE IF NOT EXISTS config (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    setting_name TEXT NOT NULL,
    setting_value TEXT NOT NULL
)
""")

conn.commit()
conn.close()
```

### **Searching Tables (Reading from Database)**

You can retrieve records using `SELECT` queries.

#### ✅ Example:

```python
conn = sqlite3.connect("college.db")
cursor = conn.cursor()

cursor.execute("SELECT * FROM config")
rows = cursor.fetchall()

for row in rows:
    print(row)

conn.close()
```

You can also add `WHERE` clauses for filtered searches:

```python
cursor.execute("SELECT * FROM config WHERE setting_name = ?", ("theme",))
```

### **Reading and Storing Configuration Info in a Database**

Applications often store settings like:

- Theme
- Language
- Version info
- Last used user ID, etc.

#### ✅ A. **Insert Configuration Values**

```python
cursor.execute("INSERT INTO config (setting_name, setting_value) VALUES (?, ?)",
               ("theme", "dark"))
conn.commit()
```

#### ✅ B. **Retrieve Configuration Values**

```python
cursor.execute("SELECT setting_value FROM config WHERE setting_name = ?", ("theme",))
value = cursor.fetchone()
if value:
    print("Theme is:", value[0])
```

### **Updating Configuration Values**

If a setting already exists, you may want to update it instead of inserting a new one.

```python
cursor.execute("UPDATE config SET setting_value = ? WHERE setting_name = ?",
               ("light", "theme"))
conn.commit()
```

### **Using Dictionary for Config Access (Optional)**

To make access easier, you can fetch all config into a dictionary:

```python
cursor.execute("SELECT setting_name, setting_value FROM config")
config_dict = dict(cursor.fetchall())

print(config_dict.get("theme", "default"))
```

### **Using JSON for Config (Alternative)**

You can also store config as a JSON string in a single table row.

```python
import json

settings = {"theme": "dark", "language": "en", "font_size": "14"}
json_data = json.dumps(settings)

cursor.execute("INSERT INTO config (setting_name, setting_value) VALUES (?, ?)",
               ("user_settings", json_data))
conn.commit()

# Read back
cursor.execute("SELECT setting_value FROM config WHERE setting_name = 'user_settings'")
data = cursor.fetchone()
settings = json.loads(data[0])
print(settings["theme"])
```

### **Best Practices**

| Practice                            | Why Important                           |
| ----------------------------------- | --------------------------------------- |
| Use parameterized queries           | Prevents SQL injection                  |
| Use `conn.commit()` after changes   | Ensures data is saved                   |
| Handle exceptions with `try-except` | Avoids crashes                          |
| Use `conn.close()`                  | Frees up system resources               |
| Avoid hardcoding config             | Makes the app portable and maintainable |

### ✅ Summary

| Task              | Method                                       |
| ----------------- | -------------------------------------------- |
| Create a table    | `CREATE TABLE` SQL via `cursor.execute()`    |
| Search table      | `SELECT * FROM table WHERE condition`        |
| Store config data | Insert key-value pairs into a `config` table |
| Retrieve config   | Use `SELECT` and optionally convert to dict  |
| Update config     | `UPDATE table SET ... WHERE ...`             |

---

## Multithreading

### **Understanding Threads**

A **thread** is a separate flow of execution. Python uses **multithreading** to run multiple tasks concurrently within a single process.

#### ✅ Why Use Threads?

- To perform **I/O-bound tasks** concurrently (e.g., reading files, web scraping, network I/O)
- Improves **efficiency** when tasks involve waiting

Python’s built-in `threading` module helps in managing threads.

### **Creating (Forking) Threads**

You can create threads using:

#### ✅ A. **Thread Class (Function-based)**

```python
import threading

def print_numbers():
    for i in range(5):
        print("Number:", i)

# Create thread
thread = threading.Thread(target=print_numbers)
thread.start()   # Forking/starting thread
thread.join()    # Wait for thread to complete
```

#### ✅ B. **Thread Subclassing**

```python
class MyThread(threading.Thread):
    def run(self):
        for i in range(5):
            print("Thread running:", i)

t = MyThread()
t.start()
t.join()
```

### **Synchronizing Threads**

Thread synchronization is needed to prevent **race conditions**, especially when multiple threads access shared resources.

#### ✅ Use of `Lock`

```python
lock = threading.Lock()

def update():
    with lock:  # Automatically acquires and releases the lock
        # critical section
        print("Thread-safe update")

threading.Thread(target=update).start()
```

You can also use `lock.acquire()` and `lock.release()` manually, but `with` is safer and cleaner.

### **Thread-safe Example**

```python
import threading

counter = 0
lock = threading.Lock()

def increment():
    global counter
    for _ in range(10000):
        with lock:
            counter += 1

threads = []
for _ in range(2):
    t = threading.Thread(target=increment)
    t.start()
    threads.append(t)

for t in threads:
    t.join()

print("Final counter:", counter)
```

Without a lock, the final counter might be incorrect due to race conditions.

### **Useful Threading Functions**

| Function / Attribute         | Purpose                             |
| ---------------------------- | ----------------------------------- |
| `threading.Thread()`         | Creates a new thread                |
| `start()`                    | Starts the thread                   |
| `join()`                     | Waits for the thread to finish      |
| `is_alive()`                 | Checks if thread is still running   |
| `threading.active_count()`   | Number of threads currently running |
| `threading.current_thread()` | Current thread object               |

### **Multithreading vs Multiprocessing**

| Aspect   | Multithreading                       | Multiprocessing                     |
| -------- | ------------------------------------ | ----------------------------------- |
| Tasks    | Concurrent tasks in **same process** | Tasks run in **separate processes** |
| Memory   | Shared memory                        | Separate memory                     |
| Best for | I/O-bound tasks                      | CPU-bound tasks                     |
| Module   | `threading`                          | `multiprocessing`                   |

### **Limitations (GIL)**

- Python (CPython) has a **Global Interpreter Lock (GIL)** that allows only **one thread to execute Python bytecode at a time**.
- So, multithreading is best suited for **I/O-bound tasks**, not for heavy CPU-bound tasks.

### ✅ Sample Multithreaded Program

```python
import threading
import time

def task(name):
    for i in range(3):
        print(f"{name} is working")
        time.sleep(1)

# Create threads
t1 = threading.Thread(target=task, args=("Thread-1",))
t2 = threading.Thread(target=task, args=("Thread-2",))

# Start threads
t1.start()
t2.start()

# Wait for completion
t1.join()
t2.join()

print("Both threads completed.")
```

### ✅ Summary

| Concept            | Description                    |
| ------------------ | ------------------------------ |
| Thread             | Lightweight process            |
| `threading.Thread` | Class to create threads        |
| `start()`          | Forks/starts a thread          |
| `join()`           | Waits for thread to complete   |
| `Lock()`           | Ensures thread synchronization |
| Use-case           | Best for I/O-bound tasks       |

---

## **`Gagan Saini`**
