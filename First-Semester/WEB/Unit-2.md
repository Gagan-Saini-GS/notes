# **Comprehensive JavaScript & DHTML Notes**

## **1. Introduction to JavaScript**

JavaScript is a **high-level, interpreted, object-oriented, event-driven** programming language primarily used for **client-side web development**. It enables interactivity on web pages and can also be used for backend development with environments like **Node.js**.

### **Key Features of JavaScript**

- **Interpreted Language**: Runs directly in the browser without compilation.
- **Object-Oriented**: Uses objects for data structuring and functionality.
- **Event-Driven**: Reacts to user interactions like clicks, inputs, etc.
- **Cross-Platform**: Runs on various browsers and operating systems.
- **Asynchronous Processing**: Supports AJAX, Promises, and Fetch API for background tasks.

```js
console.log("Hello, JavaScript!"); // Outputs in the console
alert("Welcome to JavaScript!"); // Shows an alert box
```

---

## **2. JavaScript Object Data Types**

JavaScript provides several **object-based** data types:

### **1. Object**

Objects store key-value pairs.

```js
let person = {
  name: "Alice",
  age: 25,
  greet: function () {
    return "Hello, " + this.name;
  },
};
console.log(person.greet()); // "Hello, Alice"
```

### **2. Array**

An array is a collection of values.

```js
let fruits = ["Apple", "Banana", "Mango"];
console.log(fruits[1]); // "Banana"
```

### **3. Date Object**

Represents a date and time.

```js
let now = new Date();
console.log(now.toDateString()); // "Mon Feb 12 2024"
```

### **4. Math Object**

Used for mathematical calculations.

```js
console.log(Math.PI); // 3.141592653589793
console.log(Math.sqrt(25)); // 5
```

### **5. JSON Object**

JSON (JavaScript Object Notation) is used for data exchange.

```js
let jsonData = '{"name": "John", "age": 30}';
let obj = JSON.parse(jsonData); // Converts JSON to JavaScript object
console.log(obj.name); // "John"
```

---

## **3. JavaScript Operators**

### **Arithmetic Operators**

```js
let a = 10,
  b = 5;
console.log(a + b); // 15
console.log(a - b); // 5
console.log(a * b); // 50
console.log(a / b); // 2
console.log(a % b); // 0 (Remainder)
```

### **Comparison Operators**

```js
console.log(10 > 5); // true
console.log(10 == "10"); // true (loose comparison)
console.log(10 === "10"); // false (strict comparison)
```

### **Logical Operators**

```js
console.log(true && false); // false
console.log(true || false); // true
console.log(!true); // false
```

---

## **4. Loops in JavaScript**

### **1. for Loop**

```js
for (let i = 1; i <= 5; i++) {
  console.log(i);
}
```

### **2. forEach Loop** (For arrays)

```js
let numbers = [1, 2, 3];
numbers.forEach((num) => console.log(num));
```

### **3. for-in Loop** (For objects)

```js
let person = { name: "Alice", age: 25 };
for (let key in person) {
  console.log(key + ": " + person[key]);
}
```

### **4. for-of Loop** (For iterables)

```js
let colors = ["Red", "Blue"];
for (let color of colors) {
  console.log(color);
}
```

### **5. while Loop**

```js
let i = 1;
while (i <= 5) {
  console.log(i);
  i++;
}
```

### **6. do-while Loop**

```js
let i = 1;
do {
  console.log(i);
  i++;
} while (i <= 5);
```

---

## **5. JavaScript Functions**

### **1. Function Declaration**

```js
function greet(name) {
  return "Hello, " + name;
}
console.log(greet("Alice")); // "Hello, Alice"
```

### **2. Arrow Function**

```js
const greet = (name) => `Hello, ${name}`;
console.log(greet("Bob"));
```

### **3. Anonymous Function**

```js
let add = function (a, b) {
  return a + b;
};
console.log(add(5, 3)); // 8
```

---

## **6. JavaScript and the DOM**

### **What is DOM?**

The Document Object Model (DOM) represents the structure of a web page and allows JavaScript to interact with it.

### **Manipulating the DOM**

```js
document.getElementById("demo").innerHTML = "Hello DOM!";
document.querySelector("p").style.color = "blue";
```

---

## **7. Forms and Validations**

### **Example: Form Validation**

```js
function validateForm() {
  let x = document.forms["myForm"]["fname"].value;
  if (x == "") {
    alert("Name must be filled out");
    return false;
  }
}
```

---

## **8. DHTML (Dynamic HTML)**

DHTML is a combination of **HTML, CSS, and JavaScript** used to create interactive web pages.

### **DHTML Features**

- Dynamic content updates
- Interactive buttons and forms
- Animations and effects

### **Example: Changing Text Color**

```js
function changeColor() {
  document.getElementById("text").style.color = "red";
}
```

### **Handling Events in DHTML**

```js
document.getElementById("myButton").onclick = function () {
  alert("Button Clicked!");
};
```

### **Controlling the Browser with JavaScript**

```js
window.open("https://www.google.com", "_blank"); // Opens a new tab
window.close(); // Closes the window
```

---

## **9. JSON Functions in JavaScript**

### **1. JSON.stringify()**

Converts an object into a JSON string.

```js
let person = { name: "John", age: 30 };
let jsonStr = JSON.stringify(person);
console.log(jsonStr); // '{"name":"John","age":30}'
```

### **2. JSON.parse()**

Converts a JSON string back into an object.

```js
let jsonData = '{"name": "John", "age": 30}';
let obj = JSON.parse(jsonData);
console.log(obj.name); // "John"
```

---

## **Exam Questions**

### **2-Marks Questions**

1. Define JavaScript.
2. What is DHTML?
3. What is the DOM?
4. What is JSON?
5. List any four JavaScript operators.
6. Define a function in JavaScript.
7. What is the difference between `==` and `===`?
8. What does `document.getElementById()` do?
9. What is an event in JavaScript?

### **4-Marks Questions**

1. Explain different types of loops in JavaScript with examples.
2. What is an object in JavaScript?
3. List and explain three JavaScript functions.
4. What are objects in JavaScript? Give an example.
5. How does JavaScript handle user events? Provide an example.
6. Explain the use of the `switch` statement with an example.
7. Explain the different ways to declare a function in JavaScript.

### **8-Marks Questions**

1. Discuss the various types of loops in JavaScript with code examples.
2. Discuss JavaScript functions with types.
3. Explain form validation in JavaScript.
4. Write and explain JSON.stringify() and JSON.parse().
5. Explain JavaScript, including its features, uses, and examples.
6. Explain conditional statements in JavaScript with multiple examples.
7. Explain JavaScript objects and their importance with detailed examples.
8. What is the DOM? Explain how JavaScript can interact with HTML elements using the DOM.
9. Discuss JavaScript event handling with practical examples.
10. Explain the working of form validation in JavaScript with a complete example.
11. What is DHTML? Explain its components and how JavaScript enhances web interactivity.
12. Describe how JavaScript interacts with the browser and controls navigation.
13. Write a JavaScript program demonstrating all key concepts such as loops, functions, and objects.

---
