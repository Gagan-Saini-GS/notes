# Unit-2

## Relational Data Model

The **Relational Data Model** is a widely used data model in **Database Management Systems (DBMS)** that organizes data into **tables (relations)**. It was introduced by **E.F. Codd** in 1970 and is the foundation of **Relational Database Management Systems (RDBMS)** like MySQL, PostgreSQL, and Oracle.

### **Key Concepts of the Relational Data Model:**

1. **Relation (Table):** A relation is a collection of tuples (rows) that share the same attributes (columns). Each relation has a unique name.
2. **Tuple (Row):** A tuple represents a single record in a relation.
3. **Attribute (Column):** Attributes define the properties or fields of a relation.
4. **Domain:** A domain specifies the set of allowed values for an attribute.
5. **Primary Key:** A unique identifier for each tuple in a relation.
6. **Foreign Key:** An attribute in one relation that refers to the primary key of another relation, establishing a relationship between tables.
7. **Schema:** The structure of a relation, including its attributes and constraints.
8. **Constraints:** Rules to maintain data integrity, such as:
   - **Entity Integrity:** Primary keys cannot be NULL.
   - **Referential Integrity:** Foreign keys must reference valid primary keys.
   - **Domain Constraints:** Attribute values must be within a specified domain.

### **Advantages of the Relational Data Model:**

- **Simplicity:** Data is organized in a tabular format, making it easy to understand.
- **Flexibility:** New data can be added without major changes.
- **Data Integrity:** Constraints ensure accuracy and consistency.
- **Query Optimization:** SQL (Structured Query Language) allows efficient data retrieval and manipulation.
- **Normalization:** The relational model supports normalization, which organizes data into multiple tables to eliminate redundancy and improve data consistency. This reduces anomalies and ensures efficient storage.

### **Example of a Relational Database:**

Let's consider a simple relational database for a **Student Management System** with two tables: **Students** and **Courses**.

#### **Students Table**

| Student_ID (PK) | Name   | Age | Course_ID (FK) |
| --------------- | ------ | --- | -------------- |
| 101             | Gagan  | 22  | C001           |
| 102             | Gunjan | 21  | C002           |
| 103             | Sumit  | 21  | C003           |

#### **Courses Table**

| Course_ID (PK) | Course_Name       | Credits |
| -------------- | ----------------- | ------- |
| C001           | DSA               | 3       |
| C002           | Database          | 4       |
| C003           | Web Dev           | 3       |
| C004           | Computer Networks | 3       |
| C005           | Math              | 3       |
| C006           | Project Managment | 3       |

### **Explanation:**

1. **Primary Key (PK):**

   - `Student_ID` is the primary key for the **Students** table.
   - `Course_ID` is the primary key for the **Courses** table.

2. **Foreign Key (FK):**
   - `Course_ID` in the **Students** table is a foreign key referencing `Course_ID` in the **Courses** table.
   - This establishes a relationship between students and their respective courses.

### **SQL Example:**

- Creating the **Students** table:
  ```sql
  CREATE TABLE Students (
      Student_ID INT PRIMARY KEY,
      Name VARCHAR(50),
      Age INT,
      Course_ID VARCHAR(10),
      FOREIGN KEY (Course_ID) REFERENCES Courses(Course_ID)
  );
  ```
- Creating the **Courses** table:
  ```sql
  CREATE TABLE Courses (
      Course_ID VARCHAR(10) PRIMARY KEY,
      Course_Name VARCHAR(50),
      Credits INT
  );
  ```

The **Relational Data Model** provides a structured and efficient way to organize data using relations (tables). By defining **keys, constraints, and relationships**, it ensures data consistency, integrity, and easy retrieval using **SQL**.

## **Advantages of the Relational Data Model**

1. **Simplicity** – The tabular structure is easy to understand and use.
2. **Data Integrity and Accuracy** – Constraints (like primary keys and foreign keys) help maintain data consistency.
3. **Eliminates Data Redundancy** – Using **normalization**, duplicate data is minimized, reducing storage needs.
4. **Scalability** – RDBMS can handle large amounts of data efficiently.
5. **Data Security** – Provides authorization and access control mechanisms to protect sensitive data.
6. **Flexibility** – Easy to modify or extend databases without affecting existing applications.
7. **Powerful Query Language (SQL)** – SQL allows for complex queries, making data retrieval and manipulation easier.
8. **Ensures Referential Integrity** – Foreign keys ensure that relationships between tables remain valid.
9. **Concurrency Control** – Multiple users can work on the database simultaneously without data corruption.
10. **Backup & Recovery Support** – Most RDBMS provide built-in tools for data backup and recovery.

## **Disadvantages of the Relational Data Model**

1. **Complexity in Design** – Creating a well-structured relational database requires expertise in database normalization.
2. **High Hardware and Software Cost** – RDBMS systems require powerful hardware and sometimes costly licenses.
3. **Performance Issues with Large Data** – As the database grows, performance can degrade, requiring indexing and optimization.
4. **Scalability Limitations** – Scaling an RDBMS for massive datasets is more complex compared to NoSQL databases.
5. **Rigid Schema** – Changes to the database schema (like adding new columns) can be challenging and may require modifying existing applications.
6. **Difficult to Manage Relationships in Certain Scenarios** – Complex relationships can make queries slow and harder to optimize.
7. **Increased Storage Requirements** – Normalization reduces redundancy but increases the number of tables, requiring more joins and additional storage.

---

## **Relational Integrity Constraints in DBMS**

Integrity constraints ensure **accuracy, consistency, and reliability** of data in a relational database. The main types of integrity constraints are:

### **1. Entity Integrity Constraint**

- Ensures that each table has a **unique identifier** for every row.
- **Rule:** The **Primary Key (PK) cannot have NULL values** because it uniquely identifies each record.
- **Example:**
  ```sql
  CREATE TABLE Students (
      Student_ID INT PRIMARY KEY,  -- Cannot be NULL
      Name VARCHAR(50),
      Age INT
  );
  ```
- **Violation Example:** Inserting a NULL value in `Student_ID` would violate entity integrity.

### **2. Referential Integrity Constraint**

- Ensures that relationships between tables remain **valid**.
- **Rule:** A **Foreign Key (FK) must reference an existing Primary Key (PK)** in another table or be NULL.
- **Example:**
  ```sql
  CREATE TABLE Students (
      Student_ID INT PRIMARY KEY,
      Name VARCHAR(50),
      Course_ID INT,
      FOREIGN KEY (Course_ID) REFERENCES Courses(Course_ID) -- Referential Integrity
  );
  ```
- **Violation Example:** If `Course_ID` in the **Students** table refers to a non-existent `Course_ID` in the **Courses** table, it violates referential integrity.

### **3. Domain Constraint**

- Ensures that attribute values fall within a **predefined range or type**.
- **Rule:** Each column has a **specific data type and allowed values**.
- **Example:**
  ```sql
  CREATE TABLE Employees (
      Employee_ID INT PRIMARY KEY,
      Salary DECIMAL(10,2) CHECK (Salary > 0), -- Must be positive
      Age INT CHECK (Age BETWEEN 18 AND 65) -- Age restriction
  );
  ```
- **Violation Example:** Inserting `Age = 70` or `Salary = -500` would violate domain constraints.

### **4. Key Constraint**

- Ensures that **each row is uniquely identifiable**.
- **Rule:** A **Primary Key (PK) must have unique values** across all rows.
- **Example:**
  ```sql
  CREATE TABLE Products (
      Product_ID INT PRIMARY KEY, -- Must be unique
      Product_Name VARCHAR(100)
  );
  ```
- **Violation Example:** If two rows have the same `Product_ID`, it violates key constraints.

### **Summary of Relational Integrity Constraints**

| **Constraint Type**       | **Purpose**                                        | **Example Violation**                       |
| ------------------------- | -------------------------------------------------- | ------------------------------------------- |
| **Entity Integrity**      | Primary Key **cannot be NULL**                     | `Student_ID = NULL`                         |
| **Referential Integrity** | Foreign Key **must reference a valid Primary Key** | `Course_ID` refers to a non-existent course |
| **Domain Constraint**     | Values must follow **predefined types/ranges**     | `Age = -5` or `Salary = -1000`              |
| **Key Constraint**        | Primary Key **must be unique**                     | Duplicate `Product_ID`                      |

---

## **Relational Algebra & Relational Calculus in DBMS**

Relational **Algebra** and **Relational Calculus** are **formal query languages** used to retrieve data from relational databases.

### **1. Relational Algebra**

- **Procedural Query Language** – Specifies how to retrieve data step by step.
- Operates on **relations (tables)** to produce another relation.
- Used for **query optimization** in DBMS.
- Fundamental operations include **Selection (σ), Projection (π), Union (∪), Set Difference (-), Cartesian Product (×), and Join (⨝).**

#### **Basic Operations in Relational Algebra**

| **Operation**         | **Symbol** | **Description**                                        |
| --------------------- | ---------- | ------------------------------------------------------ |
| **Selection**         | σ (sigma)  | Filters rows based on conditions.                      |
| **Projection**        | π (pi)     | Selects specific columns.                              |
| **Union**             | ∪          | Combines rows from two relations (removes duplicates). |
| **Set Difference**    | -          | Finds rows present in one table but not the other.     |
| **Cartesian Product** | ×          | Combines all rows from two relations.                  |
| **Join**              | ⨝          | Combines related tuples based on a common attribute.   |

**Example of Relational Algebra Query**

- Given **Students (Student_ID, Name, Age, Course_ID)**
- Find students **older than 21** and **show only their names**:
  ```
  π Name (σ Age > 21 (Students))
  ```
  - **σ Age > 21 (Students)** → Selects students older than 21.
  - **π Name (result)** → Projects only the `Name` column.

### **2. Relational Calculus**

- **Non-Procedural Query Language** – Specifies **what** to retrieve, not **how**.
- Uses **logical predicates** to define conditions for selecting tuples.
- Two types:
  1. **Tuple Relational Calculus (TRC)**
  2. **Domain Relational Calculus (DRC)**

#### **2.1 Tuple Relational Calculus (TRC)**

- Uses **variables that represent tuples**.
- Query format:
  ```
  { t | Condition(t) }
  ```
  - `t` represents a tuple from a relation.
  - The condition specifies criteria for selecting tuples.

**Example of Tuple Relational Calculus**

- Find students older than 21:
  ```
  { t | t ∈ Students ∧ t.Age > 21 }
  ```
  - `t ∈ Students` → `t` is a tuple from the **Students** table.
  - `t.Age > 21` → Selects students older than 21.

#### **2.2 Domain Relational Calculus (DRC)**

- Uses **variables representing column values (domains)**.
- Query format:
  ```
  { <x1, x2, ... xn> | Condition(x1, x2, ... xn) }
  ```
  - `<x1, x2, ... xn>` are **column values** from a relation.
  - The condition defines the selection criteria.

**Example of Domain Relational Calculus**

- Find names of students older than 21:
  ```
  { <N> | ∃S ∈ Students (S.Name = N ∧ S.Age > 21) }
  ```
  - `S ∈ Students` → `S` is a tuple from **Students**.
  - `S.Name = N` → Selects the **Name** attribute.
  - `S.Age > 21` → Filters students older than 21.

### **Comparison: Relational Algebra vs Relational Calculus**

| Feature                | **Relational Algebra**                  | **Relational Calculus**            |
| ---------------------- | --------------------------------------- | ---------------------------------- |
| **Type**               | Procedural                              | Non-Procedural                     |
| **Focus**              | **How** to retrieve data                | **What** data to retrieve          |
| **Operations**         | Uses selection, projection, joins, etc. | Uses logical conditions (TRC, DRC) |
| **Query Optimization** | Helps in query execution                | More abstract                      |

### **Conclusion**

- **Relational Algebra** is **step-by-step (procedural)** and used for **query execution**.
- **Relational Calculus** is **logical (non-procedural)** and used for **query formulation**.
- Both are fundamental to understanding **SQL queries** and **database optimization**.

---

## **Introduction to SQL (Structured Query Language)**

### **What is SQL?**

SQL (**Structured Query Language**) is a **standard language** used to interact with relational databases. It allows users to **store, retrieve, modify, and manage** data efficiently. SQL is used in **RDBMS** (Relational Database Management Systems) like **MySQL, PostgreSQL, SQL Server, Oracle, and SQLite**.

## **Basic SQL Commands**

SQL commands are categorized into **four main types**:

1. **DDL (Data Definition Language)**
2. **DML (Data Manipulation Language)**
3. **DCL (Data Control Language)**
4. **TCL (Transaction Control Language)**

## **1. DDL (Data Definition Language) – Defines Database Structure**

DDL commands deal with **creating, modifying, and deleting database objects** like tables, indexes, and schemas.

> **Key DDL Commands:**
> | **Command** | **Description** |
> |------------|----------------|
> | `CREATE` | Creates a new table, database, or object. |
> | `ALTER` | Modifies an existing table (add/remove columns). |
> | `DROP` | Deletes an entire table or database. |
> | `TRUNCATE` | Removes all records from a table but keeps structure. |

🔹 **Example:** Creating a table

```sql
CREATE TABLE Students (
    Student_ID INT PRIMARY KEY,
    Name VARCHAR(50),
    Age INT
);
```

🔹 **Example:** Modifying a table (adding a new column)

```sql
ALTER TABLE Students ADD Email VARCHAR(100);
```

🔹 **Example:** Deleting a table

```sql
DROP TABLE Students;
```

## **2. DML (Data Manipulation Language) – Works with Data**

DML commands handle **inserting, updating, deleting, and retrieving** data from tables.

> **Key DML Commands:**
> | **Command** | **Description** |
> |------------|----------------|
> | `SELECT` | Retrieves data from a table. |
> | `INSERT` | Adds new records to a table. |
> | `UPDATE` | Modifies existing records. |
> | `DELETE` | Removes specific records from a table. |

🔹 **Example:** Inserting a record

```sql
INSERT INTO Students (Student_ID, Name, Age) VALUES (101, 'Alice', 22);
```

🔹 **Example:** Retrieving data

```sql
SELECT * FROM Students WHERE Age > 21;
```

🔹 **Example:** Updating a record

```sql
UPDATE Students SET Age = 23 WHERE Student_ID = 101;
```

🔹 **Example:** Deleting a record

```sql
DELETE FROM Students WHERE Student_ID = 101;
```

## **3. DCL (Data Control Language) – Manages User Permissions**

DCL commands control **access rights** and **permissions** in a database.

> **Key DCL Commands:**
> | **Command** | **Description** |
> |------------|----------------|
> | `GRANT` | Gives user-specific privileges. |
> | `REVOKE` | Removes previously granted privileges. |

🔹 **Example:** Granting SELECT permission to a user

```sql
GRANT SELECT ON Students TO user1;
```

🔹 **Example:** Revoking permission

```sql
REVOKE SELECT ON Students FROM user1;
```

## **4. TCL (Transaction Control Language) – Manages Transactions**

TCL commands handle **transactions** in SQL to ensure data consistency.

> **Key TCL Commands:**
> | **Command** | **Description** |
> |------------|----------------|
> | `COMMIT` | Saves changes permanently. |
> | `ROLLBACK` | Undoes changes in case of an error. |
> | `SAVEPOINT` | Creates a temporary rollback point. |

🔹 **Example:** Using transaction control

```sql
START TRANSACTION;
UPDATE Students SET Age = 24 WHERE Student_ID = 101;
COMMIT; -- Saves the changes permanently
```

🔹 **Example:** Rolling back a transaction

```sql
START TRANSACTION;
DELETE FROM Students WHERE Age < 18;
ROLLBACK; -- Cancels the delete operation
```

🔹 **Example:** Using SAVEPOINT

```sql
START TRANSACTION;
UPDATE Students SET Age = 25 WHERE Student_ID = 102;
SAVEPOINT save1; -- Creates a rollback point
DELETE FROM Students WHERE Age < 20;
ROLLBACK TO save1; -- Undoes the delete but keeps the update
```

### **Conclusion**

SQL is a powerful language used for **database creation, data retrieval, modification, access control, and transaction management**.

- **DDL** defines database structure.
- **DML** manipulates table data.
- **DCL** controls access permissions.
- **TCL** ensures data integrity using transactions.

## **SQL Data Types, Literals, and Operators**

### **1. SQL Data Types**

SQL data types define the **type of data** that can be stored in a column. Different databases (MySQL, PostgreSQL, SQL Server, Oracle) have slight variations, but the core data types remain the same.

#### **Categories of SQL Data Types**

| **Category**         | **Data Type**                  | **Description**                                |
| -------------------- | ------------------------------ | ---------------------------------------------- |
| **Numeric**          | `INT`, `BIGINT`                | Integer numbers (whole numbers).               |
|                      | `DECIMAL(p,s)`, `NUMERIC(p,s)` | Fixed-point decimal numbers.                   |
|                      | `FLOAT`, `DOUBLE`              | Floating-point numbers (approximate values).   |
| **Character/String** | `CHAR(n)`                      | Fixed-length string (e.g., `CHAR(10)`).        |
|                      | `VARCHAR(n)`                   | Variable-length string (e.g., `VARCHAR(255)`). |
|                      | `TEXT`, `CLOB`                 | Large text data.                               |
| **Date/Time**        | `DATE`                         | Stores date (`YYYY-MM-DD`).                    |
|                      | `TIME`                         | Stores time (`HH:MM:SS`).                      |
|                      | `DATETIME`, `TIMESTAMP`        | Stores date and time.                          |
| **Boolean**          | `BOOLEAN`                      | Stores `TRUE` or `FALSE`.                      |
| **Binary**           | `BLOB`, `VARBINARY`            | Stores binary data (e.g., images, files).      |

🔹 **Example:** Creating a table with different data types

```sql
CREATE TABLE Employees (
    Employee_ID INT PRIMARY KEY,
    Name VARCHAR(50),
    Salary DECIMAL(10,2),
    Hire_Date DATE,
    Is_Active BOOLEAN
);
```

### **2. SQL Literals**

Literals are **constant values** used in SQL statements. They can be of different types:

#### **Types of SQL Literals**

| **Literal Type** | **Example**                  | **Description**                    |
| ---------------- | ---------------------------- | ---------------------------------- |
| **String**       | `'John'`, `'SQL is fun'`     | Enclosed in single quotes.         |
| **Numeric**      | `100`, `3.14`                | Used without quotes.               |
| **Date/Time**    | `'2025-02-06'`, `'12:30:00'` | Stored in `DATE` or `TIME` format. |
| **Boolean**      | `TRUE`, `FALSE`              | Represents logical values.         |

🔹 **Example:** Using literals in an SQL query

```sql
SELECT * FROM Employees WHERE Name = 'John' AND Salary > 5000;
```

### **3. SQL Operators**

SQL operators are used in **conditions and expressions** to manipulate data.

#### **Types of SQL Operators**

#### **A. Arithmetic Operators**

Used for mathematical calculations.  
| **Operator** | **Description** | **Example** (`a = 10`, `b = 5`) |
|------------|----------------|----------------|
| `+` (Addition) | Adds values | `a + b = 15` |
| `-` (Subtraction) | Subtracts values | `a - b = 5` |
| `*` (Multiplication) | Multiplies values | `a * b = 50` |
| `/` (Division) | Divides values | `a / b = 2` |
| `%` (Modulo) | Returns remainder | `a % b = 0` |

🔹 **Example:**

```sql
SELECT Employee_ID, Salary, Salary * 1.10 AS New_Salary FROM Employees;
```

#### **B. Comparison Operators**

Used for filtering rows in `WHERE` clauses.  
| **Operator** | **Description** | **Example** (`a = 10`, `b = 5`) |
|------------|----------------|----------------|
| `=` | Equal to | `a = b` (FALSE) |
| `!=` or `<>` | Not equal to | `a <> b` (TRUE) |
| `>` | Greater than | `a > b` (TRUE) |
| `<` | Less than | `a < b` (FALSE) |
| `>=` | Greater than or equal to | `a >= b` (TRUE) |
| `<=` | Less than or equal to | `a <= b` (FALSE) |

🔹 **Example:**

```sql
SELECT * FROM Employees WHERE Salary >= 5000;
```

#### **C. Logical Operators**

Used for combining conditions in `WHERE` clauses.  
| **Operator** | **Description** | **Example** (`a = 10`, `b = 5`) |
|------------|----------------|----------------|
| `AND` | Both conditions must be TRUE | `a > 5 AND b < 10` (TRUE) |
| `OR` | At least one condition is TRUE | `a > 15 OR b < 10` (TRUE) |
| `NOT` | Negates the condition | `NOT (a > 5)` (FALSE) |

🔹 **Example:**

```sql
SELECT * FROM Employees WHERE Salary > 5000 AND Is_Active = TRUE;
```

#### **D. Special Operators**

Used for pattern matching and value checking.  
| **Operator** | **Description** | **Example** |
|------------|----------------|----------------|
| `BETWEEN` | Checks range of values | `Salary BETWEEN 5000 AND 10000` |
| `IN` | Checks if value exists in a list | `Department IN ('HR', 'IT', 'Sales')` |
| `LIKE` | Matches a pattern | `Name LIKE 'J%'` (Names starting with J) |
| `IS NULL` | Checks for NULL values | `Email IS NULL` |

🔹 **Example:**

```sql
SELECT * FROM Employees WHERE Name LIKE 'A%' AND Salary BETWEEN 3000 AND 8000;
```

---

## **Database Objects in SQL**

Database objects are **structures** used to store, organize, and manage data in a database. The main database objects include:

1. **Table**
2. **View**
3. **Sequence**
4. **Index**
5. **Synonym**
6. **Queries**

### **1. Table**

A **table** is the fundamental database object used to store data in **rows and columns**. Each row (record) represents a unique entry, and each column represents a specific attribute.

🔹 **Example: Creating a Table**

```sql
CREATE TABLE Employees (
    Employee_ID INT PRIMARY KEY,
    Name VARCHAR(50),
    Salary DECIMAL(10,2),
    Department VARCHAR(30),
    Hire_Date DATE
);
```

🔹 **Example: Inserting Data into a Table**

```sql
INSERT INTO Employees (Employee_ID, Name, Salary, Department, Hire_Date)
VALUES (101, 'John Doe', 5000, 'IT', '2024-01-15');
```

### **2. View**

A **view** is a **virtual table** based on a SQL query. It does not store data itself but presents data from one or more tables.

#### **Advantages of Views**

✔ Simplifies complex queries  
✔ Enhances security by restricting access to certain columns  
✔ Improves data abstraction

🔹 **Example: Creating a View**

```sql
CREATE VIEW IT_Employees AS
SELECT Name, Salary FROM Employees WHERE Department = 'IT';
```

🔹 **Example: Using a View**

```sql
SELECT * FROM IT_Employees;
```

### **3. Sequence**

A **sequence** is used to **generate unique numbers automatically**, often for **primary key values**.

🔹 **Example: Creating a Sequence**

```sql
CREATE SEQUENCE Employee_Seq
START WITH 100
INCREMENT BY 1
NOCACHE NOCYCLE;
```

🔹 **Example: Using a Sequence in `INSERT`**

```sql
INSERT INTO Employees (Employee_ID, Name, Salary, Department)
VALUES (Employee_Seq.NEXTVAL, 'Alice', 6000, 'HR');
```

### **4. Index**

An **index** is used to **speed up data retrieval** by reducing search time. It improves query performance but slightly slows down `INSERT`, `UPDATE`, and `DELETE` operations.

#### **Types of Indexes**

✔ **Primary Index** – Automatically created on **Primary Key**  
✔ **Unique Index** – Ensures unique values in a column  
✔ **Composite Index** – Created on multiple columns  
✔ **Full-text Index** – Used for searching text-based columns

🔹 **Example: Creating an Index**

```sql
CREATE INDEX idx_salary ON Employees(Salary);
```

🔹 **Example: Query Using Index**

```sql
SELECT * FROM Employees WHERE Salary > 5000;
```

### **5. Synonym**

A **synonym** is an **alias** for a database object (table, view, sequence, etc.). It simplifies queries and helps with security.

🔹 **Example: Creating a Synonym**

```sql
CREATE SYNONYM Emp FOR Employees;
```

🔹 **Example: Using the Synonym**

```sql
SELECT * FROM Emp;
```

### **6. Queries in SQL**

A **query** is a request to retrieve, insert, update, or delete data. The most common queries include:

#### **(A) SELECT Query (Retrieving Data)**

```sql
SELECT Name, Salary FROM Employees WHERE Salary > 5000;
```

#### **(B) INSERT Query (Adding Data)**

```sql
INSERT INTO Employees (Employee_ID, Name, Salary, Department)
VALUES (102, 'Robert', 7500, 'Finance');
```

#### **(C) UPDATE Query (Modifying Data)**

```sql
UPDATE Employees SET Salary = 8000 WHERE Employee_ID = 102;
```

#### **(D) DELETE Query (Removing Data)**

```sql
DELETE FROM Employees WHERE Employee_ID = 102;
```

#### **Conclusion**

- **Tables** store data in a structured format.
- **Views** simplify and secure data retrieval.
- **Sequences** generate unique numbers for primary keys.
- **Indexes** improve search performance.
- **Synonyms** provide aliases for database objects.
- **Queries** manipulate data using `SELECT`, `INSERT`, `UPDATE`, and `DELETE`.

---

## **Advanced SQL Concepts**

### **1. SQL Functions**

SQL **functions** are built-in operations that manipulate data and return results. They are categorized into:

1. **Single-Row Functions** – Operate on each row individually.
2. **Aggregate Functions** – Operate on multiple rows and return a **single** result.

#### **1.1 Single-Row Functions**

These functions return a single value for each row in the result set.

#### **Types of Single-Row Functions**

| **Function Type**        | **Description**                  | **Example**                                                 |
| ------------------------ | -------------------------------- | ----------------------------------------------------------- |
| **String Functions**     | Perform operations on text data. | `UPPER()`, `LOWER()`, `CONCAT()`, `SUBSTRING()`, `LENGTH()` |
| **Numeric Functions**    | Perform calculations on numbers. | `ROUND()`, `CEIL()`, `FLOOR()`, `ABS()`, `POWER()`          |
| **Date Functions**       | Work with date and time values.  | `NOW()`, `DATE_ADD()`, `DATEDIFF()`, `EXTRACT()`            |
| **Conversion Functions** | Convert data types.              | `CAST()`, `CONVERT()`                                       |

🔹 **Example: Using String & Date Functions**

```sql
SELECT UPPER(Name) AS Uppercase_Name, LENGTH(Name) AS Name_Length
FROM Employees;
```

```sql
SELECT NOW() AS CurrentDateTime, YEAR(Hire_Date) AS HireYear
FROM Employees;
```

#### **1.2 Aggregate Functions**

These functions **perform calculations** on multiple rows and return a **single** value.

| **Function** | **Description**           | **Example**   |
| ------------ | ------------------------- | ------------- |
| `COUNT()`    | Counts number of rows.    | `COUNT(*)`    |
| `SUM()`      | Adds numeric values.      | `SUM(Salary)` |
| `AVG()`      | Calculates average value. | `AVG(Salary)` |
| `MAX()`      | Returns maximum value.    | `MAX(Salary)` |
| `MIN()`      | Returns minimum value.    | `MIN(Salary)` |

🔹 **Example: Aggregate Functions in SQL**

```sql
SELECT COUNT(*) AS TotalEmployees, AVG(Salary) AS AvgSalary
FROM Employees;
```

```sql
SELECT Department, SUM(Salary) AS TotalSalary
FROM Employees
GROUP BY Department;
```

### **2. Subqueries**

A **subquery** is a query inside another query. It is used to fetch intermediate results.

#### **Types of Subqueries**

| **Type**                | **Description**             |
| ----------------------- | --------------------------- |
| **Single-Row Subquery** | Returns one value.          |
| **Multi-Row Subquery**  | Returns multiple values.    |
| **Correlated Subquery** | Depends on the outer query. |

🔹 **Example: Subquery for Finding Employees with the Highest Salary**

```sql
SELECT Name, Salary
FROM Employees
WHERE Salary = (SELECT MAX(Salary) FROM Employees);
```

🔹 **Example: Multi-Row Subquery Using `IN`**

```sql
SELECT Name, Salary
FROM Employees
WHERE Department IN (SELECT Department FROM Departments WHERE Location = 'New York');
```

### **3. Join Operations**

A **JOIN** is used to **combine data from multiple tables** based on a common column.

#### **Types of Joins in SQL**

| **Join Type**       | **Description**                                                                        |
| ------------------- | -------------------------------------------------------------------------------------- |
| **INNER JOIN**      | Returns matching records from both tables.                                             |
| **LEFT JOIN**       | Returns all records from the **left table** and matching records from the right table. |
| **RIGHT JOIN**      | Returns all records from the **right table** and matching records from the left table. |
| **FULL OUTER JOIN** | Returns all records when there is a match in **either** table.                         |
| **SELF JOIN**       | Joins a table with itself.                                                             |
| **CROSS JOIN**      | Returns the Cartesian product of two tables.                                           |

#### **3.1 INNER JOIN**

🔹 **Example: Get Employee Details with Department Name**

```sql
SELECT Employees.Name, Employees.Salary, Departments.Department_Name
FROM Employees
INNER JOIN Departments ON Employees.Department_ID = Departments.Department_ID;
```

#### **3.2 LEFT JOIN**

🔹 **Example: Retrieve all employees and their department names (including employees without a department)**

```sql
SELECT Employees.Name, Employees.Salary, Departments.Department_Name
FROM Employees
LEFT JOIN Departments ON Employees.Department_ID = Departments.Department_ID;
```

#### **3.3 RIGHT JOIN**

🔹 **Example: Retrieve all departments and their employees (including departments with no employees)**

```sql
SELECT Employees.Name, Employees.Salary, Departments.Department_Name
FROM Employees
RIGHT JOIN Departments ON Employees.Department_ID = Departments.Department_ID;
```

#### **3.4 FULL OUTER JOIN**

🔹 **Example: Retrieve all employees and departments (even if there is no match)**

```sql
SELECT Employees.Name, Employees.Salary, Departments.Department_Name
FROM Employees
FULL OUTER JOIN Departments ON Employees.Department_ID = Departments.Department_ID;
```

#### **3.5 SELF JOIN**

🔹 **Example: Find Employees and Their Managers**

```sql
SELECT A.Name AS Employee, B.Name AS Manager
FROM Employees A, Employees B
WHERE A.Manager_ID = B.Employee_ID;
```

#### **Conclusion**

- **Single-Row Functions** operate on individual rows.
- **Aggregate Functions** perform calculations on multiple rows.
- **Subqueries** allow nested queries for complex operations.
- **Joins** combine data from multiple tables.

---

## **Set Operations in SQL**

SQL **Set Operations** are used to combine the results of two or more `SELECT` queries. The main set operations are:

1. **UNION** – Combines results and removes duplicates.
2. **UNION ALL** – Combines results but keeps duplicates.
3. **INTERSECT** – Returns common records.
4. **MINUS** (EXCEPT in SQL Server) – Returns records present in the first query but not in the second.

#### **Rules for Set Operations:**

✔ Each `SELECT` must have the **same number of columns**.  
✔ Corresponding columns must have **compatible data types**.

### **1. UNION**

The `UNION` operator **combines results** from multiple `SELECT` statements and removes **duplicates**.

🔹 **Example:** Get all employees from **HR** and **IT** departments (without duplicates).

```sql
SELECT Name FROM Employees WHERE Department = 'HR'
UNION
SELECT Name FROM Employees WHERE Department = 'IT';
```

### **2. UNION ALL**

The `UNION ALL` operator **combines results** but **does not remove duplicates**.

🔹 **Example:** Get all employees from **HR** and **IT** (including duplicates).

```sql
SELECT Name FROM Employees WHERE Department = 'HR'
UNION ALL
SELECT Name FROM Employees WHERE Department = 'IT';
```

### **3. INTERSECT**

The `INTERSECT` operator returns **only the common records** from both queries.

🔹 **Example:** Get employees who **work in both HR and IT**.

```sql
SELECT Name FROM Employees WHERE Department = 'HR'
INTERSECT
SELECT Name FROM Employees WHERE Department = 'IT';
```

✅ **Note:** Not supported in MySQL (Use `INNER JOIN` instead).

### **4. MINUS (EXCEPT in SQL Server)**

The `MINUS` operator returns records from the **first query** that **do not exist** in the second query.

🔹 **Example:** Get employees who are in **HR but not in IT**.

```sql
SELECT Name FROM Employees WHERE Department = 'HR'
MINUS
SELECT Name FROM Employees WHERE Department = 'IT';
```

✅ **Note:**

- `MINUS` works in Oracle & PostgreSQL.
- In SQL Server, use `EXCEPT`:

```sql
SELECT Name FROM Employees WHERE Department = 'HR'
EXCEPT
SELECT Name FROM Employees WHERE Department = 'IT';
```

#### **Conclusion**

| **Operator**       | **Description**                                                  |
| ------------------ | ---------------------------------------------------------------- |
| `UNION`            | Combines results, removes duplicates.                            |
| `UNION ALL`        | Combines results, keeps duplicates.                              |
| `INTERSECT`        | Returns common records.                                          |
| `MINUS` / `EXCEPT` | Returns records from the first query that are not in the second. |

---

## **`Gagan Saini`**
