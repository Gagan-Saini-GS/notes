## 📚 Subject: OOPS Using Java – Complete Exam Notes (with Code Examples)

### ✅ 1. Object-Oriented Programming (OOP) Paradigm

**OOP** is a programming model that focuses on **objects** which represent real-world entities. Java follows OOP principles strictly.

#### ⭐ Key Concepts:

- **Class**: Blueprint of objects.
- **Object**: Instance of a class.
- **Encapsulation**: Wrapping data and code into a single unit.
- **Abstraction**: Hiding implementation and showing only essential details.
- **Inheritance**: Acquiring properties from another class.
- **Polymorphism**: One task performed in different ways.

#### 🔸 Code Example:

```java
class Animal {
    void sound() {
        System.out.println("Animal makes sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Test {
    public static void main(String[] args) {
        Animal a = new Dog(); // Polymorphism
        a.sound();
    }
}
```

---

### ✅ 2. Advantages of OOP

- **Modularity**: Programs are divided into modules.
- **Reusability**: Existing code can be reused via inheritance.
- **Scalability**: Easy to expand with new features.
- **Security**: Data hiding via encapsulation.
- **Maintenance**: Easier to manage and update code.

#### 🔸 Code Example:

```java
class Employee {
    private int salary;

    public void setSalary(int salary) {
        this.salary = salary;
    }

    public int getSalary() {
        return salary;
    }
}
```

---

### ✅ 3. Characteristics of OOP

| Feature       | Description                              |
| ------------- | ---------------------------------------- |
| Class         | Blueprint for creating objects           |
| Object        | Instance of a class                      |
| Abstraction   | Hides internal implementation            |
| Encapsulation | Bundles data and methods                 |
| Inheritance   | Reuse code from parent class             |
| Polymorphism  | Same interface, multiple implementations |

---

### ✅ 4. Features of Java

- **Simple**: Easy syntax and structure.
- **Object-Oriented**: Everything in Java is associated with classes and objects.
- **Platform Independent**: Java bytecode runs on any OS via JVM.
- **Robust**: Strong memory management and exception handling.
- **Secure**: No pointers, sandbox execution.
- **Multithreaded**: Supports multithreading.
- **Distributed**: Facilitates distributed computing (RMI, Sockets).

---

### ✅ 5. Java Tokens

**Tokens** are smallest elements in a program.

| Token Type  | Examples                        |
| ----------- | ------------------------------- |
| Keywords    | `class`, `if`, `static`, `void` |
| Identifiers | `main`, `myVar`, `Student`      |
| Literals    | `100`, `"Java"`, `true`         |
| Operators   | `+`, `-`, `*`, `&&`, `++`       |

#### 🔸 Code Example:

```java
int number = 10;           // keyword, identifier, literal
String name = "Sumit";     // identifier, literal
```

---

### ✅ 6. Data Types

#### 🔹 Primitive Data Types:

| Type    | Size    | Example             |
| ------- | ------- | ------------------- |
| int     | 4 bytes | `int a = 5;`        |
| float   | 4 bytes | `float b = 5.5f;`   |
| boolean | 1 bit   | `boolean b = true;` |
| char    | 2 bytes | `char c = 'A';`     |

#### 🔹 Non-Primitive:

- Arrays, Strings, Classes, Interfaces

---

### ✅ 7. Java Environment

#### 📌 Java Program Structure

```java
public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello, Java!");
    }
}
```

#### 📌 Compilation & Execution

```bash
javac Hello.java    # Compiles to Hello.class (bytecode)
java Hello          # Runs on JVM
```

#### 📌 JVM (Java Virtual Machine)

- Converts bytecode to machine code.
- Handles memory allocation and garbage collection.
- Ensures platform independence.

---

### ✅ 8. Structure of Java Program

#### 🔹 Class & Object Example

```java
class Student {
    int roll;
    String name;

    void show() {
        System.out.println(roll + " " + name);
    }
}

public class Test {
    public static void main(String[] args) {
        Student s = new Student();
        s.roll = 1;
        s.name = "Sumit";
        s.show();
    }
}
```

#### 🔹 Constructor Example

```java
class Car {
    String model;

    Car(String m) {
        model = m;
    }

    void show() {
        System.out.println("Model: " + model);
    }
}
```

#### 🔹 Static Members Example

```java
class Count {
    static int x = 0;

    Count() {
        x++;
        System.out.println("Objects created: " + x);
    }
}
```

#### 🔹 Access Specifiers

| Modifier  | Scope              |
| --------- | ------------------ |
| private   | Within class       |
| default   | Within package     |
| protected | Package + Subclass |
| public    | Everywhere         |

---

### ✅ 9. Comments & Control Flow

#### 🔹 Comments

```java
// This is a single-line comment

/* This is
   a multi-line comment */

/** JavaDoc style comment */
```

#### 🔹 Control Flow

**If-Else:**

```java
if (x > 0) {
    System.out.println("Positive");
} else {
    System.out.println("Negative");
}
```

**Switch:**

```java
switch(day) {
    case 1: System.out.println("Monday"); break;
    default: System.out.println("Other Day");
}
```

**Loop Example:**

```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
```

---

### ✅ 10. Packages

#### 📦 Creating a Package

```java
package mypack;

public class Message {
    public void show() {
        System.out.println("Hello from package");
    }
}
```

#### 📦 Using Package

```java
import mypack.Message;

class Test {
    public static void main(String[] args) {
        Message m = new Message();
        m.show();
    }
}
```

#### 🔹 Built-in Packages

- `java.lang` – Basic classes (automatically imported)
- `java.util` – Utility classes like ArrayList, HashMap
- `java.io` – Input/output
- `java.sql` – Database access

---

### ✅ 11. Java API (Application Programming Interface)

- Java API is a set of prebuilt classes and packages.
- Saves time by offering reusable code.

#### 🔹 Common Packages:

| Package     | Description                   |
| ----------- | ----------------------------- |
| `java.lang` | Core features (String, Math)  |
| `java.util` | Data structures & collections |
| `java.io`   | Input/output                  |
| `java.sql`  | Database connectivity (JDBC)  |

#### 🔸 Example using `ArrayList`:

```java
import java.util.ArrayList;

public class Demo {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>();
        list.add("Sumit");
        list.add("Amit");

        for (String name : list) {
            System.out.println(name);
        }
    }
}
```

## 🧾 **OOPS Using Java – One Table Summary (Quick Revision Format)**

| **Topic**             | **Concept**          | **Description**                                      | **Example / Syntax**                          |
| --------------------- | -------------------- | ---------------------------------------------------- | --------------------------------------------- |
| **OOP Paradigm**      | Class                | Blueprint to create objects                          | `class Student { }`                           |
|                       | Object               | Instance of a class                                  | `Student s = new Student();`                  |
|                       | Encapsulation        | Hiding data using access modifiers                   | `private int age;` + `getAge()`               |
|                       | Abstraction          | Showing essential features only                      | `abstract class Shape`                        |
|                       | Inheritance          | Acquiring features from parent class                 | `class Dog extends Animal`                    |
|                       | Polymorphism         | Same method behaves differently in different classes | `Animal a = new Dog(); a.sound();`            |
| **Java Features**     | Platform Independent | Java bytecode runs on any OS via JVM                 | `.class` file runs anywhere                   |
|                       | Robust               | Exception handling + garbage collection              | `try-catch`, no memory leaks                  |
|                       | Secure               | No pointers, sandbox execution                       | Restricted memory access                      |
|                       | Multithreaded        | Java supports concurrent thread execution            | `Thread t = new Thread();`                    |
| **Tokens**            | Keyword              | Reserved words for Java syntax                       | `if`, `class`, `public`                       |
|                       | Identifier           | User-defined names                                   | `Student`, `main`                             |
|                       | Literal              | Constant values                                      | `100`, `"Java"`, `true`                       |
|                       | Operator             | Symbols to perform operations                        | `+`, `-`, `*`, `/`, `==`                      |
| **Data Types**        | Primitive            | Basic types like `int`, `float`, `char`              | `int x = 5;`, `float y = 4.5f;`               |
|                       | Non-Primitive        | Arrays, Strings, Classes                             | `String name = "Sumit";`                      |
| **Java Environment**  | JVM                  | Java Virtual Machine that executes bytecode          | `java Hello`                                  |
|                       | JDK                  | Java Development Kit – compiler + tools              | Contains `javac`, `java`                      |
|                       | Compilation          | Converts `.java` to `.class`                         | `javac Hello.java`                            |
|                       | Execution            | JVM loads and runs `.class` file                     | `java Hello`                                  |
| **Java Structure**    | Constructor          | Initializes object automatically                     | `Student() { }`                               |
|                       | Static Keyword       | Belongs to class, not object                         | `static int count;`                           |
|                       | Access Specifier     | Controls visibility of members                       | `public`, `private`, `protected`, default     |
|                       | Method               | Function defined inside a class                      | `void show() { }`                             |
| **Access Specifiers** | private              | Accessible only within class                         | `private int age;`                            |
|                       | default (no keyword) | Accessible within same package                       | No modifier                                   |
|                       | protected            | Same package and subclass                            | `protected int roll;`                         |
|                       | public               | Accessible from anywhere                             | `public int id;`                              |
| **Control Flow**      | if-else              | Decision making                                      | `if (x>0) { } else { }`                       |
|                       | switch               | Multiple branch decision                             | `switch(x) { case 1: break; }`                |
|                       | for/while/do-while   | Loops for repetition                                 | `for(int i=0;i<5;i++)`                        |
|                       | break/continue       | Loop control                                         | `break;`, `continue;`                         |
| **Packages**          | User-defined         | Custom grouping of classes                           | `package mypack;`                             |
|                       | Built-in             | Java library packages                                | `import java.util.*;`                         |
|                       | Import               | Use classes from another package                     | `import java.util.Scanner;`                   |
| **Java API**          | `java.lang`          | Core classes (auto-imported)                         | `String`, `Math`, `System`                    |
|                       | `java.util`          | Utility classes                                      | `ArrayList`, `Scanner`, `HashMap`             |
|                       | `java.io`            | Input/Output classes                                 | `File`, `BufferedReader`                      |
|                       | `java.sql`           | Database connection via JDBC                         | `Connection`, `ResultSet`                     |
| **Code Examples**     | Inheritance          | Child class inherits parent class                    | `class A { } class B extends A { }`           |
|                       | Polymorphism         | Method overriding in subclass                        | `Animal a = new Dog(); a.sound();`            |
|                       | Static Method        | Called without object                                | `Math.max(10, 20)`                            |
|                       | ArrayList            | Resizable array from `java.util`                     | `ArrayList<String> list = new ArrayList<>();` |
|                       | Constructor Overload | Multiple constructors with different params          | `Student() { } Student(int x) { }`            |

---
