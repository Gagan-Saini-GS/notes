## ✅ OOPS Using Java – Unit 2 Notes (In-Depth with Code Examples)

### 🔹 1. **Exception Handling**

Exception handling in Java is a powerful mechanism to handle runtime errors, maintain normal application flow, and improve program robustness. Java uses five keywords: `try`, `catch`, `finally`, `throw`, and `throws`.

#### 🔸 try-catch

- The code that may generate an exception is enclosed in the `try` block.
- The `catch` block is used to handle the exception.

```java
try {
    int a = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero");
}
```

#### 🔸 finally

- Executes regardless of whether an exception occurs or not.

```java
try {
    int data = 25 / 5;
} catch (Exception e) {
    System.out.println(e);
} finally {
    System.out.println("Finally block is always executed");
}
```

#### 🔸 throw

- Used to explicitly throw an exception.

```java
throw new NullPointerException("Null value encountered");
```

#### 🔸 throws

- Declares exceptions thrown by a method.

```java
void readFile() throws IOException {
    FileReader fr = new FileReader("data.txt");
}
```

---

### 🔹 2. **Wrapper Classes**

Java provides wrapper classes for each primitive data type. These are used when objects are required instead of primitives (e.g., in collections).

| Primitive | Wrapper Class |
| --------- | ------------- |
| byte      | Byte          |
| short     | Short         |
| int       | Integer       |
| long      | Long          |
| float     | Float         |
| double    | Double        |
| char      | Character     |
| boolean   | Boolean       |

#### 🔸 Example

```java
int a = 5;
Integer obj = Integer.valueOf(a);  // Autoboxing
int b = obj.intValue();            // Unboxing
```

---

### 🔹 3. **Arrays, Strings, Vectors**

#### 🔸 Array

- A container that holds elements of the same data type.
- Fixed size.

```java
int[] arr = {10, 20, 30};
for (int i : arr) {
    System.out.println(i);
}
```

#### 🔸 String

- Immutable class representing a sequence of characters.

```java
String s = "Hello";
System.out.println(s.toUpperCase());
```

#### 🔸 Vector

- Growable array-like structure.
- Thread-safe.

```java
Vector<String> v = new Vector<>();
v.add("Java");
v.add("C++");
System.out.println(v);
```

---

### 🔹 4. **Inheritance**

Inheritance allows a class to acquire the properties and methods of another class.

```java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}
```

Benefits:

- Code reusability
- Method Overriding
- Hierarchical classification

---

### 🔹 5. **final Class and Method**

#### 🔸 final class

- Cannot be extended (inherited).

```java
final class Vehicle {
    // code
}
```

#### 🔸 final method

- Cannot be overridden in subclass.

```java
class Car {
    final void run() {
        System.out.println("Running");
    }
}
```

---

### 🔹 6. **Abstract Class and Method**

- An abstract class can have abstract (no body) and concrete methods.
- Cannot be instantiated.

```java
abstract class Shape {
    abstract void draw();
}

class Circle extends Shape {
    void draw() {
        System.out.println("Drawing Circle");
    }
}
```

---

### 🔹 7. **Interface**

- An interface is like a contract.
- It can only contain abstract methods (until Java 7), and static/default methods (from Java 8).
- A class implements an interface.

```java
interface Drawable {
    void draw();
}

class Rectangle implements Drawable {
    public void draw() {
        System.out.println("Drawing Rectangle");
    }
}
```

---

### 🔹 8. **Method Overloading and Overriding**

#### 🔸 Method Overloading

- Same method name, different parameter list.

```java
class Display {
    void show(int a) {
        System.out.println(a);
    }
    void show(String b) {
        System.out.println(b);
    }
}
```

#### 🔸 Method Overriding

- Redefine a superclass method in subclass.

```java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}
class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}
```

---

### 🔹 9. **Files and I/O Streams**

Java I/O supports reading/writing files using streams.

#### 🔸 FileInputStream and FileOutputStream

```java
FileOutputStream fout = new FileOutputStream("data.txt");
fout.write("Hello Java".getBytes());
fout.close();

FileInputStream fin = new FileInputStream("data.txt");
int i;
while ((i = fin.read()) != -1) {
    System.out.print((char)i);
}
fin.close();
```

#### 🔸 Filter Streams

- These are used to add functionalities to existing streams.
- Example: BufferedInputStream, DataInputStream.

```java
BufferedInputStream bin = new BufferedInputStream(new FileInputStream("file.txt"));
```

#### 🔸 RandomAccessFile

- Allows reading/writing to a file at any position.

```java
RandomAccessFile file = new RandomAccessFile("test.txt", "rw");
file.seek(5);
file.writeBytes("Java");
```

#### 🔸 Serialization

- Converts an object into a byte stream for storage/transmission.

```java
ObjectOutputStream out = new ObjectOutputStream(new FileOutputStream("object.ser"));
out.writeObject(new Student());
out.close();
```

```java
ObjectInputStream in = new ObjectInputStream(new FileInputStream("object.ser"));
Student s = (Student) in.readObject();
in.close();
```

---

### 🔹 Summary Table for Unit 2

| Topic                          | Description                                                          | Code Example Snippet                                      |
| ------------------------------ | -------------------------------------------------------------------- | --------------------------------------------------------- |
| Exception Handling             | Handles runtime errors using try, catch, finally, throw, and throws. | `try { int x = 1/0; } catch (Exception e) {}`             |
| Wrapper Classes                | Wrap primitive types in objects.                                     | `Integer a = Integer.valueOf(5);`                         |
| Array                          | Fixed-size data container.                                           | `int[] arr = {1, 2, 3};`                                  |
| String                         | Immutable character sequence.                                        | `String s = "Java"; s.toUpperCase();`                     |
| Vector                         | Dynamic array, thread-safe.                                          | `Vector<String> v = new Vector<>(); v.add("Hello");`      |
| Inheritance                    | Acquiring properties of another class using `extends`.               | `class Dog extends Animal {}`                             |
| final class/method             | Prevents inheritance or overriding.                                  | `final class Car {}` / `final void run() {}`              |
| Abstract Class                 | Incomplete class with abstract methods.                              | `abstract void draw();`                                   |
| Interface                      | Blueprint of a class with abstract methods.                          | `interface Drawable { void draw(); }`                     |
| Method Overloading             | Same method name, different parameters.                              | `void display(int a); void display(String b);`            |
| Method Overriding              | Subclass redefines superclass method.                                | `class Dog extends Animal { void sound() {} }`            |
| FileInputStream / OutputStream | Read/write bytes to files.                                           | `new FileInputStream("file.txt");`                        |
| Filter Streams                 | Enhance existing stream functionality.                               | `BufferedInputStream bin = new BufferedInputStream(...);` |
| RandomAccessFile               | Read/write anywhere in file.                                         | `RandomAccessFile file = new RandomAccessFile(...);`      |
| Serialization                  | Convert object to byte stream for saving/transferring.               | `ObjectOutputStream out = new ObjectOutputStream(...);`   |

---

(Scroll up for full code examples and deeper explanations for each topic.)

Let me know if you’d like this in PDF or want Unit 3 notes next!
