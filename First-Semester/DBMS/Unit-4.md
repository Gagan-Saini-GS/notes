# Unit-4

## **Transaction Processing Concept & Transaction System in DBMS**

### **1. What is a Transaction?**

A **transaction** in a Database Management System (DBMS) is a sequence of one or more SQL operations that are executed as a **single unit of work**. A transaction ensures that either all the operations are successfully executed (**commit**) or none of them take effect (**rollback**), maintaining database integrity.

#### **Example of a Transaction:**

```sql
BEGIN;
UPDATE accounts SET balance = balance - 500 WHERE account_id = 101;
UPDATE accounts SET balance = balance + 500 WHERE account_id = 102;
COMMIT;
```

If any of the queries fail, the transaction should be rolled back to maintain consistency.

---

### **2. ACID Properties of Transactions**

To ensure reliability, transactions must follow **ACID** properties:

1. **Atomicity** – A transaction is **all or nothing**; either all operations execute or none.
2. **Consistency** – The database remains in a **valid state** before and after the transaction.
3. **Isolation** – Transactions are **executed independently** to avoid conflicts.
4. **Durability** – Once a transaction is **committed**, changes are permanent even if a system failure occurs.

---

### **3. Transaction Control Commands**

#### **1. COMMIT**

- Saves all changes made by a transaction permanently in the database.

```sql
COMMIT;
```

#### **2. ROLLBACK**

- Undoes all changes made in the current transaction if an error occurs.

```sql
ROLLBACK;
```

#### **3. SAVEPOINT**

- Creates a point within a transaction to which we can roll back.

```sql
SAVEPOINT sp1;
UPDATE employees SET salary = salary + 5000 WHERE employee_id = 105;
ROLLBACK TO sp1;  -- Reverts changes back to savepoint
```

---

### **4. Transaction System**

A **transaction system** is a **database management system** that ensures transactions execute **safely, consistently, and efficiently**.

#### **Types of Transaction Systems:**

1. **Online Transaction Processing (OLTP)**

   - Handles **real-time transactions** such as banking, e-commerce, and ticket booking.
   - Example: **ATM withdrawals, online purchases**.

2. **Online Analytical Processing (OLAP)**
   - Used for **data analysis** and decision-making.
   - Example: **Data warehousing, business intelligence reports**.

#### **States of a Transaction**

A transaction goes through different states during execution:

| **State**               | **Description**                                                 |
| ----------------------- | --------------------------------------------------------------- |
| **Active**              | Transaction is being executed.                                  |
| **Partially Committed** | Transaction has executed final statement but not committed yet. |
| **Committed**           | Transaction is successfully executed and saved.                 |
| **Failed**              | Transaction has encountered an error.                           |
| **Aborted**             | Transaction is rolled back due to failure.                      |

---

### **5. Concurrency Control in Transactions**

Concurrency control ensures **multiple transactions** execute **correctly** without conflicts. Common techniques include:

1. **Locking Mechanisms**

   - **Shared Lock**: Allows multiple transactions to read data but not write.
   - **Exclusive Lock**: Allows only one transaction to access the data.

2. **Timestamp-Based Protocols**

   - Assigns timestamps to transactions to maintain consistency.

3. **Optimistic Concurrency Control**
   - Transactions execute **without locking** and check for conflicts before committing.

---

#### **Example of Transaction Processing:**

```sql
BEGIN;
UPDATE accounts SET balance = balance - 1000 WHERE account_id = 201;
UPDATE accounts SET balance = balance + 1000 WHERE account_id = 202;

-- If all statements succeed
COMMIT;

-- If any statement fails
ROLLBACK;
```

This ensures **either both** updates occur, or none, preventing inconsistent balances.

---

### **Conclusion**

A **transaction system** is crucial for ensuring **data integrity, consistency, and reliability** in a multi-user environment. By following **ACID properties** and using **concurrency control techniques**, databases ensure that transactions execute **efficiently** and **securely**. 🚀

# **Serializability in DBMS**

## **1. What is Serializability?**

**Serializability** is a key concept in **concurrency control** that ensures the correct execution of **concurrent transactions** in a database. It guarantees that the outcome of executing multiple transactions concurrently is **equivalent to** some **serial execution** (one after another) of those transactions.

**Goal:** To ensure that concurrent transactions maintain the **ACID properties**, especially **consistency** and **isolation**.

### **Example of Serializability**

Consider two transactions:

- **T1**: Withdraw $500 from Account A.
- **T2**: Deposit $300 into Account A.

**Serial Execution:**

- **T1 → T2** OR **T2 → T1**

**Concurrent Execution (Non-serial Order):**

- If transactions execute at the same time without proper control, they may result in **inconsistent data**.

Thus, serializability ensures that the final result is the same as one of the **serial schedules**.

---

## **2. Testing Serializability**

To check if a given schedule is **serializable**, we use two main approaches:

### **1. Conflict Serializability (Precedence Graph / Dependency Graph)**

- **Checks whether the schedule can be transformed into a serial schedule by swapping non-conflicting operations.**
- If the **Precedence Graph (Directed Graph)** has **no cycles**, then the schedule is **conflict serializable**.

### **2. View Serializability**

- **Checks if the schedule produces the same final result as a serial schedule, regardless of swaps.**
- A schedule is **view serializable** if it is **view equivalent** to a serial schedule.

---

## **3. Serializability of Schedules**

A **schedule** is a sequence of interleaved transactions that execute read (`R`) and write (`W`) operations.

### **Types of Schedules**

1. **Serial Schedule**

   - Transactions execute **one after another** without interleaving.
   - Example:
     ```
     T1: R(A), W(A), R(B), W(B)
     T2: R(C), W(C), R(D), W(D)
     ```

2. **Non-Serial Schedule**

   - Transactions execute concurrently, with interleaving operations.
   - Example:
     ```
     T1: R(A), W(A)
     T2: R(B), W(B)
     T1: R(C), W(C)
     T2: R(D), W(D)
     ```

3. **Serializable Schedule**
   - A **non-serial** schedule that is **equivalent to a serial schedule**.

### **Serializability Types:**

- **Conflict Serializability** → Uses precedence graphs.
- **View Serializability** → Checks view equivalence.

---

## **4. Conflict & View Serializable Schedules**

### **Conflict Serializability**

- **Conflict operations:** Two operations **conflict** if:

  1. They belong to **different transactions**.
  2. They operate on the **same data item**.
  3. At least one of them is a **write** operation.

- **Example Conflict Serializability Check:**

  ```
  T1: R(A), W(A)
  T2: R(A), W(A)
  ```

  - `W(A)` in `T1` and `R(A)` in `T2` **conflict**.
  - If conflicts form a **cycle in the precedence graph**, the schedule is **not conflict serializable**.

- **Conflict Serializability Test (Precedence Graph Method)**
  - Construct a **precedence graph** (dependency graph).
  - Nodes = Transactions.
  - Directed edges = Conflicts (T1 → T2 if T1's operation must occur before T2).
  - If the graph has **no cycles**, the schedule is **conflict serializable**.

### **View Serializability**

- A **schedule S1** is **view equivalent** to another schedule **S2** if:

  1. Initial Reads: **Same transactions read the initial values**.
  2. Read-Write Consistency: **Same transactions read from the same writes**.
  3. Final Writes: **Final write operations are the same**.

- **View serializable schedules** are **a superset of conflict serializable schedules**.
- Every **conflict-serializable** schedule is **view-serializable**, but the reverse is **not always true**.

---

## **5. Summary Table**

| **Concept**                        | **Definition**                                                                                                                                                                |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Serializability**                | Ensures a schedule produces the same result as a **serial execution**.                                                                                                        |
| **Conflict Serializability**       | Uses **precedence graph** to check if a schedule can be transformed into a serial schedule by swapping **non-conflicting** operations.                                        |
| **View Serializability**           | Ensures that a schedule is equivalent to a serial schedule by checking **initial reads, read-from writes, and final writes**.                                                 |
| **Conflict vs. View Serializable** | **Conflict serializable ⊆ View serializable** (All conflict serializable schedules are view serializable, but not all view serializable schedules are conflict serializable). |

---

### **Example Question:**

**Q: Given the following schedule, is it conflict serializable?**

```
T1: R(A), W(A)
T2: R(A), W(B)
T3: R(B), W(A)
```

**Steps:**

1. Identify conflicting operations.
2. Build the **precedence graph**.
3. Check for cycles.
4. If no cycle → **Conflict Serializable**, else **Not Serializable**.

---

### **Conclusion**

- **Serializability** ensures database consistency when executing concurrent transactions.
- **Conflict serializability** uses a **precedence graph** to check for cycles.
- **View serializability** is more general but harder to test.
- **If a schedule is conflict serializable, it is also view serializable**, but the reverse is not always true.

By enforcing serializability, **DBMS ensures consistency and correctness** in concurrent transaction execution. 🚀

# **Transaction Recovery & Deadlock Handling in DBMS**

## **1. Recoverability in DBMS**

Recoverability ensures that the database can recover from failures while maintaining **data consistency** and **ACID properties** (especially **Atomicity** and **Durability**). A **recoverable schedule** ensures that if a transaction `T1` reads data written by `T2`, then `T2` **must commit before `T1` commits**.

### **Types of Schedules Based on Recoverability**

| **Schedule Type**        | **Description**                                                                                              |
| ------------------------ | ------------------------------------------------------------------------------------------------------------ |
| **Recoverable Schedule** | If `T1` reads a value written by `T2`, then `T1` commits **only after** `T2` commits.                        |
| **Cascadeless Schedule** | A recoverable schedule that prevents cascading rollbacks (A transaction can only read **committed** values). |
| **Strict Schedule**      | Transactions cannot read or write uncommitted data (ensures **strong consistency**).                         |

### **Example of a Non-Recoverable Schedule (Problem Case)**

```
T1: R(A)         W(A)        (Commit)
T2:         W(A)        R(A)   (Fails)
```

- If `T2` fails after `T1` reads its uncommitted value, **T1 must also be rolled back**, leading to inconsistency.
- A recoverable schedule **avoids this situation** by ensuring `T1` commits only after `T2` commits.

---

## **2. Recovery from Transaction Failures**

A transaction failure occurs when a transaction **cannot complete** due to errors such as:

- **System crashes** (power failure, OS crash)
- **Logical errors** (division by zero, constraint violations)
- **Deadlocks** (transactions waiting indefinitely)

### **Types of Transaction Failures**

1. **System Crash**
   - Caused by hardware failures (power failure, OS crash).
   - Recovery is done using **log-based recovery**.
2. **Transaction Errors**

   - SQL errors (e.g., constraint violations, divide by zero).
   - The system rolls back the failed transaction.

3. **Deadlocks**
   - Two or more transactions wait indefinitely for each other’s locked resources.
   - Requires **deadlock detection and handling**.

---

## **3. Log-Based Recovery**

A **transaction log** (write-ahead logging) is used to keep a record of all database modifications. If a failure occurs, **log records** help recover the database.

### **Types of Log Records**

| **Log Entry**                           | **Description**                              |
| --------------------------------------- | -------------------------------------------- |
| **[Start Transaction, T]**              | Marks the beginning of transaction `T`.      |
| **[Write, T, X, Old_Value, New_Value]** | `T` modifies `X`; stores old and new values. |
| **[Commit, T]**                         | `T` successfully completes.                  |
| **[Abort, T]**                          | `T` is rolled back.                          |

### **Write-Ahead Logging (WAL) Rule**

- **Before modifying the database, logs must be written to disk**.
- If a failure occurs, uncommitted transactions are **rolled back** using the logs.

### **Undo and Redo Operations**

| **Operation** | **When Used?**                      | **Action**                            |
| ------------- | ----------------------------------- | ------------------------------------- |
| **UNDO**      | If transaction is **not committed** | Restore old values from logs.         |
| **REDO**      | If transaction is **committed**     | Reapply changes to ensure durability. |

### **Example of Log-Based Recovery**

```
[Start Transaction, T1]
[Write, T1, A, 100, 200]
[Commit, T1]
```

- If a crash happens **after commit**, we **redo** the transaction.
- If a crash happens **before commit**, we **undo** the transaction.

---

## **4. Checkpoints in DBMS**

A **checkpoint** is a mechanism to reduce the amount of work needed during recovery.

### **How Checkpoints Work?**

- The DBMS periodically **writes all committed transactions to disk**.
- If a crash occurs, transactions before the checkpoint **do not need recovery**.

### **Checkpoint Steps**

1. **Write "START CHECKPOINT" to log.**
2. **Flush all modified data from memory to disk.**
3. **Write "END CHECKPOINT" to log.**

### **Benefits of Checkpoints**

✅ **Faster recovery** after failure  
✅ **Less need to redo transactions**  
✅ **Reduces log size**

### **Example of Recovery with Checkpoints**

```
Start Checkpoint
T1: Commit
T2: Commit
End Checkpoint
T3: Start (Crashes)
```

- After a crash, **only T3 needs recovery**, as previous transactions were checkpointed.

---

## **5. Deadlock Handling in DBMS**

A **deadlock** occurs when two or more transactions wait indefinitely for resources locked by each other.

### **Example of Deadlock**

```
T1 locks A → T2 locks B
T1 waits for B → T2 waits for A
```

- Neither `T1` nor `T2` can proceed.

### **Methods for Deadlock Handling**

1. **Deadlock Prevention**

   - Ensures that deadlocks **never happen** by following strategies:
     - **Wait-Die**: Older transactions wait; younger transactions abort.
     - **Wound-Wait**: Older transactions abort younger ones.

2. **Deadlock Detection & Resolution**

   - **Deadlock detection** algorithms periodically check for cycles in the **wait-for graph**.
   - If a deadlock is detected, the **victim transaction** is aborted.

3. **Deadlock Avoidance (Using Timestamping)**
   - Uses **timestamps** to decide which transactions should wait or abort.
   - Ensures that transactions **do not enter a deadlock state**.

---

## **6. Summary Table**

| **Concept**                | **Description**                                               |
| -------------------------- | ------------------------------------------------------------- |
| **Recoverability**         | Ensures transactions commit only after dependencies commit.   |
| **Recovery from Failures** | Uses logs (Undo/Redo) to restore database consistency.        |
| **Log-Based Recovery**     | Uses **Write-Ahead Logging (WAL)** for rollback/redo.         |
| **Checkpoints**            | Saves committed transactions to disk for **faster recovery**. |
| **Deadlock Handling**      | Uses **prevention, detection, or avoidance** strategies.      |

By implementing **recovery techniques and deadlock handling**, DBMS ensures **data consistency, durability, and high availability**. 🚀

## **`Gagan Saini`**
