# Unit-5

## **Concurrency Control Techniques in DBMS**

Concurrency control ensures that multiple transactions execute **safely and correctly** without leading to data inconsistencies in a multi-user database environment. It prevents issues like **dirty reads, lost updates, and uncommitted data access** while maintaining the **ACID properties**.

---

### **1. Concurrency Control Techniques**

Concurrency control ensures that transactions are executed **in a controlled manner** to maintain **serializability and isolation**. The main techniques are:

1. **Locking Protocols**
2. **Timestamp-Based Protocols**
3. **Optimistic Concurrency Control**
4. **Multiversion Concurrency Control (MVCC)**

---

### **2. Locking Techniques**

Locking is a **pessimistic concurrency control** technique that prevents multiple transactions from accessing the same data simultaneously in a conflicting manner.

#### **Types of Locks**

| **Lock Type**          | **Description**                                                                |
| ---------------------- | ------------------------------------------------------------------------------ |
| **Shared Lock (S)**    | Allows **read-only** access. Multiple transactions can read but **not write**. |
| **Exclusive Lock (X)** | Grants **write access**. Only **one transaction** can hold it at a time.       |

#### **Two-Phase Locking (2PL) Protocol**

- Ensures **serializability** by dividing transaction execution into two phases:
  1. **Growing Phase:** Transactions acquire locks but **do not release them**.
  2. **Shrinking Phase:** Transactions release locks but **do not acquire new ones**.

#### **Example of 2PL**

```
T1: Lock-X(A), Write(A), Lock-X(B), Write(B), Unlock(A), Unlock(B)
T2: Lock-S(A) (Waits until T1 releases lock)
```

- Ensures no conflicting operations occur simultaneously.

#### **Strict 2PL**

- Locks are released **only after transaction commits or aborts**.
- Prevents cascading rollbacks.

#### **Deadlocks in Locking**

Deadlocks occur when transactions wait indefinitely for each other’s locked resources.

#### **Deadlock Prevention in Locking**

- **Wait-Die:** Older transaction waits; younger one is aborted.
- **Wound-Wait:** Older transaction forces younger one to abort.

---

### **3. Timestamp Ordering Protocol**

The **Timestamp Ordering Protocol (TO)** is a **non-locking** concurrency control mechanism that ensures transactions execute in a **timestamp order**.

#### **How Timestamp Ordering Works**

1. Each transaction is assigned a unique **timestamp (TS)** when it starts.
2. Every data item has two timestamps:
   - **Read Timestamp (RTS)** → Last transaction that read the item.
   - **Write Timestamp (WTS)** → Last transaction that wrote the item.
3. **Read & Write Rules:**
   - **Read Rule:** If `TS(T) < WTS(X)`, the transaction is **aborted** (ensures no outdated reads).
   - **Write Rule:** If `TS(T) < RTS(X)`, the transaction is **aborted** (ensures no overwriting of newer reads).

#### **Advantages & Disadvantages of Timestamp Ordering**

✅ **Ensures serializability**  
✅ **No deadlocks** (since transactions do not wait)  
❌ **Aborts transactions frequently** (especially in a highly concurrent system)

#### **Example of Timestamp Ordering**

```
T1 (TS=5) reads A → T2 (TS=8) writes A → T1 tries to write A (ABORT)
```

- T1 is aborted since it is trying to overwrite a newer version.

---

### **4. Optimistic Concurrency Control (OCC)**

OCC assumes that **conflicts are rare** and allows transactions to execute **without locking**. It validates transactions **before commit**.

#### **Phases of OCC**

1. **Read Phase** – Transactions execute and store changes locally.
2. **Validation Phase** – Check if conflicts exist.
3. **Write Phase** – If no conflicts, commit changes; otherwise, abort and restart.

#### **Advantages & Disadvantages of OCC**

✅ **Better performance in low-conflict environments**  
✅ **No deadlocks**  
❌ **High rollback rate in high-contention systems**

---

### **5. Multiversion Concurrency Control (MVCC)**

MVCC maintains **multiple versions** of data items, allowing **concurrent reads and writes**.

- **Read transactions** use older committed versions.
- **Write transactions** create a **new version** rather than overwriting.

✅ **High read performance**  
✅ **No read locks needed**  
❌ **Requires more storage**

#### **Example of MVCC**

```
T1 reads old version of A → T2 writes new version of A
```

- Readers don’t block writers, and writers don’t block readers.

---

### **6. Summary Table**

| **Technique**                | **How It Works?**                  | **Pros**                      | **Cons**            |
| ---------------------------- | ---------------------------------- | ----------------------------- | ------------------- |
| **Locking (2PL)**            | Transactions acquire locks         | Prevents conflicts            | Can cause deadlocks |
| **Timestamp Ordering**       | Transactions ordered by timestamps | No deadlocks                  | Frequent rollbacks  |
| **Optimistic Control (OCC)** | Checks conflicts before commit     | Good for low-contention cases | High rollback rate  |
| **MVCC**                     | Keeps multiple versions of data    | Readers & writers don’t block | Uses more storage   |

#### **Conclusion**

Concurrency control is essential to maintain **database integrity and performance**. The choice of technique depends on the **use case**:

- **High contention?** → **2PL (Locking)**
- **No waiting, no deadlocks?** → **Timestamp Ordering**
- **Low conflict environment?** → **Optimistic Concurrency Control**
- **High read operations?** → **MVCC**

🚀 **Choosing the right technique optimizes database performance while ensuring correctness!**

## **Granularity of Data Items & Recovery from Catastrophic Failures in DBMS**

### **1. Granularity of Data Items**

Granularity refers to the **size of the data item** that a transaction locks or accesses in a database. It defines how much data is controlled by concurrency control mechanisms.

#### **Levels of Granularity in DBMS**

| **Granularity Level** | **Example**                    | **Locking Impact**                                |
| --------------------- | ------------------------------ | ------------------------------------------------- |
| **Database Level**    | Entire database                | High contention, low concurrency                  |
| **File Level**        | One file                       | Less contention, moderate concurrency             |
| **Table Level**       | One table                      | Better than file-level, but still locks many rows |
| **Page Level**        | A fixed-size page (e.g., 4 KB) | Common for disk-based storage                     |
| **Row Level**         | A single row in a table        | High concurrency, low contention                  |
| **Column Level**      | A single column in a row       | Used in NoSQL and columnar databases              |
| **Attribute Level**   | A single attribute (field)     | Maximum concurrency, but high overhead            |

#### **Locking & Granularity Trade-offs**

- **Fine Granularity (Row/Column Level)**
  - ✅ Increases concurrency.
  - ❌ High overhead due to more locks.
- **Coarse Granularity (Table/File Level)**
  - ✅ Reduces locking overhead.
  - ❌ Increases contention, reduces concurrency.

#### **Example of Granularity in Locking**

- **Coarse Locking:** If a transaction locks an entire table, no other transaction can access any row in that table.
- **Fine Locking:** If a transaction locks only one row, other transactions can modify other rows simultaneously.

---

### **2. Recovery from Catastrophic Failures**

A **catastrophic failure** is a **severe system failure** that results in **complete data loss**. It typically occurs due to **hardware failures, natural disasters, or cyber-attacks**.

#### **Causes of Catastrophic Failures**

1. **Hardware Failures** (Disk crashes, CPU failures)
2. **Software Corruption** (DBMS bugs, OS crashes)
3. **Power Failures** (Extended outages causing corruption)
4. **Natural Disasters** (Earthquakes, floods, fires)
5. **Cyber Attacks** (Ransomware, data breaches)

#### **Recovery from Catastrophic Failures**

To recover from catastrophic failures, databases implement **disaster recovery strategies**:

1. **Backup & Restore Mechanism**

   - Regular **backups** are stored in external locations.
   - Backups can be **full, incremental, or differential**.

2. **Remote Backups (Offsite Storage)**

   - Backups are stored in a different physical location (e.g., cloud-based storage).

3. **Database Replication**

   - **Synchronous replication:** Real-time copies of data.
   - **Asynchronous replication:** Periodic copies to a remote site.

4. **RAID Storage (Redundant Array of Independent Disks)**

   - Uses multiple disks to **prevent data loss** from disk failures.

5. **Transaction Log Backups**

   - Uses **log-based recovery** to restore transactions after the last checkpoint.

6. **Cold & Hot Sites**
   - **Cold Site:** A backup facility that requires setup after failure.
   - **Hot Site:** A fully functional backup system that can take over immediately.

#### **Example of Recovery Process**

1. Restore the latest **full database backup**.
2. Apply the most recent **incremental or differential backups**.
3. Use **log-based recovery (Redo logs)** to apply committed transactions.

---

### **3. Summary Table**

| **Concept**                               | **Description**                                     |
| ----------------------------------------- | --------------------------------------------------- |
| **Granularity of Data Items**             | Defines the size of data items locked or accessed.  |
| **Fine Granularity (Row/Column Level)**   | High concurrency, but high locking overhead.        |
| **Coarse Granularity (Table/File Level)** | Low overhead, but increases contention.             |
| **Catastrophic Failure**                  | Severe failure causing total data loss.             |
| **Recovery Methods**                      | Backups, replication, RAID, and log-based recovery. |

#### **Conclusion**

- **Choosing the right granularity** affects database performance and concurrency.
- **Disaster recovery planning** is crucial for preventing catastrophic data loss.

🚀 **Using backups, replication, and logging ensures data safety in critical failures!**

## **Concepts of Object-Oriented DBMS (OODBMS) & Distributed DBMS (DDBMS)**

### **1. Object-Oriented DBMS (OODBMS)**

An **Object-Oriented Database Management System (OODBMS)** integrates **object-oriented programming (OOP)** principles with database management to store, manage, and retrieve complex data efficiently.

#### **Key Concepts of OODBMS**

1. **Objects**

   - Data is stored as **objects** instead of tables.
   - Objects contain both **data (attributes)** and **methods (functions)**.

2. **Classes & Inheritance**

   - Objects are grouped into **classes**.
   - Classes can inherit properties from parent classes (**hierarchical structure**).

3. **Encapsulation**

   - Data and behavior are bundled together in an object.
   - Data hiding is possible using access modifiers.

4. **Polymorphism**

   - Different objects can use the same method name with different implementations.

5. **Persistence**

   - Objects are stored **permanently** in the database, unlike traditional programming where objects are temporary.

6. **Complex Data Types**

   - Supports **arrays, multimedia, geographic data, and nested objects**.

7. **Object Identity (OID)**

   - Each object has a unique **Object Identifier (OID)** that does not change.

8. **Query Language**
   - Uses **OQL (Object Query Language)**, similar to SQL but designed for objects.

#### **Advantages of OODBMS**

✅ **Better handling of complex data** (e.g., multimedia, CAD, GIS).  
✅ **No impedance mismatch** (data is stored in object form, reducing conversion overhead).  
✅ **Reusability** (supports inheritance and polymorphism).  
✅ **Efficient performance** for applications requiring object relationships.

#### **Disadvantages of OODBMS**

❌ **Complexity** (requires understanding of object-oriented principles).  
❌ **Limited adoption** (traditional RDBMS is more widely used).  
❌ **Query performance** may be lower than relational databases for some operations.

#### **Example of OODBMS**

```
class Student {
    int studentID;
    String name;
    List<Course> courses;
}
```

- Here, a **Student** object contains a list of **Course** objects, representing a **real-world relationship**.

### **Popular OODBMS Examples**

- **ObjectDB**
- **db4o**
- **Versant**
- **ODMG (Object Data Management Group) Standard**

---

### **2. Distributed DBMS (DDBMS)**

A **Distributed Database Management System (DDBMS)** manages a database that is **spread across multiple locations (servers)** and connected via a network.

#### **Characteristics of DDBMS**

1. **Data Distribution**

   - The database is **physically stored at multiple sites**.
   - Each site has its **own local database system**.

2. **Transparency**

   - **Location Transparency:** Users don't need to know where data is stored.
   - **Replication Transparency:** Users see a **single database**, even if multiple copies exist.
   - **Fragmentation Transparency:** Users can access data without knowing how it is fragmented.

3. **Autonomy**

   - Each site can operate **independently** but still participates in the distributed system.

4. **Concurrency Control**

   - Ensures transactions across multiple sites **maintain consistency**.

5. **Fault Tolerance**
   - If one site fails, others continue to function (**high availability**).

---

#### **Types of Distributed Databases**

| **Type**                | **Description**                                |
| ----------------------- | ---------------------------------------------- |
| **Homogeneous DDBMS**   | All sites use the **same DBMS** and schema.    |
| **Heterogeneous DDBMS** | Sites may use **different DBMSs** and schemas. |

#### **Data Fragmentation Techniques**

| **Type**                     | **Description**                                    |
| ---------------------------- | -------------------------------------------------- |
| **Horizontal Fragmentation** | Splits **rows** into different locations.          |
| **Vertical Fragmentation**   | Splits **columns** into different locations.       |
| **Hybrid Fragmentation**     | Uses **both horizontal & vertical** fragmentation. |

#### **Replication Strategies**

| **Replication Type**    | **Description**                               |
| ----------------------- | --------------------------------------------- |
| **Full Replication**    | Complete database is replicated at each site. |
| **Partial Replication** | Only a subset of the database is replicated.  |
| **No Replication**      | Each site stores unique data.                 |

#### **Advantages of DDBMS**

✅ **Improved Reliability & Availability** (Data is available even if one site fails).  
✅ **Faster Query Processing** (Queries are executed on local databases, reducing load).  
✅ **Scalability** (New sites can be added without disrupting the system).

#### **Disadvantages of DDBMS**

❌ **Complexity** (Requires sophisticated software to manage distributed data).  
❌ **Security Risks** (Data is transferred over a network, increasing vulnerabilities).  
❌ **High Maintenance Costs** (More resources needed for synchronization and consistency).

#### **Example of Distributed DBMS**

Imagine a **global e-commerce company** like Amazon:

- **USA Server:** Stores U.S. customer data.
- **Europe Server:** Stores European customer data.
- **Asia Server:** Stores Asian customer data.
- Customers from each region access their **local database** for faster performance.

#### **Popular DDBMS Examples**

- **Google Spanner**
- **IBM Db2**
- **Oracle Distributed Database**
- **Apache Cassandra** (NoSQL-based distributed DBMS)

---

### **3. Comparison: OODBMS vs. DDBMS**

| **Feature**        | **OODBMS**                              | **DDBMS**                                     |
| ------------------ | --------------------------------------- | --------------------------------------------- |
| **Data Structure** | Stores data as objects                  | Stores data across multiple locations         |
| **Best For**       | Complex applications (CAD, GIS, AI)     | Large-scale distributed systems               |
| **Query Language** | OQL (Object Query Language)             | SQL-based queries                             |
| **Performance**    | Efficient for object-based applications | Efficient for geographically distributed data |
| **Example DBMS**   | ObjectDB, db4o                          | Google Spanner, Cassandra                     |

---

### **4. Conclusion**

- **OODBMS** is ideal for **object-oriented applications**, handling **complex data** efficiently.
- **DDBMS** is best suited for **distributed environments**, offering **scalability, fault tolerance, and improved performance**.

🚀 **Choosing between OODBMS & DDBMS depends on application needs!**

## **Overview of Database Security Concepts**

### **1. What is Database Security?**

Database security refers to **protecting the database** from unauthorized access, misuse, and threats such as data breaches, cyberattacks, and accidental data loss. It ensures **confidentiality, integrity, and availability** (CIA Triad) of database systems.

---

### **2. Key Concepts of Database Security**

#### **A. Authentication & Authorization**

- **Authentication** → Verifies **who** is accessing the database (e.g., username & password).
- **Authorization** → Determines **what actions** a user can perform based on their privileges.

#### **B. Access Control Mechanisms**

- **Role-Based Access Control (RBAC)** → Assigns permissions based on user roles (e.g., admin, manager, employee).
- **Discretionary Access Control (DAC)** → The owner of the data controls access (e.g., file-sharing permissions).
- **Mandatory Access Control (MAC)** → Access is controlled by system policies (e.g., military databases).

#### **C. Data Encryption**

- Protects **sensitive data** by converting it into an unreadable format.
- **Types of encryption:**
  - **At-rest encryption** → Encrypts stored data (e.g., AES, TDE in SQL Server).
  - **In-transit encryption** → Encrypts data sent over a network (e.g., SSL/TLS).

#### **D. Database Auditing & Logging**

- Keeps track of all activities in the database, including:
  - **Login attempts**
  - **Data modifications**
  - **Unauthorized access attempts**
- Helps in **identifying security breaches** and meeting compliance requirements.

#### **E. Backup & Disaster Recovery**

- Regular backups prevent **data loss** due to cyberattacks or system failures.
- **Types of backups:**
  - **Full backup** → Copies the entire database.
  - **Incremental backup** → Copies only changed data since the last backup.
  - **Differential backup** → Copies data changed since the last full backup.

#### **F. SQL Injection Prevention**

- SQL injection is a hacking technique that exploits **poorly coded SQL queries**.
- **Prevention methods:**
  - Use **prepared statements** and **parameterized queries**.
  - Limit database user privileges.
  - Validate and sanitize user inputs.

#### **G. Firewalls & Network Security**

- **Database Firewalls** → Restrict unauthorized access based on IP addresses and traffic patterns.
- **Intrusion Detection Systems (IDS)** → Monitor and alert for suspicious activities.

#### **H. User Account Security**

- Use **strong passwords** and enforce **multi-factor authentication (MFA)**.
- Implement **least privilege principle (PoLP)**—users should have **only** the access they need.

---

### **3. Database Security Threats**

| **Threat**                  | **Description**                                             | **Mitigation**                                              |
| --------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| **SQL Injection**           | Hackers manipulate SQL queries to gain unauthorized access. | Use parameterized queries & input validation.               |
| **Data Leakage**            | Unauthorized access or exposure of sensitive data.          | Encrypt sensitive data & enforce strict access controls.    |
| **Privilege Abuse**         | Users misuse excessive privileges.                          | Follow the least privilege principle & audit user activity. |
| **Denial of Service (DoS)** | Attackers overload the database, causing it to crash.       | Implement rate-limiting & database firewalls.               |
| **Malware & Ransomware**    | Malicious software corrupts or encrypts data.               | Use **antivirus software** and **regular backups**.         |

---

### **4. Security Compliance & Standards**

Organizations must comply with **legal and industry regulations** to secure databases.

#### **Common Compliance Standards:**

| **Standard**                                                    | **Purpose**                                            |
| --------------------------------------------------------------- | ------------------------------------------------------ |
| **GDPR (General Data Protection Regulation)**                   | Protects personal data of EU citizens.                 |
| **HIPAA (Health Insurance Portability and Accountability Act)** | Secures healthcare data.                               |
| **PCI-DSS (Payment Card Industry Data Security Standard)**      | Protects credit card transactions.                     |
| **ISO 27001**                                                   | Establishes information security management standards. |

---

### **5. Summary Table**

| **Security Aspect**                | **Key Measures**                               |
| ---------------------------------- | ---------------------------------------------- |
| **Authentication & Authorization** | User verification & role-based access control  |
| **Encryption**                     | Protects data in transit & at rest             |
| **Auditing & Logging**             | Tracks activities & detects security incidents |
| **SQL Injection Prevention**       | Uses parameterized queries & input validation  |
| **Backups & Disaster Recovery**    | Ensures data availability & integrity          |
| **Firewalls & Network Security**   | Restricts unauthorized access                  |

---

### **6. Conclusion**

- **Database security is essential** to protect sensitive data from breaches and attacks.
- **Implementing best practices** (e.g., encryption, access control, auditing) strengthens security.
- **Compliance with industry standards** ensures legal and ethical data management.

🚀 **A secure database means a secure business!**

## **`Gagan Saini`**
