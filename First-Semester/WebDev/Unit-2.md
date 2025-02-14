# Unit-2

## **JavaScript Basics**

### **Introduction to JavaScript**

JavaScript is a lightweight, interpreted programming language used to create dynamic web pages. It allows developers to implement complex features such as interactivity, animations, and real-time updates on web pages.

Key features of JavaScript:

- **Client-side scripting**: Runs in the browser.
- **Interpreted language**: Does not require compilation.
- **Event-driven**: Executes based on user interactions.
- **Supports Object-Oriented Programming (OOP)**.
- **Can manipulate HTML and CSS dynamically**.

### **JavaScript Operators**

Operators in JavaScript are symbols used to perform operations on variables and values.

1. **Arithmetic Operators**

   ```js
   let a = 10,
     b = 5;
   console.log(a + b); // Addition: 15
   console.log(a - b); // Subtraction: 5
   console.log(a * b); // Multiplication: 50
   console.log(a / b); // Division: 2
   console.log(a % b); // Modulus: 0
   console.log(a ** b); // Exponentiation: 100000
   ```

2. **Assignment Operators**

   ```js
   let x = 10;
   x += 5; // x = x + 5
   x -= 3; // x = x - 3
   x *= 2; // x = x * 2
   x /= 4; // x = x / 4
   ```

3. **Comparison Operators**

   ```js
   console.log(10 == "10"); // true (loose equality)
   console.log(10 === "10"); // false (strict equality)
   console.log(10 != 5); // true
   console.log(10 > 5); // true
   console.log(10 < 5); // false
   ```

4. **Logical Operators**
   ```js
   let a = true,
     b = false;
   console.log(a && b); // false (AND)
   console.log(a || b); // true (OR)
   console.log(!a); // false (NOT)
   ```

### **Conditional Statements**

Conditional statements are used to perform different actions based on different conditions.

1. **if Statement**

   ```js
   let age = 18;
   if (age >= 18) {
     console.log("You are eligible to vote.");
   }
   ```

2. **if-else Statement**

   ```js
   let num = 10;
   if (num % 2 === 0) {
     console.log("Even Number");
   } else {
     console.log("Odd Number");
   }
   ```

3. **if-else if-else Statement**

   ```js
   let marks = 85;
   if (marks >= 90) {
     console.log("Grade A");
   } else if (marks >= 75) {
     console.log("Grade B");
   } else {
     console.log("Grade C");
   }
   ```

4. **Switch Statement**
   ```js
   let day = "Monday";
   switch (day) {
     case "Monday":
       console.log("Start of the week!");
       break;
     case "Friday":
       console.log("Weekend is coming!");
       break;
     default:
       console.log("Normal day");
   }
   ```

### **Loop Statements**

Loops in JavaScript are used to execute a block of code multiple times.

1. **for Loop**

   ```js
   for (let i = 1; i <= 5; i++) {
     console.log("Iteration " + i);
   }
   ```

2. **while Loop**

   ```js
   let count = 1;
   while (count <= 5) {
     console.log("Count: " + count);
     count++;
   }
   ```

3. **do-while Loop**

   ```js
   let n = 1;
   do {
     console.log("Number: " + n);
     n++;
   } while (n <= 5);
   ```

4. **forEach Loop (Array Iteration)**

   ```js
   let numbers = [1, 2, 3, 4, 5];
   numbers.forEach(function (num) {
     console.log(num);
   });
   ```

5. **for...in Loop (Iterate over Object Properties)**

   ```js
   let person = { name: "John", age: 30, city: "New York" };
   for (let key in person) {
     console.log(key + ": " + person[key]);
   }
   ```

6. **for...of Loop (Iterate over Arrays & Strings)**
   ```js
   let fruits = ["Apple", "Banana", "Cherry"];
   for (let fruit of fruits) {
     console.log(fruit);
   }
   ```

---

## **Functions in JavaScript**

A function in JavaScript is a reusable block of code that performs a specific task. It allows modular programming, code reusability, and better maintainability.

### **Declaring a Function**

A function is defined using the `function` keyword, followed by a name and parentheses `()`. The code to be executed is written inside curly braces `{}`.

```js
function greet() {
  console.log("Hello, welcome to JavaScript!");
}
greet(); // Function call
```

### **Types of Functions in JavaScript**

1. **Function Declaration (Named Function)**  
   A function that is declared using the `function` keyword and has a name.

   ```js
   function add(a, b) {
     return a + b;
   }
   console.log(add(5, 3)); // Output: 8
   ```

2. **Function Expression (Anonymous Function)**  
   A function stored in a variable. It doesn't have a name.

   ```js
   const multiply = function (a, b) {
     return a * b;
   };
   console.log(multiply(4, 5)); // Output: 20
   ```

3. **Arrow Function (ES6 Feature)**  
   A shorter syntax for writing functions using `=>`.

   ```js
   const subtract = (a, b) => a - b;
   console.log(subtract(10, 4)); // Output: 6
   ```

   **Example with multiple statements:**

   ```js
   const greetUser = (name) => {
     console.log("Hello, " + name);
   };
   greetUser("Alice"); // Output: Hello, Alice
   ```

4. **Immediately Invoked Function Expression (IIFE)**  
   A function that runs immediately after it is defined.

   ```js
   (function () {
     console.log("This is an IIFE function.");
   })();
   ```

   **With parameters:**

   ```js
   (function (name) {
     console.log("Hello, " + name);
   })("John"); // Output: Hello, John
   ```

5. **Higher-Order Function**  
   A function that takes another function as an argument or returns a function.

   ```js
   function operate(a, b, func) {
     return func(a, b);
   }
   console.log(operate(10, 5, (x, y) => x * y)); // Output: 50
   ```

6. **Callback Function**  
   A function that is passed as an argument and executed later.

   ```js
   function fetchData(callback) {
     console.log("Fetching data...");
     callback(); // Calls the function passed as an argument
   }

   function displayData() {
     console.log("Data received!");
   }

   fetchData(displayData);
   ```

7. **Recursive Function**  
   A function that calls itself.

   ```js
   function factorial(n) {
     if (n === 0) return 1;
     return n * factorial(n - 1);
   }
   console.log(factorial(5)); // Output: 120
   ```

8. **Generator Function (`function*`)**  
   A function that can pause and resume execution using `yield`.

   ```js
   function* countUp() {
     let i = 1;
     while (i <= 3) {
       yield i++;
     }
   }

   const counter = countUp();
   console.log(counter.next().value); // 1
   console.log(counter.next().value); // 2
   console.log(counter.next().value); // 3
   ```

---

## **JavaScript and Objects**

In JavaScript, an object is a collection of properties, where each property is a key-value pair. Objects allow us to store, manipulate, and organize data efficiently.

### **Creating Objects**

1. **Using Object Literals**

   ```js
   let person = {
     name: "John",
     age: 30,
     city: "New York",
     greet: function () {
       console.log("Hello, " + this.name);
     },
   };
   console.log(person.name); // John
   person.greet(); // Hello, John
   ```

2. **Using the `new Object()` Constructor**

   ```js
   let car = new Object();
   car.brand = "Toyota";
   car.model = "Corolla";
   car.year = 2022;
   console.log(car.brand); // Toyota
   ```

3. **Using a Constructor Function**

   ```js
   function Person(name, age) {
     this.name = name;
     this.age = age;
   }
   let p1 = new Person("Alice", 25);
   console.log(p1.name); // Alice
   ```

4. **Using Class (ES6)**
   ```js
   class Animal {
     constructor(name, species) {
       this.name = name;
       this.species = species;
     }
   }
   let cat = new Animal("Whiskers", "Cat");
   console.log(cat.name); // Whiskers
   ```

---

## **Commonly Used Objects in JavaScript**

JavaScript has built-in objects that are commonly used:

1. **Math Object** (for mathematical calculations)

   ```js
   console.log(Math.PI); // 3.141592653589793
   console.log(Math.sqrt(16)); // 4
   console.log(Math.random()); // Random number between 0 and 1
   ```

2. **Date Object** (for handling dates and time)

   ```js
   let today = new Date();
   console.log(today.toDateString()); // Example: Mon Feb 14 2025
   console.log(today.getFullYear()); // Example: 2025
   ```

3. **String Object** (for string manipulation)

   ```js
   let text = "JavaScript";
   console.log(text.length); // 10
   console.log(text.toUpperCase()); // JAVASCRIPT
   console.log(text.includes("Script")); // true
   ```

4. **Array Object** (for handling lists of data)

   ```js
   let fruits = ["Apple", "Banana", "Cherry"];
   console.log(fruits.length); // 3
   fruits.push("Orange"); // Add an element
   console.log(fruits); // ["Apple", "Banana", "Cherry", "Orange"]
   ```

5. **JSON Object** (for handling JSON data)
   ```js
   let obj = { name: "John", age: 30 };
   let jsonStr = JSON.stringify(obj);
   console.log(jsonStr); // '{"name":"John","age":30}'
   ```

---

## **The DOM & Web Browser Environment**

The **Document Object Model (DOM)** is an interface that allows JavaScript to interact with and manipulate HTML documents.

### **Accessing Elements in the DOM**

1. **By ID**

   ```js
   let element = document.getElementById("title");
   console.log(element.textContent);
   ```

2. **By Class Name**

   ```js
   let elements = document.getElementsByClassName("myClass");
   console.log(elements[0].innerHTML);
   ```

3. **By Tag Name**

   ```js
   let paragraphs = document.getElementsByTagName("p");
   console.log(paragraphs[0].innerText);
   ```

4. **By Query Selector**
   ```js
   let element = document.querySelector(".myClass");
   console.log(element.innerHTML);
   ```

### **Modifying the DOM**

1. **Changing Content**

   ```js
   document.getElementById("title").textContent = "New Title";
   ```

2. **Changing Styles**

   ```js
   document.getElementById("title").style.color = "blue";
   ```

3. **Adding New Elements**
   ```js
   let newPara = document.createElement("p");
   newPara.textContent = "This is a new paragraph.";
   document.body.appendChild(newPara);
   ```

### **Handling Events**

1. **Click Event**

   ```js
   document.getElementById("btn").addEventListener("click", function () {
     alert("Button clicked!");
   });
   ```

2. **Mouseover Event**
   ```js
   document.getElementById("box").addEventListener("mouseover", function () {
     this.style.backgroundColor = "yellow";
   });
   ```

### **Forms & Validation**

Forms in JavaScript are used to take user input. Validation ensures that the data entered is correct.

#### **Accessing Form Elements**

```js
let name = document.getElementById("name").value;
console.log(name);
```

#### **Simple Form Validation**

```html
<form onsubmit="return validateForm()">
  <input type="text" id="username" placeholder="Enter username" />
  <input type="submit" value="Submit" />
</form>

<script>
  function validateForm() {
    let username = document.getElementById("username").value;
    if (username === "") {
      alert("Username cannot be empty");
      return false;
    }
    return true;
  }
</script>
```

#### **Validating Email Format**

```js
function validateEmail() {
  let email = document.getElementById("email").value;
  let pattern = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;
  if (!email.match(pattern)) {
    alert("Invalid email address");
    return false;
  }
  return true;
}
```

#### **Preventing Form Submission on Invalid Input**

```js
document.getElementById("myForm").addEventListener("submit", function (event) {
  let password = document.getElementById("password").value;
  if (password.length < 6) {
    alert("Password must be at least 6 characters long");
    event.preventDefault();
  }
});
```

### **Conclusion**

- JavaScript **objects** store and manipulate data.
- Commonly used objects include **Math, Date, String, Array, and JSON**.
- The **DOM** allows JavaScript to interact with HTML.
- The **Web Browser Environment** provides features like window, document, and events.
- **Forms & Validation** ensure correct user input in web applications.

---

## **DHTML (Dynamic HTML)**

**Dynamic HTML (DHTML)** is a combination of **HTML, CSS, JavaScript, and the DOM** that allows web pages to be interactive and dynamic without requiring a page reload.

### **Key Features of DHTML:**

- Allows real-time content updates
- Enables animations and effects using CSS & JavaScript
- Enhances user interaction through event handling
- Controls the appearance and behavior of elements dynamically

### **Combining HTML, CSS & JavaScript**

DHTML uses **HTML for structure**, **CSS for styling**, and **JavaScript for interactivity**.

#### **Example: Changing Text & Style Dynamically**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>DHTML Example</title>
    <style>
      #text {
        font-size: 20px;
        color: black;
      }
    </style>
  </head>
  <body>
    <p id="text">This is a sample text.</p>
    <button onclick="changeText()">Click Me</button>

    <script>
      function changeText() {
        let textElement = document.getElementById("text");
        textElement.textContent = "Text has changed!";
        textElement.style.color = "blue";
      }
    </script>
  </body>
</html>
```

**What happens?**

- Clicking the button changes the text and color dynamically using JavaScript.

### **Events & Buttons**

**Events** allow JavaScript to react to user interactions like **clicks, mouse movements, keyboard inputs, etc.**

#### **Common Events in JavaScript:**

| Event         | Description                             |
| ------------- | --------------------------------------- |
| `onclick`     | Fires when an element is clicked        |
| `onmouseover` | Fires when the mouse is over an element |
| `onmouseout`  | Fires when the mouse leaves an element  |
| `onkeydown`   | Fires when a key is pressed             |
| `onload`      | Fires when the page loads               |

#### **Example: Handling Button Clicks**

```html
<button id="btn">Click Me</button>
<p id="msg"></p>

<script>
  document.getElementById("btn").addEventListener("click", function () {
    document.getElementById("msg").textContent = "Button Clicked!";
  });
</script>
```

### **Controlling the Browser**

JavaScript provides several ways to **interact with and control the browser** using the `window` object.

#### **1. Alert, Confirm, and Prompt Dialogs**

```js
alert("Hello, this is an alert!"); // Displays an alert box
let userConfirmed = confirm("Are you sure?"); // Displays a confirmation box
let userInput = prompt("Enter your name:"); // Takes input from the user
```

#### **2. Opening and Closing Windows**

```js
let newWin = window.open(
  "https://www.google.com",
  "_blank",
  "width=500,height=500"
); // Opens a new window
newWin.close(); // Closes the new window
```

#### **3. Navigating the Browser History**

```js
window.history.back(); // Go back to the previous page
window.history.forward(); // Go forward to the next page
```

#### **4. Getting and Setting URL Information**

```js
console.log(window.location.href); // Get current URL
window.location.href = "https://www.example.com"; // Redirect to another page
```

### **Conclusion**

- **DHTML** combines **HTML, CSS, JavaScript, and the DOM** to create interactive web pages.
- **Events & Buttons** allow user interactions to trigger actions.
- **JavaScript can control the browser** by managing windows, history, and navigation.

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

> Thanks Sumit for your valuable contribution and time.

---

## **`Gagan Saini`**
