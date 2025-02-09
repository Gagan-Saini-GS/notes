# Unit-1

## Introduction

C++ is a high-level, general-purpose programming language that supports procedural, object-oriented, and generic programming. It is widely used for system programming, game development, and applications requiring high performance.

### **OOPS Paradigm in C++**

C++ is based on **Object-Oriented Programming (OOP)**, which organizes code using objects and classes. The main principles of OOP in C++ are:

✅ **Encapsulation** – Wrapping data and methods inside a single unit (class).  
✅ **Abstraction** – Hiding complex implementation details and exposing only essential features.  
✅ **Inheritance** – Acquiring properties and behaviors of one class into another.  
✅ **Polymorphism** – Ability to use a function or method in different ways (compile-time and runtime).

Example:

```cpp
class Animal {
public:
    void makeSound() { cout << "Animal makes a sound" << endl; }
};

class Dog : public Animal {
public:
    void makeSound() { cout << "Dog barks" << endl; }
};
```

### **Identifiers, Keywords & Constants**

#### **Identifiers**

- Names used for variables, functions, arrays, classes, etc.
- Must start with a letter or underscore (`_`) and cannot be a keyword.
- Example: `int age;`, `float price;`, `void show();`

#### **Keywords**

- Reserved words with special meanings in C++.
- Examples: `int`, `float`, `class`, `if`, `else`, `return`, `public`, `private`, etc.

#### **Constants**

- Fixed values that cannot be changed during execution.
- Declared using `const` or `#define`.

Example:

```cpp
const float PI = 3.1416;
#define MAX 100
```

### **C++ Operators**

Operators are symbols that perform operations on variables and values.

#### **Types of Operators**

✅ **Arithmetic Operators**: `+`, `-`, `*`, `/`, `%`  
✅ **Relational Operators**: `==`, `!=`, `>`, `<`, `>=`, `<=`  
✅ **Logical Operators**: `&&`, `||`, `!`  
✅ **Bitwise Operators**: `&`, `|`, `^`, `~`, `<<`, `>>`  
✅ **Assignment Operators**: `=`, `+=`, `-=`, `*=`, `/=`, `%=`  
✅ **Increment/Decrement Operators**: `++`, `--`  
✅ **Ternary Operator**: `condition ? true_value : false_value;`

Example:

```cpp
int a = 10, b = 5;
cout << (a > b ? "a is greater" : "b is greater");
```

### **Type Conversion in C++**

Type conversion is the process of converting one data type to another.

#### **Implicit Type Conversion (Type Promotion)**

- Performed automatically by the compiler.
- Example: Converting `int` to `float`.

```cpp
int x = 5;
float y = x; // Implicit conversion
```

#### **Explicit Type Conversion (Type Casting)**

- Manually converting data types using `(type)` or `static_cast<type>()`.

```cpp
float num = 10.5;
int x = (int)num; // C-style casting
int y = static_cast<int>(num); // Modern C++ casting
```

### **Variable Declaration in C++**

A **variable** is a named storage location in memory. It must be declared before use.

#### **Syntax:**

```cpp
data_type variable_name;
```

**Example:**

```cpp
int age;       // Declaring an integer variable
float price;   // Declaring a floating-point variable
char grade;    // Declaring a character variable
```

#### **Variable Initialization**

You can assign a value at the time of declaration.

```cpp
int age = 25;
float price = 99.99;
char grade = 'A';
```

#### **Multiple Variable Declaration**

```cpp
int x = 5, y = 10, z = 15;
```

### **Statements in C++**

A **statement** in C++ is an instruction that performs an action. Every statement ends with a semicolon (`;`).

#### **Types of Statements:**

| **Type**                  | **Description**         | **Example**                           |
| ------------------------- | ----------------------- | ------------------------------------- |
| **Expression Statement**  | Evaluates an expression | `x = a + b;`                          |
| **Declaration Statement** | Declares a variable     | `int age = 30;`                       |
| **Control Statement**     | Controls program flow   | `if (x > 10) { ... }`                 |
| **Loop Statement**        | Repeats execution       | `for (int i = 0; i < 5; i++) { ... }` |
| **Jump Statement**        | Alters control flow     | `break;`, `continue;`, `return;`      |

### **Expression in C++**

An **expression** is a combination of variables, constants, and operators that produces a value.

**Example Expressions:**

```cpp
int a = 10, b = 5, result;
result = a + b;   // Arithmetic expression
bool check = (a > b);  // Relational expression (returns true or false)
x = (y > z) ? y : z; // Ternary expression
```

#### **Types of Expressions:**

- **Arithmetic Expressions:** Perform calculations (`a + b`, `x * y`).
- **Relational Expressions:** Compare values (`x > y`, `a == b`).
- **Logical Expressions:** Use logical operators (`&&`, `||`, `!`).
- **Assignment Expressions:** Assign values (`x = 5`, `y += 10`).
- **Ternary Expressions:** Conditional expressions (`condition ? value1 : value2`).

### **Input / Output in C++**

C++ uses the **iostream** library for input and output operations.

#### **Standard Input (`cin`)**

Used to take input from the user.

```cpp
#include <iostream>
using namespace std;

int main() {
    int age;
    cout << "Enter your age: ";
    cin >> age;  // Takes input from the user
    cout << "Your age is " << age << endl;
    return 0;
}
```

#### **Standard Output (`cout`)**

Used to display output to the screen.

```cpp
cout << "Hello, World!" << endl;
```

#### **Formatted Output (`setw`, `setprecision`)**

Requires `<iomanip>` library for advanced formatting.

```cpp
#include <iostream>
#include <iomanip>
using namespace std;

int main() {
    double pi = 3.14159;
    cout << "Pi: " << fixed << setprecision(2) << pi << endl;  // Output: 3.14
    return 0;
}
```

### **Summary Table**

| **Concept**              | **Description**                                          | **Example**        |
| ------------------------ | -------------------------------------------------------- | ------------------ |
| **Variable Declaration** | Defines a variable with a specific data type             | `int age;`         |
| **Statements**           | Instructions executed by the program                     | `x = y + z;`       |
| **Expressions**          | Combination of variables and operators producing a value | `a + b`, `x > y`   |
| **Input (`cin`)**        | Accepts user input                                       | `cin >> x;`        |
| **Output (`cout`)**      | Displays output                                          | `cout << "Hello";` |

---

### **Conditional Expressions (Ternary Operator)**

A **conditional expression** is an expression that evaluates a condition and returns a value based on whether the condition is `true` or `false`.

### **Ternary Operator (`? :`)**

Syntax:

```cpp
condition ? expression_if_true : expression_if_false;
```

Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 10, b = 20;
    int max = (a > b) ? a : b;  // Assigns the larger value to max
    cout << "Maximum: " << max << endl;
    return 0;
}
```

🔹 If `a > b`, `max = a`; otherwise, `max = b`.

### **Loop Statements**

Loops allow repeated execution of a block of code until a condition is met.

#### **Types of Loops in C++:**

| **Loop Type**     | **Description**                                   | **Syntax**                                                    |
| ----------------- | ------------------------------------------------- | ------------------------------------------------------------- |
| **For Loop**      | Used when the number of iterations is known       | `for(initialization; condition; increment/decrement) { ... }` |
| **While Loop**    | Executes while the condition is `true`            | `while(condition) { ... }`                                    |
| **Do-While Loop** | Executes at least once, then checks the condition | `do { ... } while(condition);`                                |

#### **For Loop Example**

```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 5; i++) {
        cout << "Iteration: " << i << endl;
    }
    return 0;
}
```

#### **While Loop Example**

```cpp
#include <iostream>
using namespace std;

int main() {
    int count = 1;
    while (count <= 5) {
        cout << "Count: " << count << endl;
        count++;
    }
    return 0;
}
```

#### **Do-While Loop Example**

```cpp
#include <iostream>
using namespace std;

int main() {
    int num = 1;
    do {
        cout << "Number: " << num << endl;
        num++;
    } while (num <= 5);
    return 0;
}
```

🔹 The `do-while` loop **always runs at least once**, even if the condition is false.

### **Breaking Control Statements**

These statements **alter the normal flow** of a loop.

| **Statement** | **Description**                                       | **Usage**                                     |
| ------------- | ----------------------------------------------------- | --------------------------------------------- |
| **break**     | Exits the loop immediately                            | Used to stop execution inside a loop          |
| **continue**  | Skips the current iteration and moves to the next one | Used when you want to skip certain iterations |
| **return**    | Exits from the current function                       | Used inside functions to terminate execution  |

#### **Break Statement Example**

🔹 **Stops the loop when `i == 3`**

```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 5; i++) {
        if (i == 3) {
            break;  // Exits loop when i == 3
        }
        cout << "i: " << i << endl;
    }
    return 0;
}
```

✅ **Output:**

```
i: 1
i: 2
```

#### **Continue Statement Example**

🔹 **Skips iteration when `i == 3` but continues the loop**

```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 5; i++) {
        if (i == 3) {
            continue;  // Skips iteration when i == 3
        }
        cout << "i: " << i << endl;
    }
    return 0;
}
```

✅ **Output:**

```
i: 1
i: 2
i: 4
i: 5
```

#### **Return Statement Example**

🔹 **Ends the function execution and returns a value**

```cpp
#include <iostream>
using namespace std;

int add(int a, int b) {
    return a + b;  // Function exits and returns the sum
}

int main() {
    cout << "Sum: " << add(5, 10) << endl;
    return 0;
}
```

### **Summary Table**

| **Concept**          | **Description**              | **Example**                      |
| -------------------- | ---------------------------- | -------------------------------- |
| **Ternary Operator** | Shortened `if-else`          | `(x > y) ? x : y;`               |
| **For Loop**         | Fixed number of iterations   | `for(int i=0; i<5; i++) { ... }` |
| **While Loop**       | Runs while condition is true | `while(x < 5) { ... }`           |
| **Do-While Loop**    | Runs at least once           | `do { ... } while(x < 5);`       |
| **Break**            | Exits loop immediately       | `if (x == 3) break;`             |
| **Continue**         | Skips current iteration      | `if (x == 3) continue;`          |
| **Return**           | Exits from function          | `return value;`                  |

---

## **Classes and Objects, Constructors & Destructors in C++** 🚀

### **Classes and Objects**

#### **What is a Class?**

A **class** is a user-defined blueprint for creating objects. It defines **data members (variables)** and **member functions (methods)** to operate on that data.

#### **What is an Object?**

An **object** is an instance of a class that holds actual values and can call class methods.

#### **Syntax of a Class in C++**

```cpp
class ClassName {
public:
    // Data members (variables)
    int x;

    // Member function (method)
    void display() {
        cout << "Value of x: " << x << endl;
    }
};
```

**Example: Class and Object**

```cpp
#include <iostream>
using namespace std;

// Define a class
class Car {
public:
    string brand;
    int speed;

    // Method to display car details
    void showDetails() {
        cout << "Brand: " << brand << ", Speed: " << speed << " km/h" << endl;
    }
};

int main() {
    Car car1;  // Creating an object

    car1.brand = "Toyota";
    car1.speed = 120;

    car1.showDetails();  // Calling method

    return 0;
}
```

### **Constructors in C++**

A **constructor** is a special function that is automatically called when an object is created. It **initializes** an object's attributes.

#### **Types of Constructors**

| **Constructor Type**          | **Description**                           |
| ----------------------------- | ----------------------------------------- |
| **Default Constructor**       | No parameters, initializes default values |
| **Parameterized Constructor** | Takes arguments to initialize values      |
| **Copy Constructor**          | Copies values from one object to another  |

**Example: Default & Parameterized Constructor**

```cpp
#include <iostream>
using namespace std;

class Car {
public:
    string brand;
    int speed;

    // Default Constructor
    Car() {
        brand = "Unknown";
        speed = 0;
    }

    // Parameterized Constructor
    Car(string b, int s) {
        brand = b;
        speed = s;
    }

    // Copy Constructor
    Car(const Car &obj) {
        brand = obj.brand;
        speed = obj.speed;
    }

    void showDetails() {
        cout << "Brand: " << brand << ", Speed: " << speed << " km/h" << endl;
    }
};

int main() {
    Car car1;  // Default constructor is called
    car1.showDetails();

    Car car2("BMW",220); // Parameterized constructor called
    car2.showDetails();

    Car car3 = car1; // Calls Copy Constructor
    car3.showDetails();

    return 0;
}
```

### **Destructor in C++**

A **destructor** is a special function that is automatically called when an object is destroyed. It **frees resources** (e.g., closing files, releasing memory).

#### **Syntax of Destructor**

```cpp
~ClassName() {
    // Cleanup code
}
```

**Example: Destructor in Action**

```cpp
#include <iostream>
using namespace std;

class Car {
public:
    // Constructor
    Car() {
        cout << "Car object created!" << endl;
    }

    // Destructor
    ~Car() {
        cout << "Car object destroyed!" << endl;
    }
};

int main() {
    Car car1; // Constructor is called
    return 0; // Destructor is called when the program ends
}
```

✅ **Output:**

```
Car object created!
Car object destroyed!
```

📌 The **destructor** is automatically called when the object goes out of scope.

### **Summary Table**

| **Concept**                   | **Description**                        | **Example**                    |
| ----------------------------- | -------------------------------------- | ------------------------------ |
| **Class**                     | Blueprint for creating objects         | `class Car { ... };`           |
| **Object**                    | Instance of a class                    | `Car car1;`                    |
| **Constructor**               | Initializes object automatically       | `Car() { ... }`                |
| **Parameterized Constructor** | Initializes with parameters            | `Car(string b, int s) { ... }` |
| **Copy Constructor**          | Copies values from another object      | `Car(const Car &obj) { ... }`  |
| **Destructor**                | Automatically called to free resources | `~Car() { ... }`               |

### **🔥 Key Takeaways**

✅ **Classes** define the blueprint, and **objects** are instances of the class.  
✅ **Constructors** initialize objects automatically when they are created.  
✅ **Parameterized constructors** allow setting values at creation time.  
✅ **Copy constructors** allow duplicating objects.  
✅ **Destructors** clean up when objects go out of scope.

---

## Function Overloading & Operator Overloading 🚀

### **1. Function Overloading in C++**

**Function Overloading** allows multiple functions to have the same name but different **parameters** (type, number, or order).

**Example of Function Overloading**

```cpp
#include <iostream>
using namespace std;

class Math {
public:
    // Function with two integers
    int add(int a, int b) {
        return a + b;
    }

    // Function with three integers
    int add(int a, int b, int c) {
        return a + b + c;
    }

    // Function with floating point numbers
    float add(float a, float b) {
        return a + b;
    }
};

int main() {
    Math obj;

    cout << "Sum (int): " << obj.add(5, 10) << endl;
    cout << "Sum (int, three params): " << obj.add(3, 7, 2) << endl;
    cout << "Sum (float): " << obj.add(2.5f, 3.5f) << endl;

    return 0;
}
```

✅ **Output:**

```
Sum (int): 15
Sum (int, three params): 12
Sum (float): 6
```

📌 The compiler selects the correct function based on the arguments.

### **2. Operator Overloading in C++**

**Operator Overloading** allows redefining how operators (`+`, `-`, `*`, etc.) work for user-defined types (classes).

#### **Syntax for Operator Overloading**

```cpp
return_type operator symbol (parameters) {
    // Function body
}
```

#### **Example: Overloading the `+` Operator**

```cpp
#include <iostream>
using namespace std;

class Complex {
public:
    int real, imag;

    // Constructor
    Complex(int r, int i) {
        real = r;
        imag = i;
    }

    // Overloading the + operator
    Complex operator+(const Complex &obj) {
        return Complex(real + obj.real, imag + obj.imag);
    }

    void display() {
        cout << real << " + " << imag << "i" << endl;
    }
};

int main() {
    Complex c1(3, 2), c2(1, 7);
    Complex c3 = c1 + c2; // Calls overloaded + operator

    cout << "Result: ";
    c3.display();

    return 0;
}
```

✅ **Output:**

```
Result: 4 + 9i
```

📌 The `+` operator now works with `Complex` objects.

#### **Example: Overloading the `<<` (Output) Operator**

```cpp
#include <iostream>
using namespace std;

class Complex {
public:
    int real, imag;

    Complex(int r, int i) : real(r), imag(i) {}

    // Overloading the << operator for output
    friend ostream& operator<<(ostream &out, const Complex &c) {
        out << c.real << " + " << c.imag << "i";
        return out;
    }
};

int main() {
    Complex c1(5, 3);
    cout << "Complex Number: " << c1 << endl; // Uses overloaded << operator
    return 0;
}
```

✅ **Output:**

```
Complex Number: 5 + 3i
```

📌 The `<<` operator is **overloaded as a friend function** to allow `cout` to handle `Complex` objects.

### **3. Operators That CAN Be Overloaded**

| **Operator** | **Example**    | **Usage**                 |
| ------------ | -------------- | ------------------------- |
| `+`          | `obj1 + obj2`  | Addition                  |
| `-`          | `obj1 - obj2`  | Subtraction               |
| `*`          | `obj1 * obj2`  | Multiplication            |
| `/`          | `obj1 / obj2`  | Division                  |
| `%`          | `obj1 % obj2`  | Modulus                   |
| `==`         | `obj1 == obj2` | Equality check            |
| `!=`         | `obj1 != obj2` | Inequality check          |
| `>`          | `obj1 > obj2`  | Greater than              |
| `<`          | `obj1 < obj2`  | Less than                 |
| `>=`         | `obj1 >= obj2` | Greater than or equal     |
| `<=`         | `obj1 <= obj2` | Less than or equal        |
| `++`         | `++obj`        | Pre-increment             |
| `--`         | `--obj`        | Pre-decrement             |
| `<<`         | `cout << obj`  | Stream insertion (output) |
| `>>`         | `cin >> obj`   | Stream extraction (input) |
| `=`          | `obj1 = obj2`  | Assignment                |
| `[]`         | `obj[index]`   | Array subscript           |
| `()`         | `obj()`        | Function call             |
| `->`         | `ptr->member`  | Pointer member access     |

### **4. Operators That CANNOT Be Overloaded**

Some operators have a fixed meaning in C++ and **cannot** be overloaded.

| **Operator**               | **Reason**                               |
| -------------------------- | ---------------------------------------- |
| `::` (Scope resolution)    | Defines scope, cannot be redefined       |
| `.` (Member access)        | Accesses class members                   |
| `.*` (Pointer-to-member)   | Works on pointer-to-member operations    |
| `sizeof`                   | Determines size of a data type or object |
| `typeid`                   | Retrieves type information               |
| `?:` (Ternary/Conditional) | Built-in syntax cannot be changed        |

### **Summary Table**

| **Concept**                             | **Description**                                  | **Example**                                      |
| --------------------------------------- | ------------------------------------------------ | ------------------------------------------------ |
| **Function Overloading**                | Same function name, different parameters         | `int add(int, int)` vs `float add(float, float)` |
| **Operator Overloading**                | Redefine operators for custom types              | `Complex operator+(Complex)`                     |
| **Operators That Can Be Overloaded**    | `+`, `-`, `*`, `/`, `<<`, `>>`, `==`, `!=`, etc. | `obj1 + obj2`                                    |
| **Operators That Cannot Be Overloaded** | `::`, `.`, `.*`, `sizeof`, `typeid`, `?:`        | Cannot be changed                                |

### **🔥 Key Takeaways**

✅ **Function overloading** allows multiple functions with the same name but different parameters.  
✅ **Operator overloading** allows custom behavior for operators when used with objects.  
✅ **Some operators (`::`, `.`, `sizeof`, etc.) cannot be overloaded** in C++.

---

## **Inheritance in C++** 🚀

### What is Inheritance?

**Inheritance** is a mechanism in C++ where a new class (**derived class**) inherits the properties and behaviors (data members and member functions) of an existing class (**base class**).

#### Key Benefits of Inheritance

✅ **Code Reusability** – Avoids code duplication by reusing the base class.  
✅ **Extensibility** – Allows adding new functionalities while keeping the existing ones.  
✅ **Hierarchical Representation** – Models real-world relationships (e.g., Animal 🡪 Mammal 🡪 Dog).

### Types of Inheritance

#### 1️⃣ Single Inheritance

- A derived class inherits from a single base class.
- **Example:** A `Car` class inheriting from a `Vehicle` class.

#### 2️⃣ Multiple Inheritance

- A derived class inherits from **two or more base classes**.
- **Example:** A `Child` class inheriting from both `Father` and `Mother`.

#### 3️⃣ Multilevel Inheritance

- A derived class inherits from another derived class, forming a **chain**.
- **Example:** `Animal 🡪 Mammal 🡪 Dog`.

#### 4️⃣ Hierarchical Inheritance

- A single base class is inherited by **multiple derived classes**.
- **Example:** A `Vehicle` class being inherited by `Car`, `Bike`, and `Truck`.

#### 5️⃣ Hybrid (Multiple + Multilevel) Inheritance

- A combination of **multiple** and **multilevel** inheritance.
- **Example:** A `SportsCar` class inheriting from both `Car` (single) and `RacingVehicle` (multilevel).

### Access Modifiers in Inheritance

| **Base Class Access Modifier** | **Public Inheritance**     | **Protected Inheritance**  | **Private Inheritance**  |
| ------------------------------ | -------------------------- | -------------------------- | ------------------------ |
| **Public Members**             | Public in derived class    | Protected in derived class | Private in derived class |
| **Protected Members**          | Protected in derived class | Protected in derived class | Private in derived class |
| **Private Members**            | Not accessible             | Not accessible             | Not accessible           |

📌 **Private members of a base class are never inherited directly**, but they can be accessed using **public/protected member functions** of the base class.

### Summary Table

| **Type of Inheritance**      | **Description**                                     |
| ---------------------------- | --------------------------------------------------- |
| **Single Inheritance**       | One class inherits from another single class.       |
| **Multiple Inheritance**     | One class inherits from **multiple** base classes.  |
| **Multilevel Inheritance**   | A chain of inheritance (A → B → C).                 |
| **Hierarchical Inheritance** | One base class, multiple derived classes.           |
| **Hybrid Inheritance**       | Combination of multiple and multilevel inheritance. |

### 🔥Key Takeaways

✅ **Inheritance enables code reusability and hierarchy in C++ programs.**  
✅ **Multiple inheritance allows inheriting from multiple classes but can lead to complexity.**  
✅ **Access modifiers (public, protected, private) control inherited member accessibility.**  
✅ **Hybrid inheritance combines different inheritance types.**

### Inheritance Example

```cpp
#include <iostream>
using namespace std;

// Base Class
class Vehicle {
public:
    int wheels;

    void showInfo() {
        cout << "This vehicle has " << wheels << " wheels." << endl;
    }
};

// Derived Class (Inheriting from Vehicle)
class Car : public Vehicle {
public:
    string brand;

    void showCarInfo() {
        cout << "This is a " << brand << " car." << endl;
    }
};

int main() {
    Car myCar;
    myCar.wheels = 4;  // Inherited property
    myCar.brand = "Toyota";

    myCar.showInfo();     // Calls base class function
    myCar.showCarInfo();  // Calls derived class function

    return 0;
}
```

---

## Virtual Function & Friend Function 🚀

### **Virtual Function in C++**

A **virtual function** is a member function in a **base class** that is **overridden** in the **derived class**. It allows **runtime polymorphism** by enabling **dynamic binding** (determining which function to call at runtime instead of compile time).

#### **Key Features of Virtual Functions**

✅ Defined using the `virtual` keyword in the base class.  
✅ Supports **runtime polymorphism** (function call resolved at runtime).  
✅ Uses **pointers or references** to call overridden methods dynamically.  
✅ The **base class pointer** can point to a derived class object.  
✅ If a class has a **virtual function, it should have a virtual destructor** to ensure proper cleanup.

**Example: Virtual Function**

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void show() {  // Virtual function
        cout << "Base class show function" << endl;
    }
};

class Derived : public Base {
public:
    void show() override {  // Overriding base class function
        cout << "Derived class show function" << endl;
    }
};

int main() {
    Base* basePtr;  // Base class pointer
    Derived obj;

    basePtr = &obj;  // Base class pointer points to derived class object
    basePtr->show(); // Calls Derived's show() due to virtual function

    return 0;
}
```

✅ **Output:**

```
Derived class show function
```

📌 **Explanation:**

- The `show()` function in the **base class** is declared as `virtual`.
- When the `basePtr` points to a `Derived` object and calls `show()`, the **derived class's** `show()` function is executed instead of the base class’s function.
- This is called **dynamic method dispatch** or **late binding**.

### **Friend Function in C++**

A **friend function** is a function that is **not a member of a class** but has permission to **access private and protected members** of the class.

#### **Key Features of Friend Functions**

✅ Declared using the `friend` keyword inside the class.  
✅ Not a member function, so it **cannot be called using an object**.  
✅ Can access **private and protected** members of the class.  
✅ Can be declared in multiple classes (useful for operator overloading).

**Example: Friend Function**

```cpp
#include <iostream>
using namespace std;

class Car {
private:
    int speed;

public:
    Car(int s) { speed = s; }

    // Friend function declaration
    friend void showSpeed(Car obj);
};

// Friend function definition
void showSpeed(Car obj) {
    cout << "Car speed: " << obj.speed << " km/h" << endl;
}

int main() {
    Car myCar(120);
    showSpeed(myCar); // Calling the friend function

    return 0;
}
```

✅ **Output:**

```
Car speed: 120 km/h
```

📌 **Explanation:**

- `showSpeed()` is **not a member** of the `Car` class, but it is **declared as a friend** inside the class.
- The function **can access the private member** `speed` of `Car`.
- **Friend functions are used when external functions need special access to private data.**

### **Key Differences Between Virtual & Friend Functions**

| Feature         | **Virtual Function**                        | **Friend Function**                      |
| --------------- | ------------------------------------------- | ---------------------------------------- |
| **Purpose**     | Supports **polymorphism** (dynamic binding) | Accesses private/protected members       |
| **Declared in** | Base class (with `virtual` keyword)         | Inside class (with `friend` keyword)     |
| **Access**      | Called using an **object or pointer**       | Called **normally** (not via object)     |
| **Overriding**  | Can be **overridden** in derived classes    | Cannot be overridden                     |
| **Inheritance** | Works with inheritance                      | Not related to inheritance               |
| **Binding**     | **Runtime binding (late binding)**          | **Compile-time binding (early binding)** |

### **🔥 Key Takeaways**

✅ **Virtual functions** enable **runtime polymorphism** (method overriding).  
✅ **Friend functions** access **private** and **protected** members of a class.  
✅ **Virtual functions** use **dynamic binding**, while **friend functions** use **early binding**.  
✅ Friend functions **are not members of a class** but are **granted access** to private data.

---

## **`this` Pointer & Dynamic Type Information (RTTI)** 🚀

### **`this` Pointer in C++**

#### **What is `this` Pointer?**

- The **`this` pointer** is an implicit pointer available in **non-static** member functions.
- It **stores the address** of the **current calling object**.
- Used when **variable names conflict** (e.g., class members vs. function parameters).
- Cannot be modified.

**Example: Using `this` Pointer**

```cpp
#include <iostream>
using namespace std;

class Car {
private:
    string brand;

public:
    // Constructor
    Car(string brand) {
        this->brand = brand; // Resolving name conflict using 'this'
    }

    void show() {
        cout << "Car Brand: " << this->brand << endl;
    }
};

int main() {
    Car myCar("Toyota");
    myCar.show();  // Output: Car Brand: Toyota
    return 0;
}
```

✅ **Output:**

```
Car Brand: Toyota
```

📌 **Why use `this`?**

- Without `this->brand = brand;`, there would be a conflict because the parameter and class variable have the same name.
- `this->brand` refers to the **class member variable**, while `brand` refers to the **function parameter**.

### **Dynamic Type Information (RTTI)**

#### **What is RTTI (Run-Time Type Information)?**

- **RTTI** allows identifying the **actual object type** at **runtime**.
- Used when dealing with **polymorphism** and **inheritance**.
- Requires **at least one virtual function** in the base class.
- Main RTTI operators:  
  ✅ `typeid` – Gets type of an object.  
  ✅ `dynamic_cast` – Safely converts pointers/references.

#### **Using `typeid` for Type Checking**

```cpp
#include <iostream>
#include <typeinfo> // Required for typeid
using namespace std;

class Vehicle {
public:
    virtual void show() {} // At least one virtual function is needed for RTTI
};

class Car : public Vehicle {};
class Bike : public Vehicle {};

int main() {
    Vehicle* v1 = new Car();
    Vehicle* v2 = new Bike();

    cout << "Type of v1: " << typeid(*v1).name() << endl;
    cout << "Type of v2: " << typeid(*v2).name() << endl;

    delete v1;
    delete v2;
    return 0;
}
```

✅ **Possible Output:**

```
Type of v1: class Car
Type of v2: class Bike
```

📌 **Key Points:**

- `typeid(*v1).name()` returns the **actual type** at **runtime** (Car or Bike).
- If `v1` and `v2` were not polymorphic (i.e., no virtual function in `Vehicle`), `typeid(*v1)` would return `Vehicle`.

#### **Using `dynamic_cast` for Safe Downcasting**

```cpp
#include <iostream>
using namespace std;

class Vehicle {
public:
    virtual void show() { cout << "This is a vehicle" << endl; }
};

class Car : public Vehicle {
public:
    void show() { cout << "This is a car" << endl; }
};

int main() {
    Vehicle* v = new Car(); // Base class pointer pointing to derived class object

    // Attempting to downcast safely
    Car* c = dynamic_cast<Car*>(v);
    if (c)
        c->show(); // Calls Car's show()

    delete v;
    return 0;
}
```

✅ **Output:**

```
This is a car
```

📌 **Key Points:**

- `dynamic_cast<Car*>(v)` safely **downcasts** `v` from `Vehicle*` to `Car*`.
- If `v` was pointing to something that wasn't a `Car`, the cast would return `nullptr`.

### **Key Differences: `this` Pointer vs. RTTI**

| Feature                        | **`this` Pointer**                       | **RTTI (`typeid`, `dynamic_cast`)**  |
| ------------------------------ | ---------------------------------------- | ------------------------------------ |
| **Purpose**                    | Refers to current object                 | Identifies object type at runtime    |
| **Scope**                      | Inside class member functions            | Works across polymorphic objects     |
| **Usage**                      | Resolving name conflicts, chaining calls | Safe type conversions, type checking |
| **Requires Virtual Function?** | ❌ No                                    | ✅ Yes (for accurate results)        |
| **Modifiable?**                | ❌ No                                    | ❌ No                                |
| **Common Functions**           | `this->`                                 | `typeid()`, `dynamic_cast<>()`       |

### **🔥 Key Takeaways**

✅ **`this` pointer** is used inside class member functions to access the current object.  
✅ **RTTI (`typeid` and `dynamic_cast`)** is used for **runtime type checking** and **safe downcasting**.  
✅ `dynamic_cast` ensures **safe conversion** between base and derived classes.  
✅ RTTI requires **at least one virtual function** in the base class.

---

## **Polymorphism** 🚀

### **What is Polymorphism?**

Polymorphism means "**many forms**" and allows **one interface to be used for different data types or classes**. It enables functions and operators to behave differently based on the object or data type.

### **Types of Polymorphism in C++**

#### ✅ **1. Compile-Time Polymorphism (Static Binding)**

- Also known as **early binding**.
- Decided at **compile time**.
- Achieved using:
  - **Function Overloading**
  - **Operator Overloading**

#### ✅ **2. Run-Time Polymorphism (Dynamic Binding)**

- Also known as **late binding**.
- Decided at **runtime**.
- Achieved using:
  - **Virtual Functions (Method Overriding)**
  - **Function Pointers (Less Common)**

### **1. Compile-Time Polymorphism Examples**

#### **🔹 Function Overloading**

- Same function name with **different parameters**.

```cpp
#include <iostream>
using namespace std;

class Math {
public:
    // Function with one parameter
    void add(int a) {
        cout << "Sum: " << a + 10 << endl;
    }

    // Function with two parameters
    void add(int a, int b) {
        cout << "Sum: " << a + b << endl;
    }
};

int main() {
    Math obj;
    obj.add(5);       // Calls add(int)
    obj.add(5, 10);   // Calls add(int, int)

    return 0;
}
```

✅ **Output:**

```
Sum: 15
Sum: 15
```

📌 **Why?**

- The compiler determines which function to call based on **number/type of arguments**.

#### **🔹 Operator Overloading**

- Allows **redefining operators** for user-defined types.

```cpp
#include <iostream>
using namespace std;

class Complex {
public:
    int real, imag;

    Complex(int r, int i) : real(r), imag(i) {}

    // Overloading the '+' operator
    Complex operator+(const Complex& obj) {
        return Complex(real + obj.real, imag + obj.imag);
    }

    void display() {
        cout << real << " + " << imag << "i" << endl;
    }
};

int main() {
    Complex c1(3, 4), c2(1, 2);
    Complex c3 = c1 + c2; // Calls operator+()
    c3.display(); // Output: 4 + 6i
    return 0;
}
```

✅ **Output:**

```
4 + 6i
```

📌 **Why?**

- The `+` operator is **overloaded** to work with `Complex` objects.

### **2. Run-Time Polymorphism Examples**

#### **🔹 Method Overriding (Virtual Functions)**

- Achieved using **base class pointers** to call derived class methods dynamically.

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    virtual void makeSound() { // Virtual function
        cout << "Animal makes a sound" << endl;
    }
};

class Dog : public Animal {
public:
    void makeSound() override { // Overriding base class function
        cout << "Dog barks" << endl;
    }
};

int main() {
    Animal* a;
    Dog d;

    a = &d;
    a->makeSound(); // Calls Dog's makeSound() (runtime decision)

    return 0;
}
```

✅ **Output:**

```
Dog barks
```

📌 **Why?**

- `makeSound()` in `Animal` is **virtual**, allowing dynamic method binding.
- The base class pointer (`a`) **calls the overridden function in `Dog`** at runtime.

### **Key Differences Between Compile-Time & Run-Time Polymorphism**

| Feature            | **Compile-Time Polymorphism**              | **Run-Time Polymorphism**                 |
| ------------------ | ------------------------------------------ | ----------------------------------------- |
| **Binding Time**   | Compile-time                               | Runtime                                   |
| **Achieved Using** | Function Overloading, Operator Overloading | Virtual Functions (Method Overriding)     |
| **Performance**    | Faster (determined at compile-time)        | Slightly slower (requires runtime lookup) |
| **Flexibility**    | Less flexible (fixed at compile-time)      | More flexible (resolved at runtime)       |

### **Summary Table**

| **Type**                 | **Example**                                                 | **Binding Type** |
| ------------------------ | ----------------------------------------------------------- | ---------------- |
| **Function Overloading** | `void add(int); void add(int, int);`                        | Compile-time     |
| **Operator Overloading** | `Complex operator+(Complex);`                               | Compile-time     |
| **Method Overriding**    | Virtual function in base class, overridden in derived class | Run-time         |

### **🔥 Key Takeaways**

✅ **Polymorphism** allows functions/objects to behave **differently** in different scenarios.  
✅ **Compile-time polymorphism** is **faster** but **less flexible**.  
✅ **Run-time polymorphism** is **slower** but **more dynamic** (useful in OOP design).  
✅ **Virtual functions** enable **runtime method overriding** using **base class pointers**.

---

## **`Gagan Saini`**
