# Unit-3

## Normalization

Normalization in **DBMS** is the process of organizing data in a database to minimize **redundancy** and **dependency** by dividing large tables into smaller ones and defining relationships between them. The main goal is to eliminate anomalies (insertion, update, and deletion anomalies) and ensure data integrity.

### **Forms of Normalization**

1. **First Normal Form (1NF)** – Eliminates duplicate columns and ensures atomicity (each column contains indivisible values).
2. **Second Normal Form (2NF)** – Ensures **1NF** and removes **partial dependency** (a non-key attribute should depend on the entire primary key, not just a part of it).
3. **Third Normal Form (3NF)** – Ensures **2NF** and removes **transitive dependency** (non-key attributes should not depend on other non-key attributes).
4. **Boyce-Codd Normal Form (BCNF)** – A stricter version of **3NF**, ensuring no redundancy due to functional dependencies.
5. **Fourth (4NF) and Fifth (5NF) Normal Forms** – Handle multi-valued dependencies and further decomposition for eliminating redundancy.

Normalization helps improve **data consistency, scalability, and efficiency** in relational databases.

### **Functional Dependencies in Normalization**

**Functional Dependency (FD)** is a key concept in database normalization. It defines a relationship between attributes in a relational database, ensuring that one attribute uniquely determines another.

### **Definition:**

A functional dependency **X → Y** means that if two tuples have the same value for attribute **X**, they must also have the same value for attribute **Y**.  
Here, **X** is called the **determinant**, and **Y** is the **dependent attribute**.

### **Types of Functional Dependencies:**

1. **Trivial Functional Dependency:**

   - If **Y** is a subset of **X**, then **X → Y** is trivial.
   - Example: `{Student_ID, Name} → Name` (since Name is already part of the left side).

2. **Non-Trivial Functional Dependency:**

   - If **Y** is not a subset of **X**, then **X → Y** is non-trivial.
   - Example: `Student_ID → Name` (Student_ID determines Name, but Name is not part of Student_ID).

3. **Partial Functional Dependency:**

   - A non-key attribute is dependent on a **part** of the **composite primary key**.
   - Example: In a table with `{Student_ID, Course_ID} → Grade`, if `Student_ID → Student_Name`, it's a **partial dependency** (violates 2NF).

4. **Transitive Functional Dependency:**

   - If `X → Y` and `Y → Z`, then `X → Z` is a **transitive dependency**.
   - Example: `Student_ID → Department_ID` and `Department_ID → Department_Name` implies `Student_ID → Department_Name` (violates 3NF).

5. **Multivalued Dependency (MVD):**

   - If **X →→ Y**, then for each **X**, there is a set of values in **Y**, independent of other attributes.
   - Example: `Student_ID →→ Phone_Number` (a student can have multiple phone numbers, requiring 4NF).

6. **Join Dependency:**
   - If a table can be decomposed into smaller tables without losing information, it exhibits **join dependency** (used in 5NF).
   - Example: If a relation **R(A, B, C)** can be split into **R1(A, B)** and **R2(B, C)** without loss, it has a join dependency.

### **Role of Functional Dependencies in Normalization:**

- **1NF:** Eliminates repeating groups and ensures atomicity.
- **2NF:** Removes **partial dependencies**.
- **3NF:** Removes **transitive dependencies**.
- **BCNF:** Ensures no redundancy due to functional dependencies.
- **4NF & 5NF:** Eliminate **multivalued** and **join dependencies** for further optimization.

Understanding functional dependencies helps design efficient, consistent, and anomaly-free databases. 🚀

### **Introduction to PL/SQL**

**PL/SQL (Procedural Language/Structured Query Language)** is Oracle’s extension of SQL that allows procedural programming, including loops, conditions, functions, and exception handling. It enhances SQL by providing features such as **variables, control structures, procedures, and triggers**, making it more powerful for database applications.

### **Key Features of PL/SQL:**

- **Procedural Capabilities** – Supports loops, conditions, and functions.
- **Block Structure** – Code is organized into **PL/SQL blocks**.
- **Error Handling** – Built-in **exception handling** for runtime errors.
- **Improved Performance** – Reduces **network traffic** by sending multiple SQL statements at once.
- **Security** – Can be used to create **stored procedures** that encapsulate business logic.

---

## **Structure of a PL/SQL Block**

A **PL/SQL block** is the basic unit of PL/SQL programming. It consists of three main sections:

### **1. Declaration Section (Optional)**

- Declares **variables, constants, records, and cursors**.
- Starts with the keyword `DECLARE`.

### **2. Execution Section (Mandatory)**

- Contains SQL and procedural statements.
- Begins with `BEGIN` and ends with `END;`.

### **3. Exception Handling Section (Optional)**

- Handles **runtime errors** using the `EXCEPTION` keyword.

### **PL/SQL Block Syntax:**

```plsql
DECLARE
   -- Variable declarations
   v_employee_name VARCHAR2(50);

BEGIN
   -- SQL and procedural statements
   SELECT employee_name INTO v_employee_name FROM employees WHERE employee_id = 101;
   DBMS_OUTPUT.PUT_LINE('Employee Name: ' || v_employee_name);

EXCEPTION
   -- Error handling
   WHEN NO_DATA_FOUND THEN
      DBMS_OUTPUT.PUT_LINE('No employee found!');
   WHEN OTHERS THEN
      DBMS_OUTPUT.PUT_LINE('Some error occurred!');
END;
/
```

---

## **Types of PL/SQL Blocks**

1. **Anonymous Block** – A block that does not have a name and is executed instantly.
2. **Named Blocks** – These include:
   - **Procedures** – Stored programs that perform specific tasks.
   - **Functions** – Return a value and can be used in SQL statements.
   - **Triggers** – Automatic execution on specific events (e.g., `BEFORE INSERT`).
   - **Packages** – Groups related procedures and functions.

---

### **Advantages of PL/SQL**

✔ **Reduces network traffic**  
✔ **Improves execution speed**  
✔ **Ensures better security and control**  
✔ **Supports modular programming**

PL/SQL is widely used in **database-driven applications** where business logic needs to be executed at the database level efficiently. 🚀

# **PL/SQL Language**

PL/SQL (Procedural Language/Structured Query Language) is Oracle’s procedural extension of SQL, allowing programming capabilities like variables, loops, conditions, and error handling within SQL statements.

---

## **1. Operators in PL/SQL**

PL/SQL supports various operators for performing arithmetic, comparison, logical, and string operations.

### **Types of Operators**

| **Operator Type** | **Example**           | **Description**                   |
| ----------------- | --------------------- | --------------------------------- |
| **Arithmetic**    | `+, -, *, /, MOD`     | Performs mathematical operations. |
| **Comparison**    | `=, !=, >, <, >=, <=` | Used for comparing values.        |
| **Logical**       | `AND, OR, NOT`        | Used in conditional statements.   |
| **Concatenation** | `Symbol or OR`        | Joins two strings together.       |
| **Assignment**    | `:=`                  | Assigns a value to a variable.    |

**Example:**

```plsql
DECLARE
   num1 NUMBER := 10;
   num2 NUMBER := 5;
   result NUMBER;
BEGIN
   result := num1 + num2;
   DBMS_OUTPUT.PUT_LINE('Sum: ' || result);
END;
/
```

---

## **2. Control Structures in PL/SQL**

PL/SQL provides control structures to handle decision-making and looping.

### **Conditional Statements:**

- **IF-THEN**
- **IF-THEN-ELSE**
- **IF-THEN-ELSIF**
- **CASE Statement**

**Example (IF-THEN-ELSE):**

```plsql
DECLARE
   age NUMBER := 18;
BEGIN
   IF age >= 18 THEN
      DBMS_OUTPUT.PUT_LINE('Eligible to Vote');
   ELSE
      DBMS_OUTPUT.PUT_LINE('Not Eligible to Vote');
   END IF;
END;
/
```

### **Looping Statements:**

- **LOOP (Basic Loop)**
- **WHILE LOOP**
- **FOR LOOP**

**Example (FOR LOOP):**

```plsql
BEGIN
   FOR i IN 1..5 LOOP
      DBMS_OUTPUT.PUT_LINE('Iteration: ' || i);
   END LOOP;
END;
/
```

---

## **3. Cursors in PL/SQL**

A **cursor** is a pointer to a result set of a SQL query, used for row-by-row processing.

### **Types of Cursors:**

1. **Implicit Cursor** – Automatically created for SQL queries like `SELECT` and `UPDATE`.
2. **Explicit Cursor** – Defined by the user for complex query processing.

**Example (Explicit Cursor):**

```plsql
DECLARE
   CURSOR emp_cursor IS SELECT employee_name FROM employees;
   v_emp_name employees.employee_name%TYPE;
BEGIN
   OPEN emp_cursor;
   LOOP
      FETCH emp_cursor INTO v_emp_name;
      EXIT WHEN emp_cursor%NOTFOUND;
      DBMS_OUTPUT.PUT_LINE('Employee: ' || v_emp_name);
   END LOOP;
   CLOSE emp_cursor;
END;
/
```

---

## **4. Triggers in PL/SQL**

A **trigger** is a stored PL/SQL block that automatically executes in response to certain database events.

### **Types of Triggers:**

- **Before Trigger** – Executes before an event (`INSERT`, `UPDATE`, `DELETE`).
- **After Trigger** – Executes after an event.
- **Instead of Trigger** – Used on views.

**Example (AFTER INSERT Trigger):**

```plsql
CREATE OR REPLACE TRIGGER trg_after_insert
AFTER INSERT ON employees
FOR EACH ROW
BEGIN
   DBMS_OUTPUT.PUT_LINE('New Employee Added: ' || :NEW.employee_name);
END;
/
```

---

## **5. Procedures in PL/SQL**

A **procedure** is a named PL/SQL block that performs a specific task but does not return a value.

### **Syntax:**

```plsql
CREATE OR REPLACE PROCEDURE get_employee (emp_id IN NUMBER) AS
   v_name employees.employee_name%TYPE;
BEGIN
   SELECT employee_name INTO v_name FROM employees WHERE employee_id = emp_id;
   DBMS_OUTPUT.PUT_LINE('Employee Name: ' || v_name);
END;
/
```

### **Calling the Procedure:**

```plsql
BEGIN
   get_employee(101);
END;
/
```

---

## **6. Functions in PL/SQL**

A **function** is similar to a procedure but always returns a value.

### **Syntax:**

```plsql
CREATE OR REPLACE FUNCTION get_salary (emp_id IN NUMBER) RETURN NUMBER AS
   v_salary employees.salary%TYPE;
BEGIN
   SELECT salary INTO v_salary FROM employees WHERE employee_id = emp_id;
   RETURN v_salary;
END;
/
```

### **Calling the Function:**

```plsql
DECLARE
   salary NUMBER;
BEGIN
   salary := get_salary(101);
   DBMS_OUTPUT.PUT_LINE('Salary: ' || salary);
END;
/
```

---

### **Summary of PL/SQL Components**

| **Component**          | **Description**                                                     |
| ---------------------- | ------------------------------------------------------------------- |
| **Operators**          | Arithmetic, Logical, Comparison, String, and Assignment operators.  |
| **Control Structures** | IF-ELSE, CASE, FOR, WHILE, and basic LOOP.                          |
| **Cursors**            | Used for handling multiple records (Implicit and Explicit Cursors). |
| **Triggers**           | Auto-executed PL/SQL blocks triggered by DML events.                |
| **Procedures**         | Named PL/SQL blocks performing a task, do not return values.        |
| **Functions**          | Similar to procedures but return a value.                           |

PL/SQL is essential for developing robust, efficient, and secure database applications. 🚀

## **`Gagan Saini`**
