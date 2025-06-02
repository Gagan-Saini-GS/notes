# Unit-4

## 💽 **Disk Structure**

### Basic Components:

- **Platters**: Circular disks stacked on a spindle, coated with magnetic material.
- **Tracks**: Concentric circles on a platter.
- **Sectors**: Each track is divided into sectors (smallest addressable unit).
- **Cylinders**: Set of tracks aligned vertically across platters.
- **Read/Write Head**: Moves over platters to read/write data.
- **Disk Arm**: Moves the head radially across platters.

### Addressing:

Disks are accessed via **CHS (Cylinder, Head, Sector)** or more commonly now by **LBA (Logical Block Addressing)**, which maps sectors linearly.

---

## 🚀 **Disk Scheduling Methods**

Since disk access time is affected by **seek time**, **rotational latency**, and **transfer time**, scheduling is used to **minimize seek time**.

### Common Scheduling Algorithms:

| Algorithm  | Description                                         | Pros                    | Cons                        |
| ---------- | --------------------------------------------------- | ----------------------- | --------------------------- |
| **FCFS**   | First-Come-First-Serve                              | Fair, simple            | May be inefficient          |
| **SSTF**   | Shortest Seek Time First                            | Faster than FCFS        | Can lead to starvation      |
| **SCAN**   | Elevator algorithm: moves back and forth            | Less starvation         | Can be slower for some jobs |
| **C-SCAN** | Like SCAN, but only in one direction                | More uniform wait time  | Longer for far requests     |
| **LOOK**   | Like SCAN but doesn't go to disk ends if not needed | Efficient seek handling | Similar to SCAN             |
| **C-LOOK** | LOOK but in one direction only                      | Uniform & efficient     | Skips some requests         |

### 📈 Example:

Given head at 50, and queue: 10, 22, 20, 2, 40, 6, 38

- **FCFS** → 10 → 22 → ...
- **SSTF** → closest to current head first
- **SCAN** → sweep from one end to another

---

## 🛠️ **Disk Management Tasks**

### a. **Partitioning**

- Dividing disk into logical parts (partitions)
- Each partition can hold different OS, or file systems

### b. **Logical Formatting**

- Creating file system structures (e.g., superblock, inode table, etc.)

### c. **Boot Block Management**

- Contains OS loader or boot manager
- BIOS/UEFI loads boot block during startup

### d. **Bad Block Management**

- Tracks and remaps bad sectors (low-level formatting or OS-level tools)

---

## 🛠️ **Recovery in Disk Management**

Recovery refers to restoring the system or disk to a **consistent and working state** after a **failure** such as a crash, power outage, or file system corruption.

### a. **Types of Recovery**

- **File System Recovery**: Fixing corrupted metadata or lost files.
- **Crash Recovery**: Restoring file system consistency after a crash.
- **Bad Sector Recovery**: Relocating data from bad sectors to healthy ones.

### b. **Techniques**

1. **Consistency Checking**

   - Tools: `fsck` (Linux), `chkdsk` (Windows)
   - Detects and fixes file system structure issues (like orphaned files).

2. **Journaled File Systems**

   - File systems like **ext4**, **NTFS**, **ReiserFS** use **journaling**.
   - Log all changes before applying them → easy rollback after crash.

3. **Backups & Snapshots**

   - Scheduled backups and **disk snapshots** (via LVM or backup software) help recover from hardware failure or human error.

4. **RAID**

   - Redundant array of independent disks offers redundancy for recovery.
   - E.g., RAID 1 (mirroring), RAID 5 (parity-based recovery).

---

## 🧠 Summary

| Topic                  | Key Points                                                    |
| ---------------------- | ------------------------------------------------------------- |
| **Disk Structure**     | Platters, tracks, sectors, cylinders, heads                   |
| **Scheduling Methods** | FCFS, SSTF, SCAN, C-SCAN, LOOK, C-LOOK                        |
| **Management Tasks**   | Partitioning, formatting, boot management, bad block tracking |
| **Recovery**           | Journaling, file system checks, backups, RAID                 |

---

Sure! Here's a clear and detailed explanation of **Swap-Space Management**, and **Protection and Security** in operating systems, including the **Goals of Protection**.

---

## 🔄 **Swap-Space Management**

Swap space is a portion of the disk used as **virtual memory** to supplement physical RAM. It temporarily holds pages that are not currently in use by the main memory.

### What is Swapping?

Swapping is the process of **moving processes or memory pages** between main memory (RAM) and swap space (disk) to **free up RAM**.

### Swap-Space Location:

- Typically a **dedicated partition** or **swap file** on the hard drive.

### Swap Usage in Virtual Memory:

When RAM is full:

- Inactive memory pages are moved to **swap space**.
- When needed again, they're brought back into RAM (causing a **page-in**).
- This mechanism supports **larger programs** and **multitasking**.

### Swap-Space Management Policies:

1. **Allocation Methods**:

   - **Fixed-size swap space** (pre-allocated)
   - **Dynamic swap space** (allocated as needed)

2. **Page Replacement**:

   - Works with algorithms like LRU (Least Recently Used) to decide what to swap out.

### Performance Impact:

- Swap space is much slower than RAM.
- Excessive swapping leads to **thrashing** (constant paging in/out).

---

## 🔐 **Protection and Security in Operating Systems**

These mechanisms ensure that:

- Programs **don’t interfere** with each other.
- Data is **safe** from unauthorized access.
- System resources are **used properly**.

### 🎯 **Goals of Protection**

1. **Prevent Unauthorized Access**:

   - Only authorized users/processes should access specific resources.

2. **Ensure Resource Isolation**:

   - Each process should run in isolation without affecting others.

3. **Controlled Sharing**:

   - Enable safe and controlled sharing of resources (e.g., files, memory).

4. **Fair Usage**:

   - Prevent misuse or monopolization of resources.

5. **System Integrity**:

   - Prevent one process from corrupting system data or programs.

### 🛡️ Protection Mechanisms

- **Access Control**:

  - Use of **user IDs (UIDs)** and **group IDs (GIDs)** to restrict access.
  - **Access Control Lists (ACLs)** specify who can do what (read/write/execute).

- **Memory Protection**:

  - Each process gets its own memory space.
  - Hardware (MMU) enforces limits to prevent memory violations.

- **File Protection**:

  - Permissions like `rwx` for user, group, others.

- **CPU Protection**:

  - Use of **timer interrupts** and **privileged modes** to prevent infinite loops or unauthorized hardware access.

### 🔒 Security vs. Protection

| Aspect    | Protection                      | Security                              |
| --------- | ------------------------------- | ------------------------------------- |
| **Scope** | Internal (process vs. process)  | External (user vs. system)            |
| **Focus** | Correct usage of resources      | Preventing unauthorized access        |
| **Tools** | Memory isolation, access rights | Authentication, encryption, firewalls |

### ✅ Summary

| Topic                | Key Points                                                         |
| -------------------- | ------------------------------------------------------------------ |
| **Swap-Space**       | Used as virtual memory on disk; manages page-outs when RAM is full |
| **Protection Goals** | Isolation, access control, controlled sharing, fair use, integrity |
| **Security**         | Protecting system from unauthorized users or programs              |

---

Here’s a clear overview of the **UNIX/Linux Operating System**, including an **introduction** and its **key features**:

---

## 🐧 **UNIX/Linux Operating System: Introduction**

### What is UNIX?

- UNIX is a **multiuser**, **multitasking** operating system originally developed in the 1960s and 1970s at **Bell Labs**.
- It is known for its **portability**, **modular design**, and **stability**.
- Written mostly in **C language**, which made it highly portable across different hardware.

### What is Linux?

- **Linux** is a **UNIX-like** operating system created by **Linus Torvalds** in 1991.
- It is **open-source**, meaning its source code is freely available to use, modify, and distribute.
- Popular in servers, embedded systems, desktops (like Ubuntu), and supercomputers.

### ⭐ **Features of UNIX/Linux Operating System**

| Feature                                  | Description                                                            |
| ---------------------------------------- | ---------------------------------------------------------------------- |
| **1. Multiuser Support**                 | Multiple users can access system resources concurrently.               |
| **2. Multitasking**                      | Can run many programs (processes) simultaneously.                      |
| **3. Portability**                       | Runs on various hardware platforms with minimal changes.               |
| **4. Security & Permissions**            | Uses file permissions and user authentication to secure data.          |
| **5. Hierarchical File System**          | Files organized in a tree-like directory structure.                    |
| **6. Shell & Command-Line Interface**    | Powerful shell (e.g., bash) for command execution and scripting.       |
| **7. Open Source (Linux)**               | Free to use, modify, and distribute.                                   |
| **8. Networking Capabilities**           | Built-in support for TCP/IP networking protocols.                      |
| **9. Modularity**                        | Kernel and user utilities are well-separated; supports kernel modules. |
| **10. Stability and Reliability**        | Rarely crashes; widely used in mission-critical systems.               |
| **11. Interprocess Communication (IPC)** | Supports pipes, message queues, shared memory, etc.                    |

### 🧠 Bonus: Components of a Linux System

1. **Kernel**: Core component that manages hardware, processes, memory, etc.
2. **Shell**: Command interpreter (bash, zsh, etc.).
3. **Utilities**: Small programs for tasks (e.g., `ls`, `grep`, `cp`).
4. **File System**: Ext4, XFS, etc.
5. **System Libraries**: APIs used by programs to interact with the kernel.

---

## 🧱 **Structure of UNIX/Linux Operating System**

UNIX/Linux systems have a modular structure with distinct layers:

### 1. **Kernel**

- The **core** of the operating system.
- Manages:

  - **Memory**
  - **Processes**
  - **File systems**
  - **Device I/O**
  - **System calls**

- Runs in **privileged (kernel) mode**.
- Examples: **Monolithic kernel** (Linux), **Microkernel** (Minix).

### 2. **Shell**

- Acts as an **interface** between the user and the kernel.
- It interprets user **commands** and **executes** them.
- Shells can be:

  - **Bash** (Bourne Again Shell) – most common
  - **Sh** (Bourne Shell)
  - **Csh** (C Shell)
  - **Ksh** (Korn Shell)
  - **Zsh** (Z Shell)

### 3. **Utilities and Applications**

- A collection of standard programs (e.g., `ls`, `cp`, `man`) for system operations.

### 4. **File System**

- Hierarchical directory structure.
- Root directory `/` is the top-level.

### 💡 **Basic Linux/UNIX Commands**

| Command    | Description                     |
| ---------- | ------------------------------- |
| `pwd`      | Print current working directory |
| `ls`       | List files and directories      |
| `cd`       | Change directory                |
| `mkdir`    | Make new directory              |
| `touch`    | Create an empty file            |
| `rm`       | Remove files or directories     |
| `cp`       | Copy files                      |
| `mv`       | Move/rename files               |
| `cat`      | View file contents              |
| `echo`     | Display a line of text          |
| `man`      | View manual pages               |
| `chmod`    | Change file permissions         |
| `ps`       | Display running processes       |
| `top`      | Real-time process viewer        |
| `shutdown` | Shut down system                |

### 🆘 **Accessing Help Options**

Linux provides several ways to access **help** or **manuals** for commands:

#### 1. `man` (manual pages)

- Syntax: `man <command>`
- Example: `man ls`
- Shows detailed documentation.

#### 2. `--help` option

- Syntax: `<command> --help`
- Example: `ls --help`
- Quick summary of available options.

#### 3. `info` command

- Syntax: `info <command>`
- More detailed than `man` for some commands.

#### 4. `whatis` command

- Shows a one-line description.
- Example: `whatis grep`

#### 5. `apropos` command

- Searches for a keyword in all man pages.
- Example: `apropos copy`

### ✅ Summary

| Component        | Role                                         |
| ---------------- | -------------------------------------------- |
| **Kernel**       | Core system manager (memory, CPU, I/O)       |
| **Shell**        | User interface (command interpreter)         |
| **Commands**     | Utilities for interacting with the OS        |
| **Help Options** | `man`, `--help`, `info`, `whatis`, `apropos` |

---

## 📝 **Filenames in UNIX/Linux**

### ✅ Rules for Filenames:

- Can include letters, numbers, and special characters like `_`, `-`, `.`
- **Case-sensitive**: `File.txt` ≠ `file.txt`
- Avoid using: `/` (used as directory separator), and NULL character

### ✅ Examples of valid filenames:

```
report.txt
my_folder
data123.csv
project-v1.0.sh
```

### 🌟 **Using Wildcards in UNIX/Linux**

Wildcards are **special characters** used to match patterns in filenames. Useful in commands like `ls`, `cp`, `mv`, `rm`, etc.

| Wildcard | Description                          | Example            | Matches                  |
| -------- | ------------------------------------ | ------------------ | ------------------------ |
| `*`      | Matches **zero or more** characters  | `ls *.txt`         | All `.txt` files         |
| `?`      | Matches **exactly one** character    | `ls file?.txt`     | `file1.txt`, `file2.txt` |
| `[]`     | Matches **any one** character in set | `ls file[123].txt` | `file1.txt`, `file2.txt` |
| `[a-z]`  | Matches **range** of characters      | `ls file[a-c].txt` | `filea.txt`, `fileb.txt` |
| `{}`     | Matches **alternatives**             | `ls file{1,2}.txt` | `file1.txt`, `file2.txt` |

### 📂 **Types of Files in UNIX/Linux**

Linux treats **everything as a file**, including devices and processes.

| File Type             | Description                                           | Example                   |
| --------------------- | ----------------------------------------------------- | ------------------------- |
| **Regular file**      | Text or binary data (documents, executables, scripts) | `file.txt`, `app.sh`      |
| **Directory**         | Folder containing other files or directories          | `Documents/`              |
| **Symbolic Link**     | Shortcut or reference to another file                 | `ln -s target linkname`   |
| **Character Device**  | For devices that transmit data character by character | `/dev/tty`, `/dev/random` |
| **Block Device**      | Devices that transmit data in blocks (e.g., disks)    | `/dev/sda`                |
| **FIFO (Named Pipe)** | Enables inter-process communication                   | Created using `mkfifo`    |
| **Socket**            | For network or inter-process communication via ports  | `/tmp/mysocket`           |

### ✅ Check File Type with `ls` and `file`:

#### `ls -l`

- Lists file type via the **first character**:

  - `-` : regular file
  - `d` : directory
  - `l` : symbolic link
  - `c` : character device
  - `b` : block device
  - `p` : pipe (FIFO)
  - `s` : socket

#### `file <filename>`

- Describes the content/type of the file.

### 🧠 Summary

| Concept        | Key Points                                                |
| -------------- | --------------------------------------------------------- |
| **Filenames**  | Case-sensitive, flexible naming                           |
| **Wildcards**  | Match multiple files easily using `*`, `?`, `[]`, `{}`    |
| **File Types** | Includes regular files, directories, links, devices, etc. |

---

## 🗂️ **File Systems in UNIX/Linux**

A **file system** is the way an operating system organizes and stores files on a storage device (like a hard disk or SSD). Linux supports various file systems like **ext4, XFS, Btrfs, FAT32**, etc.

### 📦 **Four Main Blocks of a File System**

A UNIX/Linux file system is divided into **four main components (blocks)**:

#### 1. **Boot Block**

- Contains the **boot loader** (used to start the OS).
- Present at the **beginning of the disk partition**.
- Executes first when the system starts.

#### 2. **Super Block**

- Contains metadata about the file system:

  - Size of the file system
  - Number of free blocks/inodes
  - Location of inode table and data blocks

- Crucial for mounting and managing the file system.

#### 3. **Inode Table**

- An **inode** (index node) stores information about each file:

  - File size
  - Owner, permissions
  - Timestamps (created, modified)
  - Data block locations (pointers)

- Each file has a unique inode.

#### 4. **Data Blocks**

- Where the **actual content** of files is stored.
- Inodes point to these blocks.
- Could be contiguous or scattered based on usage.

### 🔍 Visual Summary:

```
+-------------+----------------+------------------+----------------+
| Boot Block  | Super Block    | Inode Table      | Data Blocks    |
+-------------+----------------+------------------+----------------+
| Boot loader | FS info/meta   | File metadata    | File contents  |
```

### 📁 **UNIX/Linux Directory Hierarchy**

The file system is organized in a **hierarchical tree** structure, with the **root directory `/`** at the top.

#### 🗂️ **Top-Level Directories**:

| Directory | Description                                         |
| --------- | --------------------------------------------------- |
| `/`       | Root of the file system                             |
| `/bin`    | Essential binary executables (e.g., `ls`, `cp`)     |
| `/boot`   | Boot loader files, kernel                           |
| `/dev`    | Device files (e.g., `/dev/sda`)                     |
| `/etc`    | Configuration files                                 |
| `/home`   | Home directories for users                          |
| `/lib`    | Shared libraries for binaries in `/bin` and `/sbin` |
| `/media`  | Mount point for removable media                     |
| `/mnt`    | Temporary mount point                               |
| `/opt`    | Optional/additional software packages               |
| `/proc`   | Virtual file system for process and kernel info     |
| `/root`   | Home directory of the root user                     |
| `/sbin`   | System binaries (for admin tasks)                   |
| `/tmp`    | Temporary files                                     |
| `/usr`    | User programs and data                              |
| `/var`    | Variable data like logs, mail, spool files          |

### 🌳 Example Hierarchy View:

```
/
├── bin
├── etc
├── home
│   └── user1
├── lib
├── usr
│   ├── bin
│   └── lib
└── var
```

### ✅ Summary

| Topic              | Key Points                                                                            |
| ------------------ | ------------------------------------------------------------------------------------- |
| **Four Blocks**    | Boot block, Super block, Inode table, Data blocks                                     |
| **Inode**          | Stores file metadata and pointers to actual data                                      |
| **File Hierarchy** | Tree structure starting from `/` with standard directories like `/bin`, `/home`, etc. |

---

## **Operations & Utilities for Directories and Files**

Linux/UNIX provides many command-line utilities for managing files and directories.

### 📁 **Directory Operations:**

| Command | Description                 | Example            |
| ------- | --------------------------- | ------------------ |
| `mkdir` | Create new directory        | `mkdir new_folder` |
| `rmdir` | Remove empty directory      | `rmdir old_folder` |
| `cd`    | Change directory            | `cd /home/user`    |
| `pwd`   | Show current directory path | `pwd`              |
| `ls`    | List contents of directory  | `ls -l /etc`       |

### 📄 **File Operations:**

| Command         | Description                         | Example                  |
| --------------- | ----------------------------------- | ------------------------ |
| `touch`         | Create empty file                   | `touch file.txt`         |
| `cp`            | Copy files/directories              | `cp file1.txt file2.txt` |
| `mv`            | Move or rename files                | `mv old.txt new.txt`     |
| `rm`            | Remove/delete files                 | `rm file.txt`            |
| `cat`           | Display file content                | `cat notes.txt`          |
| `more` / `less` | Paginated viewing of large files    | `less log.txt`           |
| `find`          | Search files in directory hierarchy | `find . -name "*.txt"`   |
| `file`          | Determine file type                 | `file script.sh`         |

---

## **User & Group File Access Permissions**

In Linux, every file and directory has **three types of permissions** for **three types of users**.

### 👥 **User Types:**

- **Owner (u)**: The user who owns the file
- **Group (g)**: Users in the file's group
- **Others (o)**: All other users

### 🔑 **Permission Types:**

- **r (read)**: View contents
- **w (write)**: Modify contents
- **x (execute)**: Run file (if executable) or enter directory

### 🧱 **Permission Format (from `ls -l`)**

Example:

```bash
-rwxr-xr--  1 user group 1234 Jun 1  notes.sh
```

Breakdown:

- `-` → Regular file (could also be `d` for directory, `l` for link)
- `rwx` → Owner has read, write, execute
- `r-x` → Group has read and execute
- `r--` → Others have read only

### 🛠️ **Changing Permissions:**

#### `chmod` – change permissions

**Symbolic method**:

```bash
chmod u+x file.sh   # Add execute to user
chmod g-w file.txt  # Remove write from group
chmod o=r file.txt  # Set others to read-only
```

**Numeric method** (Octal):

- `r = 4`, `w = 2`, `x = 1`
- Example: `chmod 754 file.sh`

  - `7` (user) = 4+2+1 = rwx
  - `5` (group) = 4+0+1 = r-x
  - `4` (others) = 4+0+0 = r--

### 👥 **User and Group Management:**

| Command  | Description                           |                        |
| -------- | ------------------------------------- | ---------------------- |
| `whoami` | Show current username                 |                        |
| `groups` | Show groups user belongs to           |                        |
| `id`     | Show user ID (UID) and group ID (GID) |                        |
| `chown`  | Change file owner                     | `chown user file.txt`  |
| `chgrp`  | Change group of a file                | `chgrp staff file.txt` |

### ✅ Summary

| Topic                         | Tools/Concepts                              |
| ----------------------------- | ------------------------------------------- |
| **Directory/File Operations** | `mkdir`, `rm`, `cp`, `mv`, `ls`             |
| **Permissions**               | `r`, `w`, `x` for `user`, `group`, `others` |
| **Permission Tools**          | `chmod`, `chown`, `chgrp`, `ls -l`          |
| **User/Group Info**           | `id`, `whoami`, `groups`                    |

---

## **`Gagan Saini`**
