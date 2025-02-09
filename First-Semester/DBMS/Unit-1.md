# Unit-1

## **What is a Database?**

A **database** is an organized collection of data that allows users to store, retrieve, manage, and manipulate data efficiently. It is designed to handle large amounts of information in a structured way, ensuring easy access, security, and integrity.

Databases can be of different types, including:

- **Relational Databases (RDBMS)**: Use tables and SQL (e.g., MySQL, PostgreSQL, Oracle, SQL Server).
- **NoSQL Databases**: Handle unstructured or semi-structured data (e.g., MongoDB, Cassandra).
- **Cloud Databases**: Hosted on cloud platforms (e.g., Amazon RDS, Google Firestore).

---

## **Database Users**

Database users are individuals or applications that interact with the database for different purposes. There are several types of users:

1. **Database Administrators (DBA)**

   - Manage the database system, user access, and security.
   - Perform backups, updates, and optimization.
   - Ensure data integrity and recovery in case of failures.

2. **End Users**

   - Regular users who interact with the database via applications (e.g., customers using an online shopping app).
   - They retrieve or enter data without directly running complex queries.

3. **Application Programmers/Developers**

   - Write code and applications that interact with the database.
   - Use SQL or database APIs to fetch, insert, update, or delete data.

4. **System Analysts**

   - Design database structures and workflows based on business requirements.
   - Ensure databases meet organizational needs efficiently.

5. **Database Designers**

   - Plan and create the database schema (tables, relationships, indexes).
   - Optimize database performance and normalization.

6. **Privileged Users**
   - Have higher access than regular users but lower than DBAs.
   - Can modify data and generate reports but may not manage database structure.

## **Characteristics of a Database**

A database has several key characteristics that make it an essential tool for managing and organizing data efficiently. Here are the main characteristics:

### **1. Organized and Structured Data Storage**

- Data is stored in tables (for relational databases) or other structured formats (for NoSQL databases).
- Allows efficient retrieval and management of large datasets.

### **2. Data Integrity**

- Ensures accuracy and consistency of data.
- Uses constraints (e.g., primary keys, foreign keys) to prevent incorrect or duplicate entries.

### **3. Data Security**

- Provides authentication and authorization to control access.
- Protects sensitive data through encryption and access control mechanisms.

### **4. Data Independence**

- Changes in database structure (e.g., adding new columns) do not affect applications that use the database.
- Ensures flexibility and scalability.

### **5. Multi-User Access**

- Allows multiple users to access and modify data simultaneously without conflicts.
- Uses concurrency control mechanisms to maintain consistency.

### **6. Transactions and ACID Properties**

- Supports transactions, ensuring reliable data operations.
- **ACID properties**:
  - **A**tomicity: Ensures all parts of a transaction are completed or none at all.
  - **C**onsistency: Keeps the database in a valid state before and after transactions.
  - **I**solation: Prevents transactions from interfering with each other.
  - **D**urability: Ensures data is permanently stored even after system failures.

### **7. Data Redundancy Reduction**

- Prevents unnecessary duplication of data.
- Uses **normalization** techniques to optimize data storage.

### **8. Data Recovery and Backup**

- Provides backup and recovery mechanisms to restore data in case of failure.
- Ensures business continuity and disaster recovery.

### **9. Query Processing and Optimization**

- Supports powerful query languages like SQL for data retrieval.
- Optimizes queries for faster performance.

### **10. Scalability and Flexibility**

- Can handle growing amounts of data efficiently.
- Supports distributed databases for better performance and availability.

## **ACID Properties in Databases**

ACID is a set of properties that ensure reliable and consistent database transactions. These properties are crucial for maintaining data integrity, especially in multi-user environments.

### **1. Atomicity ("All or Nothing")**

- Ensures that a transaction is **fully completed** or **fully rolled back** if any part fails.
- If a transaction has multiple steps, and one step fails, the entire transaction is undone.
- Example:
  - Transferring money from Account A to Account B involves **debiting A** and **crediting B**.
  - If debiting succeeds but crediting fails, the entire transaction is **rolled back** to prevent money loss.

### **2. Consistency ("Valid State")**

- Ensures that a transaction **brings the database from one valid state to another**.
- Any operation must follow defined rules, constraints, and relationships.
- Example:
  - A bank transfer should never create or lose money; the total balance across accounts must remain unchanged.

### **3. Isolation ("No Interference")**

- Ensures that transactions running simultaneously do not affect each other.
- Each transaction is executed as if it is the only one running, preventing dirty reads, lost updates, or inconsistencies.
- Example:
  - If two people try to buy the last item in stock, **isolation ensures only one transaction succeeds** and the other is informed.

### **4. Durability ("Permanent Changes")**

- Ensures that once a transaction is **committed**, it is permanently saved, even in case of system failure.
- Uses **logs, backups, and recovery mechanisms** to prevent data loss.
- Example:
  - After confirming a bank transfer, even if the system crashes, the transaction remains recorded when the system restarts.

### **Why ACID Properties Matter?**

- Prevents **data corruption and inconsistency**.
- Ensures **reliable** and **secure** database transactions.
- Maintains **trust and accuracy** in financial, healthcare, and critical systems.

---

## **What is a Database System?**

A **Database System** is a combination of software, hardware, users, and procedures that work together to **store, manage, and retrieve data efficiently**. It ensures data integrity, security, and availability for users and applications.

### **Components of a Database System**

1. **Database**

   - A structured collection of data stored for easy access and management.
   - Can be relational (SQL-based) or non-relational (NoSQL).

2. **Database Management System (DBMS)**

   - Software that **manages** the database (e.g., MySQL, PostgreSQL, Oracle, MongoDB).
   - Provides tools for data storage, retrieval, and security.

3. **Hardware**

   - The physical devices used to store and run the database (servers, storage drives, network devices).

4. **Software**

   - Includes the DBMS, application software, and tools for interacting with the database.

5. **Users**

   - **Database Administrators (DBAs)**: Manage the system, security, and backups.
   - **Developers**: Write applications that interact with the database.
   - **End Users**: Use applications to retrieve or update data.

6. **Procedures & Policies**
   - Guidelines for database access, backup, recovery, and security.

---

## **Functions of a Database System**

✔ **Data Storage & Retrieval** – Efficiently store and retrieve data using queries.  
✔ **Data Security** – Restrict unauthorized access using authentication and encryption.  
✔ **Data Integrity** – Maintain accuracy and consistency of data.  
✔ **Transaction Management** – Ensure ACID properties for reliability.  
✔ **Backup & Recovery** – Prevent data loss due to failures.  
✔ **Concurrency Control** – Allow multiple users to access data without conflicts.

## **Data Concepts and Architecture in a Database System**

A **database system** follows a structured approach to managing data efficiently. It consists of core **data concepts** and **architectural models** that define how data is stored, accessed, and processed.

### **1. Key Data Concepts**

#### **a) Data**

- Raw facts and figures (e.g., numbers, names, dates).
- Example: "John, 25, New York" is data.

#### **b) Information**

- Processed data that has meaning.
- Example: "John is 25 years old and lives in New York" is information.

#### **c) Metadata**

- Data **about data** (e.g., data types, table structures).
- Example: A column named **"Age"** with **integer type** is metadata.

#### **d) Database Schema**

- The **structure** of a database, defining tables, fields, and relationships.
- Example: A customer database schema with **Customers (ID, Name, Email)** table.

#### **e) Data Model**

- The way data is **structured and organized** in a database.
- Types of data models:
  - **Relational Model** (SQL-based, tables with rows & columns)
  - **Hierarchical Model** (Tree-like structure)
  - **Network Model** (Graph-based relationships)
  - **NoSQL Model** (Flexible, document-based like MongoDB)

### **2. Database Architecture**

Database architecture defines how databases are designed, structured, and accessed. The main types are:

#### **a) 1-Tier Architecture**

- The database and application reside on the **same** machine.
- Suitable for personal or small-scale applications.
- Example: A local MS Access database.

#### **b) 2-Tier Architecture (Client-Server)**

- The client (user interface) interacts directly with the **DBMS on a server**.
- More secure and efficient than 1-tier.
- Example: A desktop application that connects to a remote MySQL database.

#### **c) 3-Tier Architecture (Web-Based Systems)**

- Divides the system into three layers:
  1. **Presentation Layer (Client/UI)** – User interface (web browser, app).
  2. **Application Layer (Business Logic)** – Processes user requests.
  3. **Database Layer (DBMS)** – Stores and retrieves data.
- Used in **web applications**, banking, e-commerce.

### **3. Data Storage and Access**

- **Primary Storage**: RAM, cache (temporary storage for fast processing).
- **Secondary Storage**: Hard drives, SSDs (stores database files permanently).
- **Indexing**: Speeds up searching by creating structured references to data.
- **Normalization**: Organizes data to reduce redundancy.

### **Why is Database Architecture Important?**

✅ Improves **performance and scalability**.  
✅ Ensures **security and access control**.  
✅ Supports **multi-user** environments.  
✅ Helps in **data integrity and consistency**.

## **Data Models, Schema, and Instance in a Database System**

In a database system, data is organized using **data models**, structured using a **schema**, and updated dynamically through **instances**.

### **1. Data Models**

A **data model** defines how data is stored, organized, and manipulated in a database. It establishes rules for data relationships and structures.

#### **Types of Data Models**

#### **a) Hierarchical Model**

- Data is organized in a **tree-like** structure (parent-child relationship).
- Each parent can have multiple children, but each child has only one parent.
- **Example**: A company database where a "Department" has multiple "Employees".
- **Used in:** XML databases, IBM IMS.

#### **b) Network Model**

- Data is stored using a **graph structure** with multiple parent-child relationships.
- More flexible than the hierarchical model.
- **Example**: A student can enroll in multiple courses, and a course can have multiple students.
- **Used in:** Early DBMS like IDMS.

#### **c) Relational Model (Most Common)**

- Data is stored in **tables (relations)** with rows and columns.
- Uses **primary keys** and **foreign keys** to define relationships.
- **Example**: A customer database with "Customers" and "Orders" tables.
- **Used in:** MySQL, PostgreSQL, Oracle, SQL Server.

#### **d) Object-Oriented Model**

- Stores data in the form of **objects** (like in OOP).
- Each object contains **attributes (fields)** and **methods (functions)**.
- **Example**: Multimedia databases storing images, videos, and their properties.
- **Used in:** Object-oriented DBMS like db4o.

#### **e) NoSQL Model (Non-Relational)**

- Designed for **large-scale, flexible, and high-performance applications**.
- Types:
  - **Document-based (e.g., MongoDB) → JSON-like documents.**
  - **Key-Value stores (e.g., Redis) → Simple key-value pairs.**
  - **Column-family stores (e.g., Cassandra) → Distributed column storage.**
  - **Graph-based (e.g., Neo4j) → Nodes and edges for relationships.**

### **2. Schema in a Database**

A **schema** defines the overall structure of a database, including tables, attributes, and relationships. It acts as a **blueprint** for how data is stored and managed.

#### **Types of Schema**

1. **Physical Schema**

   - Defines how data is **physically stored** on disk (storage structure, indexes).
   - **Example**: The way PostgreSQL stores data in tablespaces.

2. **Logical Schema**

   - Defines the **structure and relationships** of the database at a high level.
   - **Example**: A schema defining tables like "Customers", "Orders", and their relations.

3. **View Schema**
   - Defines **how users see the data**. Different users may have different views.
   - **Example**: An HR system where employees see only their details, but managers see all employees.

### **3. Instance in a Database**

An **instance** is the actual **data stored** in the database at a specific moment. It is a snapshot of the database contents.

#### **Difference Between Schema and Instance**

| Feature    | Schema                                | Instance                             |
| ---------- | ------------------------------------- | ------------------------------------ |
| Definition | Structure of the database (blueprint) | Actual data stored in the database   |
| Changes    | Rarely changes (static)               | Changes frequently (dynamic)         |
| Example    | A table "Students (ID, Name, Age)"    | (101, "Alice", 22), (102, "Bob", 25) |

### **Key Takeaways**

✅ **Data Models** define how data is structured (Relational, NoSQL, etc.).  
✅ **Schema** defines the blueprint of the database (tables, relationships).  
✅ **Instance** is the actual data at a given time (snapshot of the database).

---

### ER Model

The **Entity-Relationship (ER) Model** is a high-level conceptual data model used in **Database Management Systems (DBMS)** to design and represent the logical structure of databases. It provides a graphical representation of entities, their attributes, and the relationships between them.

### **1. Components of ER Model**

The ER model consists of the following key components:

#### **1.1 Entity**

An **entity** is a real-world object that can be uniquely identified.

- **Types of Entities**:
  1. **Strong Entity** – Has a primary key (e.g., _Student, Employee_).
  2. **Weak Entity** – Depends on a strong entity and has no primary key (e.g., _Dependent in an Employee-Dependent relationship_).

#### **1.2 Attributes**

Attributes define the properties of an entity.

- **Types of Attributes**:
  1. **Simple (Atomic) Attribute** – Cannot be divided further (_e.g., Name, Age_).
  2. **Composite Attribute** – Can be divided into smaller sub-parts (_e.g., Full Name → First Name, Last Name_).
  3. **Derived Attribute** – Derived from other attributes (_e.g., Age from Date of Birth_).
  4. **Multivalued Attribute** – Can have multiple values (_e.g., Phone Numbers_).

#### **1.3 Relationship**

A **relationship** represents the association between two or more entities.

- **Types of Relationships**:
  1. **One-to-One (1:1)** – Each entity in Set A is related to at most one entity in Set B (_e.g., One person has one passport_).
  2. **One-to-Many (1:M)** – One entity in Set A is related to multiple entities in Set B (_e.g., One teacher teaches multiple students_).
  3. **Many-to-Many (M:N)** – Multiple entities in Set A relate to multiple entities in Set B (_e.g., Students enroll in multiple courses_).

### **2. ER Diagram Representation**

An **ER Diagram** visually represents the database structure using:

- **Rectangles** → Entities
- **Ellipses** → Attributes
- **Diamonds** → Relationships
- **Lines** → Connecting entities and relationships

Example: **ER Diagram for a Student Database**

```
            +-------------+
            |  Student    |
            +-------------+
            | Student_ID  | (Primary Key)
            | Name        |
            | Age         |
            | Course_ID   | (Foreign Key)
            +-------------+
                  |
                  | Enrolled In (M:N Relationship)
                  |
            +-------------+
            |  Course     |
            +-------------+
            | Course_ID   | (Primary Key)
            | Course_Name |
            +-------------+
```

### **3. Advantages of ER Model**

✅ **Easy to Understand** – Uses diagrams to represent data relationships.  
✅ **Simplifies Database Design** – Provides a clear conceptual structure.  
✅ **Efficient Communication** – Helps developers, designers, and stakeholders understand data flow.  
✅ **Foundation for Normalization** – Helps in structuring relational schemas.

### **4. Limitations of ER Model**

❌ **Not Suitable for Complex Queries** – ER diagrams focus on structure, not retrieval efficiency.  
❌ **No Standard Notation** – Different tools use slightly different notations.  
❌ **Limited Data Constraints** – Does not express functional dependencies or advanced constraints.

### **5. Converting ER Model to Relational Model**

To implement the ER Model in a database, convert:

1. **Entities → Tables**
2. **Attributes → Columns**
3. **Relationships → Foreign Keys**

Example:

- **Student Table**

  | Student_ID | Name   | Age | Course_ID |
  | ---------- | ------ | --- | --------- |
  | 101        | Gagan  | 22  | 303       |
  | 102        | Gunjan | 21  | 301       |
  | 102        | Sumit  | 21  | 302       |

- **Course Table**

  | Course_ID | Course_Name |
  | --------- | ----------- |
  | 301       | Database    |
  | 302       | Networking  |
  | 303       | DSA         |

### **Conclusion**

The **ER Model** is essential in DBMS for designing databases with clear relationships between entities. It provides a **structured approach** to database development and helps ensure data integrity. 🚀

---

## **DBMS Architecture and Data Independence**

A **Database Management System (DBMS) Architecture** defines how a database is structured, accessed, and managed. It ensures **efficient data processing, security, and scalability**. **Data independence** ensures that changes in database structure do not affect applications using the database.

### **1. DBMS Architecture**

DBMS architecture describes the **layers and components** of a database system. It can be classified into different types:

#### **A. Types of DBMS Architecture**

#### **1-Tier Architecture** (Simple & Local)

- The database and application are on the **same** system.
- Used for small applications or **local databases (e.g., MS Access, SQLite).**
- **Example:** A personal finance tracker storing data on a local machine.

#### **2-Tier Architecture** (Client-Server)

- The database is on a **server**, and clients (applications) access it remotely.
- The client sends **queries (SQL requests)** to the server, which processes them and returns the result.
- **Example:** A desktop application connecting to a MySQL server.
- **Used in:** Banking systems, small enterprise applications.

#### **3-Tier Architecture** (Most Common - Web-Based)

- Divides the system into **three layers**:
  1. **Presentation Layer (Client/UI)** → User interacts via a web browser or mobile app.
  2. **Application Layer (Business Logic)** → Processes client requests and communicates with the database.
  3. **Database Layer (DBMS)** → Stores and retrieves data efficiently.
- **Example:** A web application like Amazon, where users interact with a website, which then communicates with a database.
- **Used in:** E-commerce, cloud-based applications, banking.

#### **B. Components of DBMS Architecture**

1. **Database Engine** – Manages data storage, retrieval, and query execution.
2. **Query Processor** – Converts user queries (SQL) into actionable tasks.
3. **Transaction Manager** – Ensures **ACID properties** (Atomicity, Consistency, Isolation, Durability).
4. **Storage Manager** – Handles **physical storage and indexing** for fast access.
5. **Metadata Manager** – Manages **data definitions (schemas, constraints, indexes)**.
6. **Security Manager** – Controls **user authentication, permissions, and encryption**.

### **2. Data Independence**

**Data Independence** ensures that changes in one layer of the database system do not affect other layers. It improves **scalability, flexibility, and maintainability**.

#### **Types of Data Independence**

#### **1. Logical Data Independence** (High-Level)

- **Definition**: The ability to change the **logical schema** (table structures, relationships) **without affecting applications**.
- **Example**:
  - A company adds a new column **"Phone Number"** to the "Customers" table.
  - Applications querying "Customers" remain unaffected unless they specifically request the new column.
- **Benefit**: Makes it easier to **modify the database schema** without updating all applications.

#### **2. Physical Data Independence** (Low-Level)

- **Definition**: The ability to change the **physical storage structure** (indexing, file organization) **without affecting the logical schema**.
- **Example**:
  - A database moves from HDD to SSD storage for better performance.
  - No changes are needed in tables or SQL queries.
- **Benefit**: Enables **performance improvements** without altering database design.

#### **Key Differences: Logical vs Physical Data Independence**

| Feature                | Logical Data Independence                     | Physical Data Independence           |
| ---------------------- | --------------------------------------------- | ------------------------------------ |
| Affects                | Table structures, relationships               | Storage methods, indexing            |
| Impact on Applications | **No impact** unless accessing new attributes | **No impact** at all                 |
| Example                | Adding/removing columns                       | Changing file storage format         |
| Flexibility            | High (supports schema modifications)          | Medium (supports performance tuning) |

### **Why is DBMS Architecture and Data Independence Important?**

✅ **Scalability** – Supports growing data needs without affecting applications.  
✅ **Security** – Multi-tier architecture **protects sensitive data** from direct access.  
✅ **Efficiency** – Logical and physical independence **improves performance and flexibility**.  
✅ **Ease of Maintenance** – Changes can be made **without disrupting operations**.

---

## **Overview of the Hierarchical Database Model**

The **Hierarchical Database Model** organizes data in a **tree-like structure**, where each record (node) has a **single parent** and **multiple children**. This model represents **one-to-many (1:M) relationships**, similar to a family tree or an organizational chart.

## **1. Characteristics of Hierarchical Databases**

✅ **Tree Structure:** Data is stored in a hierarchy of **parent-child** relationships.  
✅ **One Parent, Many Children:** Each child node has only **one parent**, but a parent can have multiple children.  
✅ **Fast Navigation:** Uses predefined **paths** to access records quickly.  
✅ **Data Dependence:** The structure is rigid; changes in hierarchy may require redesign.

## **2. Structure of a Hierarchical Database**

A hierarchical database consists of **nodes**, representing records, and **links**, representing relationships.

**Example:** A company’s employee database

```
          CEO (Parent)
           │
    ┌──────┴──────┐
  Manager1      Manager2 (Children)
    │               │
  Employee1     Employee2 (Children)
```

- The **CEO** is the root node (topmost parent).
- Each **Manager** reports to the CEO and has subordinates (employees).
- Each **Employee** has exactly one manager (parent).

## **3. Examples of Hierarchical Databases**

🔹 **IBM Information Management System (IMS)** – Used in banking & government.  
🔹 **Windows Registry** – Stores system configurations in a hierarchical format.  
🔹 **XML Data Storage** – Organizes data in a nested hierarchical structure.

## **4. Advantages of Hierarchical Databases**

✔ **Fast Data Retrieval** – Queries follow predefined paths, making searches quick.  
✔ **Data Integrity** – Ensures consistency through strict relationships.  
✔ **Efficient for One-to-Many Relationships** – Works well for structured data like organizational charts.

## **5. Disadvantages of Hierarchical Databases**

❌ **Rigid Structure** – Difficult to modify; changes require restructuring.  
❌ **Complex Relationships Not Supported** – Cannot easily handle **many-to-many** relationships.  
❌ **Data Redundancy** – Repeated data can increase storage costs.

The **hierarchical model** is **fast and structured** but **inflexible for modern applications**. Today, it has been largely replaced by **relational (SQL) and NoSQL databases**, which provide more flexibility.

## **Network Database Management System (Network DBMS)**

A **Network DBMS** is a type of database model that allows **many-to-many (M:M) relationships** by using a **graph-like structure** instead of a strict hierarchy. It is an extension of the **Hierarchical Model** but provides more flexibility in data relationships.

### **1. Characteristics of Network DBMS**

✅ **Graph-Based Structure** – Data is organized using **nodes (records)** and **edges (relationships)**.  
✅ **Many-to-Many Relationships** – A child can have **multiple parents**, unlike the hierarchical model.  
✅ **Set-Based Connections** – Uses **pointers or links** to establish relationships between records.  
✅ **High Performance** – Optimized for **complex relationships** and **fast traversal**.  
✅ **Less Data Redundancy** – Eliminates data duplication by allowing multiple connections.

### **2. Structure of a Network Database**

A **Network DBMS** uses **records** (entities) and **sets** (relationships).

**Example: University Database**

Consider a database with **Students, Courses, and Professors**.

```
       (Student1) → (Course1) ← (Professor1)
           │            │
       (Student2) → (Course2) ← (Professor2)
```

- A **Student** can enroll in **multiple courses**.
- A **Course** can have **multiple students and multiple professors**.
- A **Professor** can teach **multiple courses**.

This **many-to-many** relationship is **difficult in hierarchical databases** but is **easily managed in a network DBMS**.

### **3. Examples of Network DBMS**

🔹 **Integrated Data Store (IDS)** – Early network DBMS used in commercial applications.  
🔹 **IDMS (Integrated Database Management System)** – Developed by **Cullinet**.  
🔹 **Raima Database Manager** – Still in use for embedded systems.

### **4. Advantages of Network DBMS**

✔ **Supports Complex Relationships** – Handles **many-to-many** relationships easily.  
✔ **Efficient Data Access** – Uses **pointers** for fast traversal.  
✔ **Less Data Redundancy** – Avoids duplicate data storage.  
✔ **Flexibility** – More adaptable than the hierarchical model.

### **5. Disadvantages of Network DBMS**

❌ **Complex Structure** – Requires **pointers and links**, making it harder to manage.  
❌ **Difficult to Modify** – Changes in structure require careful updates to pointers.  
❌ **High Maintenance** – Needs **skilled database administrators** for optimization.

The **Network Model** was popular before the **Relational Model (SQL)** became dominant. Today, it is used in **graph databases** (e.g., **Neo4j**) for applications like **social networks, recommendation systems, and fraud detection**.

---

## **Relational Database Management System (RDBMS)**

A **Relational Database Management System (RDBMS)** is the most widely used database model today. It organizes data into **tables (relations)** with **rows (records)** and **columns (attributes)**, ensuring **data integrity, consistency, and flexibility**.

## **1. Characteristics of RDBMS**

✅ **Uses Tables (Relations)** – Data is stored in structured tables with rows and columns.  
✅ **Primary and Foreign Keys** – Ensures relationships between different tables.  
✅ **Follows ACID Properties** – Guarantees **Atomicity, Consistency, Isolation, and Durability** for transactions.  
✅ **Supports SQL (Structured Query Language)** – Standard query language for managing relational databases.  
✅ **Normalization** – Reduces **data redundancy** and improves **data integrity**.  
✅ **Multi-User Access** – Allows concurrent access by multiple users.

## **2. Structure of an RDBMS**

### **Example: A Simple Library Database**

#### **1. Books Table**

| Book_ID | Title                 | Author              | Genre     |
| ------- | --------------------- | ------------------- | --------- |
| 101     | The Great Gatsby      | F. Scott Fitzgerald | Fiction   |
| 102     | 1984                  | George Orwell       | Dystopian |
| 103     | To Kill a Mockingbird | Harper Lee          | Fiction   |

#### **2. Users Table**

| User_ID | Name   | Email            |
| ------- | ------ | ---------------- |
| 1       | Gagan  | gagan@gmail.com  |
| 2       | Gunjan | gunjan@gmail.com |
| 3       | Sumit  | sumit@gmail.com  |

#### **3. Borrowed_Books Table (Relationship Table)**

| Borrow_ID | User_ID (FK) | Book_ID (FK) | Borrow_Date | Return_Date |
| --------- | ------------ | ------------ | ----------- | ----------- |
| 001       | 1            | 102          | 2024-02-01  | 2024-02-15  |
| 002       | 2            | 103          | 2024-02-02  | 2024-02-16  |

- **Primary Key (PK)** → Uniquely identifies a row (**Book_ID, User_ID, Borrow_ID**).
- **Foreign Key (FK)** → Establishes relationships between tables (**User_ID, Book_ID** in `Borrowed_Books`).

## **3. Examples of RDBMS**

🔹 **MySQL** – Open-source, widely used in web applications.  
🔹 **PostgreSQL** – Advanced open-source RDBMS with strong ACID compliance.  
🔹 **Oracle Database** – Enterprise-level RDBMS with high performance.  
🔹 **Microsoft SQL Server** – Common in business and enterprise applications.  
🔹 **SQLite** – Lightweight RDBMS for mobile and embedded systems.

## **4. Advantages of RDBMS**

✔ **Data Integrity & Consistency** – Maintains accuracy through normalization.  
✔ **Flexibility** – Easily modified using SQL queries.  
✔ **Security** – User access control with authentication.  
✔ **Scalability** – Supports large databases with indexing and partitioning.

## **5. Disadvantages of RDBMS**

❌ **Complex Setup** – Requires planning, especially for large databases.  
❌ **Performance Issues for Big Data** – Struggles with unstructured or very large datasets.  
❌ **Requires Skilled Administrators** – Needs database professionals for optimization and maintenance.

## **6. SQL Queries in RDBMS**

- **Create a Table**

```sql
CREATE TABLE Books (
    Book_ID INT PRIMARY KEY,
    Title VARCHAR(100),
    Author VARCHAR(100),
    Genre VARCHAR(50)
);
```

- **Insert Data**

```sql
INSERT INTO Books (Book_ID, Title, Author, Genre)
VALUES (101, 'The Great Gatsby', 'F. Scott Fitzgerald', 'Fiction');
```

- **Retrieve Data**

```sql
SELECT * FROM Books WHERE Genre = 'Fiction';
```

- **Join Two Tables**

```sql
SELECT Users.Name, Books.Title, Borrowed_Books.Borrow_Date
FROM Users
JOIN Borrowed_Books ON Users.User_ID = Borrowed_Books.User_ID
JOIN Books ON Borrowed_Books.Book_ID = Books.Book_ID;
```

RDBMS is **the most widely used database model** due to its **structured format, relational capabilities, and reliability**. It is ideal for **business applications, banking, e-commerce, and web applications**.

## **`Gagan Saini`**
