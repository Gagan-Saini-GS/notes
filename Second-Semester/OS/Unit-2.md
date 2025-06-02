# Unit-2

## **Memory Management**

### **1. Swapping**

- **Definition:** Swapping is a memory management technique where processes are temporarily moved (swapped out) from main memory to secondary storage (usually disk) and brought back (swapped in) when needed.
- **Purpose:** To free up main memory so other processes can execute.
- **How it works:**

  - When memory is full, a process is suspended and swapped out to disk.
  - Later, it is swapped back into memory when CPU time is allocated.

- **Use case:** Useful in systems with limited physical memory or to enable multiprogramming.
- **Cost:** Swapping causes overhead due to slow disk I/O.

### **2. Contiguous Memory Allocation**

- **Definition:** Each process is allocated a single contiguous block of memory.
- **How it works:**

  - Memory is divided into partitions.
  - A process is loaded into a partition large enough to hold it.

- **Advantages:**

  - Simple to implement.
  - Easy to access memory using base and limit registers.

- **Disadvantages:**

  - **External fragmentation:** Free memory is broken into small blocks scattered across.
  - Difficult to allocate large contiguous blocks.

- **Memory protection:** Base and limit registers ensure a process cannot access memory outside its allocated range.

### **3. Paging**

- **Definition:** Paging is a memory management scheme that eliminates the need for contiguous allocation by dividing memory and processes into fixed-size blocks.

#### Key Concepts:

- **Page:** A fixed-size block of the process's logical memory.
- **Frame:** A fixed-size block of physical memory (same size as a page).

#### How it works:

- Logical memory is divided into pages.
- Physical memory is divided into frames.
- The OS maintains a **page table** mapping pages to frames.
- A process’s pages can be loaded into any available frames in physical memory, not necessarily contiguous.

#### Benefits:

- Eliminates external fragmentation.
- Efficient use of memory.
- Allows processes to use non-contiguous physical memory.

#### Example:

- Process with pages 0, 1, 2, 3.
- Pages can be stored in frames 5, 9, 3, 7 respectively.
- Address translation happens via the page table.

### **Summary Table**

| Concept                   | Description                                 | Pros                                        | Cons                                                    |
| ------------------------- | ------------------------------------------- | ------------------------------------------- | ------------------------------------------------------- |
| **Swapping**              | Moving whole processes to/from disk         | Enables multiprogramming                    | High overhead due to disk I/O                           |
| **Contiguous Allocation** | Allocating one continuous block per process | Simple, easy access                         | External fragmentation, poor flexibility                |
| **Paging**                | Divides memory into fixed-size pages/frames | Eliminates external fragmentation, flexible | Overhead of page table, internal fragmentation possible |

---

## **Segmentation with Virtual Paging (Segmented Paging)**

### **Segmentation**

- **Definition:** Divides a program's memory into **variable-sized segments**, each representing a logical unit like code, stack, heap, or data.
- Each segment has:

  - **Segment number**
  - **Offset** (displacement within the segment)

**Address = Segment Number + Offset**

### **Virtual Paging in Segmentation (Segmented Paging)**

- Combines **segmentation** and **paging**:

  - Each **segment** is **paged internally**.
  - Provides **logical division** (via segments) and **efficient memory use** (via paging).

#### How it works:

1. The **logical address** has three parts:
   `Segment Number | Page Number | Offset`
2. The **segment table** gives the **page table base** for that segment.
3. The **page table** gives the frame number for the page.
4. The frame and offset combine to form the physical address.

### ✅ Benefits:

- Supports **modular programming** (segmentation)
- Reduces **fragmentation** (paging)
- Flexible and efficient

---

## **Demand Paging**

### **Definition:**

- A memory management scheme where pages are **loaded into memory only when needed (on-demand)**.
- Not all pages of a process are loaded initially—only when accessed.

### **Mechanism:**

1. A page is **referenced** but not in memory.
2. This causes a **page fault**.
3. The OS:

   - Finds a **free frame**.
   - Loads the **required page** from disk.
   - Updates the **page table**.

4. The process resumes.

### ✅ Advantages:

- Saves memory.
- Enables **larger programs** to run on limited RAM.
- Improves **system performance** with effective page usage.

### ⚠️ Disadvantages:

- Too many page faults lead to **thrashing** (constant disk I/O, little actual work done).

---

## **Page Replacement Algorithms**

When a page fault occurs and **no free frame** is available, the OS must **replace** an existing page.

### **Common Algorithms:**

#### a. **FIFO (First-In, First-Out)**

- Replace the oldest page in memory.

```plaintext
Simple but can evict frequently used pages (Belady’s Anomaly).
```

#### b. **LRU (Least Recently Used)**

- Replaces the page that hasn't been used for the **longest time**.

```plaintext
Good performance, but requires tracking page usage history.
```

#### c. **Optimal Page Replacement**

- Replace the page that **will not be used for the longest future duration**.

```plaintext
Theoretical best; used for benchmarking, not practical (future unknown).
```

#### d. **Clock (Second Chance)**

- Modified version of FIFO using a circular queue and reference bits.

```plaintext
Efficient and performs nearly as well as LRU.
```

---

### ✅ Summary Table

| Algorithm | Concept                          | Pros                    | Cons                         |
| --------- | -------------------------------- | ----------------------- | ---------------------------- |
| FIFO      | Oldest page replaced             | Easy to implement       | Belady’s Anomaly             |
| LRU       | Least recently used page         | Good performance        | Needs time/history tracking  |
| Optimal   | Future usage prediction          | Best possible results   | Impractical in real time     |
| Clock     | Second chance with reference bit | Efficient approximation | May miss optimal replacement |

---

### 🔁 Example: LRU Simulation in Python

```python
def lru(pages, capacity):
    memory = []
    page_faults = 0

    for page in pages:
        if page not in memory:
            page_faults += 1
            if len(memory) == capacity:
                memory.pop(0)  # Remove LRU page
            memory.append(page)
        else:
            memory.remove(page)
            memory.append(page)  # Move to the most recent

    print(f"Total Page Faults (LRU): {page_faults}")

# Example usage
pages = [7, 0, 1, 2, 0, 3, 0, 4, 2]
capacity = 3
lru(pages, capacity)
```

---

## **Allocation of Frames**

A **frame** is a fixed-size block of physical memory, and **frame allocation** refers to deciding how many frames to give each process.

### **Types of Allocation:**

#### a. **Equal Allocation**

- Each process gets the **same number** of frames.
- Simple but **unfair** if processes vary in size.

#### b. **Proportional Allocation**

- Frames are allocated based on **process size**.

  Example:
  If total frames = 100, and process A is 20KB, B is 80KB:

  - A gets 20 frames, B gets 80.

#### c. **Priority Allocation**

- Higher priority processes receive more frames.
- Can lead to **starvation** of low-priority processes.

---

## **Thrashing**

### **Definition:**

- A condition where the system spends **more time swapping pages** than executing actual processes.

### **Causes:**

- Too many processes with **too few frames each**.
- High **page fault rate**.
- Poor allocation strategy.

### **Detection:**

- CPU utilization drops while page fault rate increases.

### **Solutions:**

- Reduce the degree of multiprogramming.
- Use **working set model** to allocate enough frames.
- Apply **page fault frequency (PFF)** control.

---

## **Page Size**

### **Definition:**

- The size of each page/frame (typically 4KB, 8KB, etc.)

### **Considerations:**

| Small Page Size               | Large Page Size               |
| ----------------------------- | ----------------------------- |
| + Less internal fragmentation | + Fewer page table entries    |
| + Better for small processes  | + Efficient disk I/O          |
| - Large page tables           | - More internal fragmentation |
| - Higher page table overhead  | - Memory wastage              |

### **Modern Trend:**

- Many systems use **multiple page sizes** (e.g., 4KB, 2MB, 1GB) to balance tradeoffs.

---

## **Other Considerations in Paging**

- **Page Table Size**: Large programs require large page tables. Solutions:

  - **Hierarchical paging**
  - **Inverted page tables**

- **TLB (Translation Lookaside Buffer)**: A cache that stores recent translations of virtual to physical addresses to reduce access time.
- **Page Replacement Policy**: Impacts performance; common ones include LRU, FIFO, etc.
- **Access Rights**: Read/write/execute permissions enforced per page.

---

## **Demand Segmentation**

### **Definition:**

- A memory management scheme similar to **demand paging**, but using **segments** instead of pages.

### **How it works:**

- Only required **segments** are loaded into memory on demand.
- When a segment is referenced but not in memory:

  - A **segment fault** occurs.
  - The segment is loaded from disk into memory.

### **Benefits:**

- Better logical organization (segments match program structure).
- Less overhead than paging for certain workloads.

### **Drawbacks:**

- **External fragmentation** still possible.
- Complex management of variable-sized segments.

---

## ✅ Summary Table

| Concept                 | Description                                           |
| ----------------------- | ----------------------------------------------------- |
| **Frame Allocation**    | Assigning physical memory frames to processes         |
| **Thrashing**           | Excessive paging causing poor performance             |
| **Page Size**           | Impacts fragmentation, table size, and I/O efficiency |
| **Demand Segmentation** | Load segments into memory only when accessed          |

---

## Files

### 📁 1. **File Systems**

A **file system** organizes and manages how data is stored and retrieved on storage devices like hard drives and SSDs. It handles:

- **File creation, deletion, reading, writing**
- **Directory management**
- **Access control**
- **Data integrity and recovery**

### 📄 2. **File Concept**

A **file** is a named collection of related data stored on secondary storage.

#### File Attributes:

- Name
- Type (e.g., `.txt`, `.jpg`)
- Location (disk address)
- Size
- Creation/access/modification time
- Owner and permissions

#### File Operations:

- Create, open, close
- Read, write
- Seek (move file pointer)
- Delete, rename
- Truncate (clear file contents)

### 📂 3. **Access Methods**

Access methods define how data in a file is accessed.

#### a. **Sequential Access**

- Data is read/written in order.
- Simple and efficient for tapes, logs.
- Example: reading a text file line by line.

#### b. **Direct (Random) Access**

- Data can be accessed at any location.
- Ideal for databases, binary files.

#### c. **Indexed Access**

- An index maps keys to file locations.
- Faster access using search keys.
- Common in large databases.

### 📁 4. **Directory Structure**

Directories store information about files (metadata) and help organize files.

#### Types of Directory Structures:

| Type                | Description                                  |
| ------------------- | -------------------------------------------- |
| **Single-Level**    | All files in one directory                   |
| **Two-Level**       | One directory per user                       |
| **Tree-Structured** | Hierarchical directories with subdirectories |
| **Acyclic Graph**   | Allows sharing files among directories       |
| **General Graph**   | More flexible but needs cycle detection      |

### 💾 5. **Secondary Storage Structure**

Secondary storage refers to **non-volatile** storage like HDDs, SSDs, and flash drives.

#### Common Structures:

- **Blocks**: Small fixed-size chunks of data.
- **Sectors**: Physical storage units on disks.
- **Tracks/Cylinders**: Circular paths where data is stored (on HDDs).

#### Disk Scheduling Algorithms (for HDDs):

- **FCFS**, **SSTF**, **SCAN**, **LOOK** (optimize read/write head movement)
- SSDs don’t require such scheduling due to no moving parts.

### ⚙️ 6. **Efficiency and Performance**

#### Key Factors:

- **Block size**: Small blocks reduce waste but increase overhead.
- **Disk caching**: Speeds up access using RAM as a buffer.
- **Buffering**: Temporarily holds data during transfer.
- **Prefetching**: Loads anticipated data in advance.

#### File Allocation Methods:

| Method         | Description                                       | Pros               | Cons                   |
| -------------- | ------------------------------------------------- | ------------------ | ---------------------- |
| **Contiguous** | Files occupy continuous blocks                    | Fast access        | External fragmentation |
| **Linked**     | Files are chains of blocks with pointers          | No fragmentation   | Slow random access     |
| **Indexed**    | Each file has an index block with block addresses | Fast direct access | Index block overhead   |

### 🛠️ 7. **Recovery**

When systems crash or disks fail, file systems must **recover lost or corrupted data**.

#### Recovery Techniques:

##### a. **Backup and Restore**

- Periodic backup of files to a separate location.
- Can restore lost files.

##### b. **Journaling File System**

- Keeps a log (journal) of changes.
- If crash occurs, the journal is replayed to recover consistent state.
- Examples: NTFS (Windows), ext4 (Linux)

##### c. **Checkpoints**

- Mark a safe consistent state; recovery rolls back to last checkpoint.

##### d. **Shadow Paging**

- Keeps a duplicate page; changes are made to a copy and swapped only after a successful write.

### ✅ Summary Table

| Concept                  | Description                                                        |
| ------------------------ | ------------------------------------------------------------------ |
| **File System**          | Organizes storage and access to files                              |
| **Access Methods**       | Sequential, direct, indexed access                                 |
| **Directory Structures** | Organizes files hierarchically                                     |
| **Secondary Storage**    | Non-volatile memory, block-based storage                           |
| **Efficiency**           | Depends on allocation, caching, scheduling                         |
| **Recovery**             | Journaling, backups, checkpoints ensure data is safe after crashes |

---

## **`Gagan Saini`**
