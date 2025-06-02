# Unit-3

## 🔄 **Concurrency Control**

In multiprogramming and multithreading environments, multiple processes or threads may access shared data or resources **simultaneously**.
To prevent **data inconsistency** or **race conditions**, concurrency must be controlled using synchronization tools.

### 🔐 1. **The Critical-Section Problem**

#### What is a Critical Section?

- A **critical section** is a part of a process where it accesses **shared resources** (e.g., variables, files).
- Only **one process** should be allowed in its critical section at any given time to prevent inconsistencies.

#### Problem Statement:

Design a solution for `n` processes such that:

| Requirement          | Description                                                                                     |
| -------------------- | ----------------------------------------------------------------------------------------------- |
| **Mutual Exclusion** | Only one process can enter its critical section at a time.                                      |
| **Progress**         | If no process is in the critical section, only those wanting to enter can decide who goes next. |
| **Bounded Waiting**  | A limit exists on how many times other processes can enter before one is allowed.               |

#### Structure of a Typical Process

```c
do {
    // Entry Section
    // Critical Section
    // Exit Section
    // Remainder Section
} while (true);
```

### 🛑 2. **Semaphores**

Semaphores are a **synchronization tool** introduced by Dijkstra to solve the critical-section problem.

#### Types of Semaphores

| Type         | Description                                                          |
| ------------ | -------------------------------------------------------------------- |
| **Binary**   | 0 or 1 value, acts like a mutex (lock/unlock)                        |
| **Counting** | Can hold any non-negative integer, used for managing a resource pool |

#### Semaphore Operations (Atomic)

```c
wait(S):   // Also called P(S)
    while (S <= 0);   // Busy wait
    S = S - 1;

signal(S): // Also called V(S)
    S = S + 1;
```

> **Note:** In modern systems, busy waiting is avoided using blocking mechanisms.

#### Example: Solving Critical-Section with Binary Semaphore

```c
Semaphore mutex = 1;

Process Pi:
do {
    wait(mutex);         // Entry section
    // Critical Section
    signal(mutex);       // Exit section
    // Remainder Section
} while (true);
```

This ensures **mutual exclusion**: only one process can decrement the semaphore and enter the critical section.

### 🧠 Key Concepts Summary

| Concept              | Role                                                |
| -------------------- | --------------------------------------------------- |
| **Critical Section** | Code that accesses shared resource                  |
| **Race Condition**   | When multiple threads update shared data at once    |
| **Mutual Exclusion** | Ensures only one thread/process in critical section |
| **Semaphore**        | A synchronization primitive using counters          |
| **Busy Waiting**     | Inefficient loop that waits for a resource          |

---

## 🔄 **Classical Synchronization Problems**

These problems highlight key synchronization challenges like mutual exclusion, deadlocks, starvation, and race conditions.

### ✅ 1. **Bounded Buffer Problem**

(Also known as the **Producer-Consumer Problem**)

**Scenario**:

- A **producer** produces items and puts them in a buffer.
- A **consumer** removes items from the buffer.
- The buffer has a **fixed size (N)** — bounded.

**Constraints**:

- Producer must wait if buffer is **full**.
- Consumer must wait if buffer is **empty**.
- Access to buffer must be **mutually exclusive**.

**Solution (using semaphores)**:

```c
Semaphore mutex = 1;        // for mutual exclusion
Semaphore full = 0;         // count of full slots
Semaphore empty = N;        // count of empty slots

Producer:
do {
    produce_item();
    wait(empty);
    wait(mutex);
    insert_item();
    signal(mutex);
    signal(full);
} while (true);

Consumer:
do {
    wait(full);
    wait(mutex);
    remove_item();
    signal(mutex);
    signal(empty);
    consume_item();
} while (true);
```

### ✅ 2. **Readers-Writers Problem**

**Scenario**:

- Multiple **readers** can read a shared database **simultaneously**.
- **Writers** need **exclusive access**.

**Problem**:

- Allow multiple readers but ensure only one writer at a time.
- Avoid starvation (especially of writers or readers).

#### Variants:

- **First readers–writers problem**: No reader waits unless a writer has access.
- **Second readers–writers problem**: Writers are given preference.

**Solution (basic idea)**:

```c
Semaphore mutex = 1;
Semaphore wrt = 1;
int readcount = 0;

Reader:
wait(mutex);
readcount++;
if (readcount == 1)
    wait(wrt);
signal(mutex);

// reading

wait(mutex);
readcount--;
if (readcount == 0)
    signal(wrt);
signal(mutex);

Writer:
wait(wrt);
// writing
signal(wrt);
```

### ✅ 3. **Dining Philosophers Problem**

**Scenario**:

- Five philosophers sitting around a table.
- Each needs **two forks** to eat.
- One fork between each philosopher.

**Problem**:

- Prevent **deadlock**, **starvation**, and **race conditions**.

**Naive solution (causes deadlock)**:

```c
wait(left_fork);
wait(right_fork);
eat();
signal(left_fork);
signal(right_fork);
```

**Improved Solution**:

- Use a waiter/arbiter.
- Allow only **4 philosophers** to try to pick forks at the same time.
- Pick up both forks **only if both are available**.

### ✅ 4. **Sleeping Barber Problem**

**Scenario**:

- One barber, one barber chair, and a waiting room with `N` chairs.
- Customers arrive and either wait or leave if full.
- Barber sleeps when no customers.

**Solution** involves semaphores for:

- **Waiting customers**
- **Barber readiness**
- **Mutual exclusion on chairs**

### 📊 Summary Table

| Problem             | Key Challenge                      | Synchronization Focus           |
| ------------------- | ---------------------------------- | ------------------------------- |
| Bounded Buffer      | Full/Empty buffer access           | Producer-consumer coordination  |
| Readers-Writers     | Multiple readers, exclusive writer | Reader-writer fairness          |
| Dining Philosophers | Shared resources (forks)           | Deadlock and starvation         |
| Sleeping Barber     | Limited waiting space              | Producer-consumer with sleeping |

---

## 🔒 **Critical Regions**

### Definition:

A **critical region** is a **high-level language construct** that ensures **only one process/thread** can execute a specific section of code accessing shared variables.

### Concept:

Languages like Pascal or Modula-2 introduce **region constructs** for controlled access:

```pascal
region v do
    S;
```

- `v`: shared variable (protected resource)
- `S`: code block (critical section)
- Only one process can execute `S` with `v` at a time.

**Note:** Not commonly supported in modern languages—replaced by semaphores, mutexes, or monitors.

---

## 🖥️ **Monitors**

### Definition:

A **monitor** is a **high-level abstraction** that encapsulates:

- Shared variables
- Procedures that operate on the shared variables
- Synchronization (only one process active in the monitor at a time)

### Key Properties:

- Mutual exclusion is **automatically handled**.
- Uses **condition variables** for signaling.

```java
monitor Buffer {
    int[] buffer;
    int count = 0;
    condition notEmpty, notFull;

    procedure insert(item) {
        if (count == buffer.length)
            wait(notFull);
        buffer[count++] = item;
        signal(notEmpty);
    }

    procedure remove() {
        if (count == 0)
            wait(notEmpty);
        item = buffer[--count];
        signal(notFull);
        return item;
    }
}
```

---

## 🍝 **Dining Philosophers Problem (Using Semaphores)**

```c
Semaphore forks[5];
Semaphore mutex = 1;

philosopher(i):
do {
    think();
    wait(mutex);
    wait(forks[i]);
    wait(forks[(i+1)%5]);
    signal(mutex);

    eat();

    signal(forks[i]);
    signal(forks[(i+1)%5]);
} while (true);
```

> This avoids deadlock by acquiring a global mutex before picking up forks. There are better versions using numbered philosophers or limiting concurrency.

---

## 🍲 **Producer-Consumer Problem**

### ✅ a. **Using Semaphores**

```c
Semaphore mutex = 1;
Semaphore full = 0;
Semaphore empty = N;

Producer:
do {
    produce_item();
    wait(empty);
    wait(mutex);
    insert_item();
    signal(mutex);
    signal(full);
} while (true);

Consumer:
do {
    wait(full);
    wait(mutex);
    remove_item();
    signal(mutex);
    signal(empty);
    consume_item();
} while (true);
```

### ✅ b. **Using Monitors**

```java
monitor BoundedBuffer {
    final int size = 5;
    int[] buffer = new int[size];
    int in = 0, out = 0, count = 0;
    condition notFull, notEmpty;

    void insert(int item) {
        if (count == size)
            wait(notFull);
        buffer[in] = item;
        in = (in + 1) % size;
        count++;
        signal(notEmpty);
    }

    int remove() {
        if (count == 0)
            wait(notEmpty);
        int item = buffer[out];
        out = (out + 1) % size;
        count--;
        signal(notFull);
        return item;
    }
}
```

## 🧠 Summary Comparison

| Feature              | Semaphores                   | Monitors                                    |
| -------------------- | ---------------------------- | ------------------------------------------- |
| **Level**            | Low-level (prone to errors)  | High-level (language-supported abstraction) |
| **Mutual Exclusion** | Must be implemented manually | Built-in                                    |
| **Complexity**       | Higher, more flexible        | Simpler, more readable                      |
| **Deadlock Risk**    | Higher (if used incorrectly) | Lower (with correct use of condition vars)  |

---

## 💀 **Deadlocks**

A **deadlock** is a situation where a set of processes are **permanently blocked**, each waiting for a resource held by another.

### 🧩 1. **System Model**

A deadlock occurs in a system with:

- **Processes (P₁, P₂, ..., Pₙ)**
- **Resources (R₁, R₂, ..., Rₘ)** — such as CPU cycles, memory, I/O devices, files, semaphores

#### Resource Types

- **Preemptable**: can be taken back (e.g., CPU)
- **Non-preemptable**: can’t be forcibly removed (e.g., printer)

#### Process States (in resource use):

1. **Requesting** a resource
2. **Using** (holding) a resource
3. **Releasing** a resource

#### Resource Allocation Graph (RAG):

- **Nodes**: processes (circles), resources (squares)
- **Edges**:

  - **Request Edge (P → R)**: process is requesting resource
  - **Assignment Edge (R → P)**: resource is assigned to process

> **Cycle in RAG**:

- **Single instance per resource**: cycle ⇒ deadlock
- **Multiple instances**: cycle ≠ deadlock (but possible)

### 🔎 2. **Deadlock Characterization**

#### A deadlock can occur if **all four** of the following **Coffman conditions** are **true simultaneously**:

| Condition               | Description                                                                                                            |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **1. Mutual Exclusion** | At least one resource must be non-shareable.                                                                           |
| **2. Hold and Wait**    | A process holding at least one resource is waiting for additional ones.                                                |
| **3. No Preemption**    | Resources can’t be forcibly taken away from a process.                                                                 |
| **4. Circular Wait**    | There exists a set of processes {P₁, P₂, ..., Pₙ} where Pᵢ is waiting for a resource held by Pᵢ₊₁, and Pₙ waits on P₁. |

> **If any one condition is broken, deadlock cannot occur.**

### 🔁 Circular Wait Example:

```text
P1 → waiting for R1 held by P2
P2 → waiting for R2 held by P3
P3 → waiting for R3 held by P1
=> Deadlock!
```

### 🧠 Summary Table

| Topic                    | Details                                                       |
| ------------------------ | ------------------------------------------------------------- |
| **System Model**         | Processes request, hold, and release resources                |
| **Graph Representation** | Request → edge; Assignment ← edge                             |
| **Cycle Detection**      | Cycle = potential or definite deadlock                        |
| **4 Conditions**         | Mutual exclusion, Hold and wait, No preemption, Circular wait |

### 🔐 **Deadlock Prevention**

**Goal**: Ensure that **at least one of the four Coffman conditions** is **never satisfied**, thus preventing deadlock.

| Condition            | How to Prevent It                                                |
| -------------------- | ---------------------------------------------------------------- |
| **Mutual Exclusion** | Make resources sharable (not always possible)                    |
| **Hold and Wait**    | Require processes to request all resources at once               |
| **No Preemption**    | Allow preemption — take resources from waiting processes         |
| **Circular Wait**    | Impose an ordering on resources; processes request in that order |

#### Example: Circular Wait Prevention

Assign a **numerical order** to all resources. Processes must request resources in **increasing order** only.

### 🧭 **Deadlock Avoidance**

**Goal**: Avoid unsafe states that could lead to deadlock.

#### Safe State

A state is **safe** if the system can allocate resources to all processes in some order without deadlock.

> In a safe state, there exists at least one **safe sequence** of process execution.

### 🔍 **Deadlock Detection**

**Goal**: Let deadlock happen, then detect and recover.

#### For Single Instance per Resource:

Use **Wait-For Graph**:

- Remove resource nodes from RAG.
- If a **cycle exists** → **deadlock**.

#### For Multiple Instances:

Use an algorithm similar to the **Banker’s Safety Algorithm** but without checking "what if":

- Mark processes that can finish with current available
- If a process can't finish and is unmarked → **deadlocked**

---

## 🏦 **Banker’s Algorithm** (by Dijkstra)

Used for **deadlock avoidance**. Works like a banker deciding whether to grant a loan.

### 🧱 Assumptions:

- Known number of processes `n` and resource types `m`
- Each process declares its **maximum need**
- Resources are allocated if the system **remains in a safe state**

### Data Structures:

Let:

- `Available[m]`: Available instances of each resource type
- `Max[n][m]`: Maximum demand of each process
- `Allocation[n][m]`: Currently allocated resources
- `Need[n][m] = Max - Allocation`: Remaining need

### ✅ **Safety Algorithm (to Check if State is Safe)**

```plaintext
1. Initialize:
   Work = Available
   Finish[i] = false for all i

2. Find a process i such that:
   Finish[i] == false and Need[i] <= Work
   If found:
      Work = Work + Allocation[i]
      Finish[i] = true
      Repeat step 2

3. If all Finish[i] == true, the system is in a safe state
```

### 🔄 **Resource Request Algorithm**

When process `Pᵢ` requests `Request[i]`:

1. If `Request[i] <= Need[i]`, continue.
2. If `Request[i] <= Available`, pretend to allocate:

   - `Available -= Request[i]`
   - `Allocation[i] += Request[i]`
   - `Need[i] -= Request[i]`

3. Run the **Safety Algorithm**:

   - If safe → **grant request**
   - If not → **deny request** (rollback)

### 📌 Banker’s Algorithm Example

| Process | Max | Allocation | Need |
| ------- | --- | ---------- | ---- |
| P1      | 7   | 3          | 4    |
| P2      | 5   | 2          | 3    |
| P3      | 3   | 2          | 1    |

If Available = 2, we check if any Need ≤ Available. If yes, simulate allocation and test for safety.

### 🧠 Summary Table

| Strategy               | Description                             | Risk of Deadlock |
| ---------------------- | --------------------------------------- | ---------------- |
| **Prevention**         | Break one of the 4 conditions           | No               |
| **Avoidance**          | Allocate only in safe state             | No               |
| **Detection**          | Detect and recover after deadlock       | Yes              |
| **Banker's Algorithm** | Dynamic check for safe state on request | No               |

---

## **`Gagan Saini`**
