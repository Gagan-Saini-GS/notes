# Unit-1

## **Introduction to Operating System & Process Management**

### **1. Definition of Operating System**

An **Operating System (OS)** is system software that acts as an intermediary between users and computer hardware. It manages hardware resources and provides services for computer programs.

### **2. Types of Operating Systems**

Operating Systems can be categorized based on how they handle tasks and users:

#### a. **Batch Operating System**

- Executes batches of jobs without user interaction.
- Used in early computers.
- Example: IBM OS/360.

#### b. **Time-Sharing Operating System**

- Allows multiple users to use the system simultaneously.
- CPU time is divided among users (multitasking).
- Example: UNIX.

#### c. **Distributed Operating System**

- Manages a group of distinct computers and makes them appear as a single computer.
- Resources are shared among systems.
- Example: LOCUS.

#### d. **Real-Time Operating System (RTOS)**

- Responds to input instantly and is used in time-critical environments.
- Example: VxWorks, RTLinux.

#### e. **Network Operating System**

- Provides services to computers connected over a network.
- Example: Novell NetWare.

#### f. **Mobile Operating System**

- Designed specifically for mobile devices.
- Example: Android, iOS.

### **3. Operating System Components and Services**

#### a. **Main Components**

1. **Kernel** – Core component managing CPU, memory, and devices.
2. **Process Manager** – Manages processes and threads.
3. **Memory Manager** – Handles allocation and deallocation of memory.
4. **File System** – Manages files and directories.
5. **Device Manager** – Controls hardware devices.
6. **User Interface** – CLI or GUI for user interaction.

#### b. **Main Services Provided**

- **Program execution**: Load and run programs.
- **I/O operations**: Input and output device management.
- **File system manipulation**: Create, read, write, and delete files.
- **Communication**: Inter-process communication (IPC).
- **Error detection**: Monitor and report errors.
- **Resource allocation**: Distribute CPU, memory, etc.
- **Security and protection**: Safeguard data and user access.

### **4. System Calls**

**System calls** are interfaces between a process and the operating system. They allow user-level processes to request services from the OS.

#### Types of System Calls:

1. **Process control** – `fork()`, `exit()`, `wait()`
2. **File management** – `open()`, `read()`, `write()`, `close()`
3. **Device management** – `ioctl()`, `read()`, `write()`
4. **Information maintenance** – `getpid()`, `alarm()`, `sleep()`
5. **Communication** – `pipe()`, `shmget()`, `msgsnd()`

---

## **Process Management**

### **1. Process Concept**

A **process** is an instance of a program in execution. It includes:

- **Program code** (text section)
- **Program counter** (next instruction)
- **Stack** (function parameters, return addresses, local variables)
- **Heap** (dynamically allocated memory)
- **Data section** (global variables)

#### **States of a Process**:

A process goes through various states during its lifetime:

1. **New** – Process is being created.
2. **Ready** – Waiting to be assigned to the CPU.
3. **Running** – Instructions are being executed.
4. **Waiting** – Waiting for an event (e.g., I/O).
5. **Terminated** – Finished execution.

#### **Process Control Block (PCB)**:

The OS maintains a **PCB** for each process, containing:

- Process ID (PID)
- State
- Program counter
- CPU registers
- Memory management info
- Accounting info
- I/O status

### **2. Process Scheduling**

**Process Scheduling** is the activity of the OS that selects which process should run next.

#### **Types of Schedulers**:

- **Long-term scheduler** – Controls admission of jobs to the system.
- **Short-term scheduler** – Selects from ready queue which process to run next.
- **Medium-term scheduler** – Swaps processes in and out of memory.

#### **Scheduling Algorithms**:

1. **First-Come, First-Served (FCFS)**
2. **Shortest Job Next (SJN)**
3. **Round Robin (RR)**
4. **Priority Scheduling**
5. **Multilevel Queue Scheduling**
6. **Multilevel Feedback Queue Scheduling**

Each has trade-offs in terms of CPU utilization, throughput, turnaround time, waiting time, and response time.

### **3. Operations on Processes**

The operating system supports several operations on processes:

#### a. **Process Creation**

- A process can create a new process using system calls like `fork()` (Unix) or `CreateProcess()` (Windows).
- The created process is called a **child process**.
- Parent and child may run concurrently.

#### b. **Process Termination**

- A process ends using an `exit()` system call.
- The parent may terminate the child using `kill()` or `terminateProcess()`.

#### c. **Process Hierarchy**

- In some systems, processes are organized in a **tree structure**, with parent-child relationships.

#### d. **Inter-Process Communication (IPC)**

Processes often need to communicate, especially in multitasking systems. IPC methods include:

- **Shared memory**
- **Message passing**
- **Pipes**
- **Sockets**

---

## **Inter-Process Communication (IPC)**

### **What is IPC?**

**Inter-Process Communication (IPC)** is a mechanism that allows processes to **exchange data and coordinate actions** with one another. It is essential in a **multiprocessing environment**, where multiple processes run concurrently and need to cooperate.

Processes can be:

- **Independent** – Do not share data or communicate.
- **Cooperating** – Share data and work together, requiring communication.

### **Why IPC is Needed**

- **Data sharing** – E.g., between a client and a server process.
- **Computation speed-up** – Split tasks across processes.
- **Modularity** – Keep tasks in separate processes.
- **Convenience** – Communicate results or control messages.

### **Types of IPC Mechanisms**

#### **1. Shared Memory**

- Processes share a portion of memory.
- Fastest method because no kernel involvement after setup.
- Requires synchronization (e.g., semaphores or mutexes) to prevent race conditions.

> 🧠 Example: One process writes data to a shared buffer; another reads from it.

#### **2. Message Passing**

- Processes send and receive messages using system calls.
- No shared memory needed.
- Easier to implement but slower due to system call overhead.

##### Methods:

- **Direct communication** – Processes must name each other explicitly.
- **Indirect communication** – Messages go through **mailboxes** or **message queues**.

> 📬 Example: `send(P, message)`, `receive(Q, message)`

#### **3. Pipes**

- Unidirectional communication channel.
- Often used between related processes (e.g., parent-child).
- Two types:

  - **Anonymous Pipes** – Limited to parent-child processes.
  - **Named Pipes (FIFOs)** – Can be used between unrelated processes.

> 🧪 Example: Unix shell command `ls | sort` uses a pipe.

#### **4. Sockets**

- Used for communication between processes **on different machines** (over a network).
- Provides **bidirectional** communication.
- Basis of most networked applications.

> 🌐 Example: A web browser (client) communicating with a web server.

#### **5. Message Queues**

- Allows messages to be placed in a queue and read in order.
- Can persist even after sender/receiver processes end.

#### **6. Signals**

- Used to notify a process that a particular event has occurred.
- Limited communication (only signal, no data).

### **Synchronization in IPC**

When multiple processes communicate, especially via shared memory, **synchronization** is essential to avoid issues like:

- **Race conditions**
- **Deadlocks**
- **Data inconsistency**

Mechanisms used:

- **Semaphores**
- **Mutexes (Mutual Exclusion Locks)**
- **Monitors**
- **Condition variables**

### **Summary Table**

| Mechanism       | Direction          | Scope              | Speed     | Use Case Example              |
| --------------- | ------------------ | ------------------ | --------- | ----------------------------- |
| Shared Memory   | Bi-directional     | Same machine       | Very fast | Video editing, databases      |
| Message Passing | Uni/Bi-directional | Local or remote    | Moderate  | Microservices, kernel comms   |
| Pipes           | Unidirectional     | Same machine       | Fast      | Shell pipelines               |
| Sockets         | Bi-directional     | Local or networked | Slower    | Web apps, network services    |
| Signals         | One-way            | Same machine       | Very fast | Error handling, notifications |

---

## **Threads & Thread Management**

### **1. What is a Thread?**

A **thread** is the **smallest unit of execution** within a process.
While a **process** is an independent program with its own memory space, **threads** are like lightweight subprocesses that **share the same memory and resources** (code, data, files) of the parent process but run independently.

#### Example:

Think of a web browser:

- One thread handles the UI.
- Another downloads a file.
- A third renders video.

All part of the same process, but doing different tasks concurrently.

### **2. Benefits of Threads**

- **Responsiveness**: UI remains active even while doing background tasks.
- **Resource Sharing**: Threads within the same process share memory and resources.
- **Efficiency**: Thread creation and context switching are faster than processes.
- **Scalability**: Takes advantage of multicore processors.

### **3. Types of Threads**

#### a. **User-Level Threads (ULT)**

- Managed by a user-level thread library (e.g., POSIX pthreads).
- OS is unaware of them.
- Fast to create and manage, but if one thread blocks, all do.

#### b. **Kernel-Level Threads (KLT)**

- Managed by the OS.
- Each thread is scheduled individually by the kernel.
- Slower to create/manage, but better performance under load.

#### c. **Hybrid Threads**

- Combine benefits of ULTs and KLTs.
- Multiple user threads map to multiple kernel threads.
- Example: Many-to-Many or Two-level models.

### **4. Thread Lifecycle**

A thread typically goes through the following states:

1. **New** – Thread is created.
2. **Ready** – Waiting to be assigned CPU.
3. **Running** – Being executed.
4. **Waiting** – Waiting for a resource or event.
5. **Terminated** – Execution completed or forcibly stopped.

### **5. Thread Operations**

#### Common operations include:

- **Thread creation** – `pthread_create()` in C, `Thread t = new Thread()` in Java.
- **Thread termination** – Ends after execution or explicitly via `pthread_exit()`, `thread.exit()`.
- **Thread joining** – Waits for a thread to finish: `pthread_join()` or `thread.join()`.
- **Thread synchronization** – Ensures proper data access:

  - **Mutexes**
  - **Semaphores**
  - **Condition variables**
  - **Locks and Monitors**

### **6. Thread Management in Operating Systems**

The OS is responsible for:

- Scheduling threads on available CPUs.
- Switching contexts between threads.
- Managing thread states.
- Synchronizing thread activities to prevent race conditions and deadlocks.

#### Example (Linux):

- Linux uses **POSIX threads (pthreads)**.
- Threads are treated as lightweight processes.
- Thread scheduling is handled by the **kernel**.

### **7. Multithreading Models**

| Model            | Description                                                                             |
| ---------------- | --------------------------------------------------------------------------------------- |
| **Many-to-One**  | Many user threads map to one kernel thread. Efficient but one thread block affects all. |
| **One-to-One**   | Each user thread maps to one kernel thread. More control and concurrency.               |
| **Many-to-Many** | Many user threads mapped to many kernel threads. Flexible and efficient.                |

### **Comparison: Process vs Thread**

| Aspect        | Process               | Thread                      |
| ------------- | --------------------- | --------------------------- |
| Memory        | Separate memory space | Shared memory               |
| Creation time | Slower                | Faster                      |
| Communication | Through IPC           | Through shared variables    |
| Overhead      | High                  | Low                         |
| Dependency    | Independent           | Dependent on parent process |

---

## **CPU Scheduling**

### **1. CPU Scheduling Criteria**

When designing or selecting a CPU scheduling algorithm, several criteria are considered to evaluate performance and suitability:

| Criteria            | Description                                                 |
| ------------------- | ----------------------------------------------------------- |
| **CPU Utilization** | Keep the CPU as busy as possible (aim for high %)           |
| **Throughput**      | Number of processes completed per time unit                 |
| **Turnaround Time** | Total time taken from submission to completion of a process |
| **Waiting Time**    | Total time a process spends waiting in the ready queue      |
| **Response Time**   | Time from submission until first response/output            |
| **Fairness**        | Ensure all processes get a fair share of CPU                |

### **2. Scheduling Algorithms**

#### a. **First-Come, First-Served (FCFS)**

- Non-preemptive
- Processes executed in order of arrival
- Simple but can cause **convoy effect** (long wait times)

#### b. **Shortest Job Next (SJN) / Shortest Job First (SJF)**

- Select process with the smallest burst time
- Can be preemptive or non-preemptive
- Minimizes average waiting time
- Needs knowledge of burst time (not always possible)

#### c. **Round Robin (RR)**

- Preemptive, each process gets a fixed time slice (quantum)
- Fair time-sharing
- Performance depends on quantum size

#### d. **Priority Scheduling**

- Each process assigned a priority; highest priority runs first
- Can be preemptive or non-preemptive
- Risk of **starvation** for low-priority processes

#### e. **Multilevel Queue Scheduling**

- Separate queues for different types of processes (e.g., foreground, background)
- Each queue can have its own scheduling algorithm
- Processes assigned permanently to a queue

#### f. **Multilevel Feedback Queue Scheduling**

- Similar to multilevel queue but allows processes to move between queues based on behavior and aging
- Addresses starvation by gradually increasing priority of waiting processes

### **3. Multiprocessor Scheduling**

- Deals with scheduling processes across multiple CPUs/cores.
- Types:

  - **Asymmetric multiprocessing**: One CPU schedules all processes, others execute.
  - **Symmetric multiprocessing (SMP)**: All CPUs are equal; each runs its own scheduler.

- Challenges:

  - Load balancing: Distribute processes evenly.
  - Processor affinity: Keep a process on the same CPU for cache benefits.
  - Synchronization overhead between CPUs.

### **4. Real-Time Scheduling**

Designed for systems where tasks must meet strict timing constraints.

#### Types:

- **Hard Real-Time Systems**: Missing a deadline is catastrophic.
- **Soft Real-Time Systems**: Missing deadlines degrades performance but is not critical.

#### Algorithms:

- **Rate Monotonic Scheduling (RMS)**: Fixed priority; shorter period = higher priority.
- **Earliest Deadline First (EDF)**: Dynamic priority; tasks closest to deadline run first.
- **Deadline Monotonic Scheduling**: Fixed priority based on deadlines.

### **5. Scheduling Evaluation**

Evaluation involves both **analytical** and **experimental** methods:

- **Simulation**: Run workloads through scheduling algorithms to compare performance.
- **Mathematical analysis**: Compute average waiting time, turnaround time, etc.
- **Benchmarks**: Use real workloads to measure CPU utilization, throughput.
- **Fairness and starvation**: Check if all processes get CPU time.

### **Summary Table of Scheduling Algorithms**

| Algorithm                 | Preemptive | Advantages                   | Disadvantages                    | Use Case                |
| ------------------------- | ---------- | ---------------------------- | -------------------------------- | ----------------------- |
| FCFS                      | No         | Simple, easy to implement    | Poor turnaround and waiting time | Batch systems           |
| SJF (Non-preemptive)      | No         | Optimal average waiting time | Requires burst time knowledge    | Offline scheduling      |
| Round Robin               | Yes        | Fair, good for time-sharing  | High context switching overhead  | Interactive systems     |
| Priority Scheduling       | Yes/No     | Supports priorities          | Starvation risk                  | Priority-based systems  |
| Multilevel Queue          | Yes/No     | Separate handling of types   | Rigid queues, starvation         | Multi-user systems      |
| Multilevel Feedback Queue | Yes        | Flexible, reduces starvation | Complex to implement             | General purpose OS      |
| RMS (Real-time)           | No         | Predictable and simple       | Only for fixed tasks             | Hard real-time systems  |
| EDF (Real-time)           | Yes        | Optimal dynamic scheduling   | Complex, overhead                | Soft and hard real-time |

---

## **Code**

### 1. **First-Come, First-Served (FCFS)**

```python
def fcfs(processes):
    start_time = 0
    waiting_times = []
    turnaround_times = []

    for burst_time in processes:
        waiting_times.append(start_time)
        turnaround_times.append(start_time + burst_time)
        start_time += burst_time

    avg_wait = sum(waiting_times) / len(processes)
    avg_turnaround = sum(turnaround_times) / len(processes)

    print(f"FCFS Average Waiting Time: {avg_wait}")
    print(f"FCFS Average Turnaround Time: {avg_turnaround}")

# Example processes with burst times
processes = [5, 3, 8, 6]
fcfs(processes)
```

### 2. **Round Robin Scheduling**

```python
def round_robin(processes, quantum):
    n = len(processes)
    remaining_bt = processes.copy()
    t = 0  # current time
    waiting_time = [0]*n
    finish_time = [0]*n

    while True:
        done = True
        for i in range(n):
            if remaining_bt[i] > 0:
                done = False
                if remaining_bt[i] > quantum:
                    t += quantum
                    remaining_bt[i] -= quantum
                else:
                    t += remaining_bt[i]
                    waiting_time[i] = t - processes[i]
                    remaining_bt[i] = 0
        if done:
            break

    avg_wait = sum(waiting_time) / n
    print(f"Round Robin Average Waiting Time: {avg_wait}")

processes = [5, 3, 8, 6]
quantum = 2
round_robin(processes, quantum)
```

### 3. **Shortest Job First (Non-preemptive)**

```python
def sjf(processes):
    n = len(processes)
    processes_sorted = sorted(processes)
    start_time = 0
    waiting_times = []
    turnaround_times = []

    for bt in processes_sorted:
        waiting_times.append(start_time)
        turnaround_times.append(start_time + bt)
        start_time += bt

    avg_wait = sum(waiting_times) / n
    avg_turnaround = sum(turnaround_times) / n
    print(f"SJF Average Waiting Time: {avg_wait}")
    print(f"SJF Average Turnaround Time: {avg_turnaround}")

processes = [5, 3, 8, 6]
sjf(processes)
```

---

## **`Gagan Saini`**
