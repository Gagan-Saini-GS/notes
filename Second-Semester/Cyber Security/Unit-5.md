# 📘 In-Depth Notes: Network Forensics and Steganography

## 🔷 1. **Network Forensics**

Network forensics is a **branch of digital forensics** that deals with **capturing, recording, and analyzing network traffic** to detect intrusions, investigate cybercrimes, or gather evidence for legal purposes.

---

### ✅ 1.1 Network Fundamentals

#### ➤ What is a Network?

A **computer network** is a group of interconnected devices that share resources and data. In forensic terms, it’s a potential source of **evidence** (packets, IP addresses, protocols, etc.).

#### ➤ Components of a Network (Forensic Relevance)

- **Nodes**: Devices (computers, routers, etc.)
- **Transmission Media**: Physical (Ethernet) or wireless (Wi-Fi)
- **Protocols**: Rules for communication (TCP/IP, FTP, HTTP, etc.)

#### ➤ Protocol Layers (OSI Model)

Forensics often focuses on **Layer 3 (Network)** and **Layer 4 (Transport)** to inspect:

- **IP addresses**
- **TCP/UDP traffic**
- **Packets**

| **Layer**    | **Function**            | **Forensic Relevance** |
| ------------ | ----------------------- | ---------------------- |
| Physical     | Bits transmission       | Not usually analyzed   |
| Data Link    | Frames, MAC             | Some evidence possible |
| Network      | IP addressing, routing  | IP, routing data       |
| Transport    | End-to-end connection   | TCP/UDP ports          |
| Session      | Session management      | Less common            |
| Presentation | Encryption, compression | Encryption forensics   |
| Application  | User-level interactions | Email, HTTP, DNS logs  |

---

### ✅ 1.2 Types of Networks

| **Type**                            | **Scope**                    | **Forensic Insight**                       |
| ----------------------------------- | ---------------------------- | ------------------------------------------ |
| **LAN (Local Area Network)**        | Small-scale (offices, homes) | Internal data leaks, device logs           |
| **WAN (Wide Area Network)**         | Long distance, Internet      | Most public cybercrimes occur here         |
| **MAN (Metropolitan Area Network)** | City-wide networks           | Public Wi-Fi forensics                     |
| **PAN (Personal Area Network)**     | Bluetooth, mobile tethering  | Bluetooth sniffing                         |
| **WLAN (Wireless LAN)**             | Wi-Fi                        | Access point monitoring, password cracking |

---

### ✅ 1.3 Network Security Tools & Attacks

#### 🛠️ Tools Used in Network Forensics

| **Tool**      | **Purpose**                           |
| ------------- | ------------------------------------- |
| **Wireshark** | Packet sniffing and protocol analysis |
| **tcpdump**   | Command-line traffic capture          |
| **Nmap**      | Port scanning, host discovery         |
| **Snort**     | Network Intrusion Detection           |
| **NetFlow**   | Traffic flow analysis                 |
| **Xplico**    | Network forensic analysis             |

These tools help reconstruct events, trace IPs, monitor behavior, and discover the source of attacks.

#### ⚠️ Common Network Attacks

| **Attack**          | **How It Works**               | **Forensic Evidence**                 |
| ------------------- | ------------------------------ | ------------------------------------- |
| **DoS/DDoS**        | Flood server with traffic      | Packet captures showing large volumes |
| **MITM**            | Intercept communication        | Duplicate packet streams              |
| **ARP Spoofing**    | Sends fake ARP messages        | ARP tables, altered MAC-IP mappings   |
| **DNS Poisoning**   | Redirect DNS to malicious site | DNS cache inspection                  |
| **Packet Sniffing** | Capture unencrypted traffic    | Cleartext credentials, chat logs      |

---

### ✅ 1.4 Intrusion Detection Systems (IDS)

An IDS is a **monitoring system** that detects suspicious activities by analyzing network or system events.

#### 🔸 Types of IDS:

| **Type**                 | **Definition**                  | **Use Case**                          |
| ------------------------ | ------------------------------- | ------------------------------------- |
| **NIDS (Network-based)** | Monitors entire network traffic | Best for detecting widespread threats |
| **HIDS (Host-based)**    | Monitors a single machine       | Detects insider or local attacks      |

#### 🔸 Advantages:

- Real-time threat detection
- Alerts based on known patterns (signature-based) or anomalies (behavior-based)
- Central logging for analysis
- Non-invasive: doesn’t block but monitors

#### 🔸 Disadvantages:

- False positives (benign events flagged)
- False negatives (missed threats)
- Cannot stop attack (only detect)
- High data volume can overwhelm system

---

### ✅ 1.5 Forensic Importance of Network Logs

Logs are crucial in network forensics:

- **Firewall logs**: Inbound/outbound traffic
- **Web server logs**: Requests and IPs
- **Proxy logs**: Browsing history
- **IDS logs**: Alerts
- **Router logs**: Routing anomalies

These logs help **reconstruct the timeline of events** during an incident.

---

### ✅ 1.6 Chain of Custody in Network Forensics

- **Collection**: Capture live traffic or logs.
- **Preservation**: Hash the logs, timestamp, use write-once media.
- **Analysis**: Use tools like Wireshark, NetWitness.
- **Presentation**: Provide clear reports in court-compatible formats.

Maintaining **chain of custody** ensures evidence integrity and legal acceptability.

---

# 📧 2. Email Investigations – In-Depth

Email investigation is a **critical aspect of cyber forensics**, as emails are often used for communication in frauds, phishing, harassment, blackmailing, and corporate espionage.

---

### ✅ 2.1 Email Protocols

| **Protocol**                                | **Purpose**                                  | **Forensic Relevance**                                  |
| ------------------------------------------- | -------------------------------------------- | ------------------------------------------------------- |
| **SMTP (Simple Mail Transfer Protocol)**    | Used to send emails from client to server    | Can be intercepted or logged at sending stage           |
| **POP3 (Post Office Protocol 3)**           | Used to retrieve email (downloads to device) | Useful for local disk recovery                          |
| **IMAP (Internet Message Access Protocol)** | Used to access and manage email on server    | Emails stored on the server can be synced and recovered |

---

### ✅ 2.2 Email as Evidence

Emails are legally accepted as **documentary evidence**, provided they meet **admissibility standards**.

#### 🔹 Features as Evidence:

- **Sender & Receiver IDs**
- **Timestamp**
- **IP address of origin**
- **Message content and headers**
- **Attachments (can carry malware or images)**
- **Conversation threads**

#### 🔹 Legal Requirements:

- Must be **authentic**
- **Unaltered** content
- Verified through **digital signatures, logs, headers**
- Collected with proper **chain of custody**

---

### ✅ 2.3 Working of Email

1. **User composes email** using client (e.g., Gmail, Outlook).
2. The client **sends** it using **SMTP** to the mail server.
3. Server delivers it to **recipient’s server**.
4. Recipient accesses it using **POP3 or IMAP** via mail client.

---

### ✅ 2.4 Steps in Email Communication (Flowchart Style)

```plaintext
[User Client]
     ↓ SMTP
[Sender Mail Server]
     ↓ Internet Routing
[Recipient Mail Server]
     ↓ IMAP/POP3
[Recipient Client]
```

Forensics involves **tapping or analyzing logs** at any of these stages.

---

### ✅ 2.5 IP Tracking in Emails

#### 🔹 Purpose:

Track down **location of sender**, detect **spoofing**, verify **header trail**.

#### 🔹 Where is IP located?

- IPs are embedded in email headers like:

  ```
  Received: from [123.45.67.89] by mail.example.com
  ```

#### 🔹 Tool Examples:

- **Email Header Analyzer**
- **MXToolbox**
- **TraceEmail**

Caution: In Gmail and other major clients, IPs may be masked due to privacy policies.

---

### ✅ 2.6 Email Recovery Techniques

Even if deleted from inbox, emails often reside:

- In **local application files** (like Outlook’s `.PST`, `.OST`)
- In **web cache**, if accessed via browser
- In **server backups** (esp. corporate)
- In **recycle/trash folder** temporarily

#### 🔹 Tools for Email Forensics:

| **Tool**                   | **Use**                             |
| -------------------------- | ----------------------------------- |
| **MailXaminer**            | Advanced analysis of mail formats   |
| **Paraben Email Examiner** | Investigate headers and attachments |
| **Fookes Aid4Mail**        | Export and convert formats          |
| **Kernel Email Recovery**  | Recovery of corrupt mail files      |

---

## 🤖 3. Android Forensics – In-Depth

Android is the world’s most used OS and therefore a **prime target** and **evidence source** in mobile forensics.

---

### ✅ 3.1 Evolution of Android

- Originally developed by **Android Inc.**, acquired by **Google in 2005**.
- First Android version: **1.0 (2008)**
- Now evolved to versions like **Android 14**, supporting advanced security.

---

### ✅ 3.2 Android Architecture (Model)

Android is structured in layers:

1. **Linux Kernel** – Hardware drivers, security
2. **Libraries & Android Runtime (ART)** – Core libraries (SQLite, WebKit)
3. **Application Framework** – Activity manager, content providers
4. **Applications** – Pre-installed & user apps

🔹 Forensic data can exist in all layers: kernel logs, SQLite databases, app caches.

---

### ✅ 3.3 Android Security Features

| **Feature**                     | **Description**                                      |
| ------------------------------- | ---------------------------------------------------- |
| **Sandboxing**                  | Each app runs in isolated environment                |
| **Permission System**           | User grants/denies access to storage, contacts, etc. |
| **File-based Encryption (FBE)** | Encrypts different files with different keys         |
| **Google Play Protect**         | Malware scanning engine                              |
| **Verified Boot**               | Ensures OS has not been tampered with                |

**Note**: These protections may hinder forensic extraction.

---

### ✅ 3.4 Android File Hierarchy

| **Directory**                        | **Content**                             |
| ------------------------------------ | --------------------------------------- |
| `/data/data/[package-name]/`         | App private files (chat logs, settings) |
| `/sdcard/` or `/storage/emulated/0/` | User media (images, videos)             |
| `/system/`                           | OS-level apps and config                |
| `/proc/`                             | System process info                     |
| `/cache/`                            | Temporary app data                      |

---

### ✅ 3.5 Android Data Extraction Techniques

| **Method**   | **Description**                                                | **Forensic Depth**                        |
| ------------ | -------------------------------------------------------------- | ----------------------------------------- |
| **Manual**   | View info using device screen                                  | Low – only visible content                |
| **Logical**  | Use software to extract accessible data (e.g., SMS, call logs) | Medium – doesn't get deleted files        |
| **Physical** | Bit-by-bit copy of full flash memory (even deleted data)       | High – can recover deleted & hidden files |

---

### ✅ Common Android Forensic Tools

| **Tool**                       | **Function**                                       |
| ------------------------------ | -------------------------------------------------- |
| **Cellebrite UFED**            | Leading tool for full mobile extraction            |
| **Magnet AXIOM**               | Recovers data from apps, chats, encrypted areas    |
| **ADB (Android Debug Bridge)** | Command-line tool to access files, logs            |
| **Oxygen Forensic Detective**  | Supports multiple platforms, extracts deleted data |

---

# 🧰 4. Cyber Forensics Tools – In-Depth

In digital forensics, selecting the right **tools** (hardware and software) is essential to **collect, preserve, analyze, and present evidence**.

---

### ✅ 4.1 Tool Selection Criteria

Choosing a forensic tool depends on:

| **Criteria**              | **Details**                                  |
| ------------------------- | -------------------------------------------- |
| **Type of Investigation** | Network, mobile, system, email, cloud, etc.  |
| **Platform Support**      | Windows, Linux, macOS, Android, iOS          |
| **Data Types Supported**  | Emails, images, databases, logs              |
| **Legal Acceptability**   | Evidence must be admissible in court         |
| **Ease of Use**           | GUI vs CLI, automation                       |
| **Reporting**             | Ability to generate court-admissible reports |
| **Vendor Credibility**    | Recognized tools have higher legal standing  |

---

### ✅ 4.2 Hardware Tools

| **Tool**                        | **Function**                                                       |
| ------------------------------- | ------------------------------------------------------------------ |
| **Write Blocker**               | Prevents modification of the source disk during acquisition        |
| **Tableau Forensic Duplicator** | Creates forensic images from hard drives                           |
| **Faraday Bag**                 | Blocks all wireless signals to isolate mobile devices              |
| **Data Acquisition Kits**       | Portable kits with forensic laptops, storage, connectors           |
| **Forensic Workstation**        | High-performance machines with large storage and analysis software |

---

### ✅ 4.3 Software Tools

| **Tool**                   | **Purpose**                                                            | **Category**         |
| -------------------------- | ---------------------------------------------------------------------- | -------------------- |
| **FTK (Forensic Toolkit)** | Complete forensic suite for disk imaging, file carving, email recovery | General Forensics    |
| **EnCase**                 | Evidence collection, analysis, and reporting with strong legal support | Enterprise/Corporate |
| **Autopsy**                | Open-source tool for timeline analysis, keyword search, hash matching  | Free, Modular        |
| **X-Ways Forensics**       | Lightweight but powerful tool for disk-level analysis                  | Fast Performance     |
| **Wireshark**              | Network traffic capture and analysis                                   | Network Forensics    |
| **Volatility**             | Memory dump analysis                                                   | RAM Forensics        |

---

### ✅ 4.4 PKT and FKT Tools

In some academic or military forensic systems, tools are classified into:

| **Tool Type** | **Full Form**              | **Use**                                                                                 |
| ------------- | -------------------------- | --------------------------------------------------------------------------------------- |
| **PKT**       | **Primary Knowledge Tool** | Tools that offer full data acquisition, analysis, and reporting. E.g., EnCase, FTK      |
| **FKT**       | **Field Knowledge Tool**   | Lightweight tools used for preliminary or field investigations. E.g., Belkasoft, Recuva |

---

# 🎭 5. Steganography – In-Depth

**Steganography** is the art and science of **hiding messages or data** inside other non-secret data (such as images, audio, text). In forensics, steganography is both a **challenge and investigative domain**.

---

### ✅ 5.1 What is Steganography?

> Hiding data inside another file in such a way that the presence of hidden data is **not obvious**.

Unlike cryptography (which hides **content**), steganography hides the **existence** of the message itself.

---

### ✅ 5.2 Categories of Steganography in Forensics

---

#### 📄 5.2.1 **Text Steganography**

- **Technique**: Hide messages in the formatting of text, spacing, font size, invisible characters, or between white spaces.
- **Examples**:

  - Using capital letters to represent binary.
  - Zero-width characters (Unicode).

- **Forensic Tools**: Stegdetect, custom Python scripts to decode patterns.

---

#### 🖼️ 5.2.2 **Image Steganography**

- **Technique**: Embed data into image files (like `.jpg`, `.png`) using **Least Significant Bit (LSB)** insertion.
- **LSB Method**: Replaces the least significant bit of pixels with hidden data.

  - 1 pixel (RGB) = 3 bytes → 3 bits usable for hiding

- **Detection**:

  - Image artifacts when zoomed
  - File size discrepancies
  - Statistical analysis (Chi-square tests)

- **Tools**:

  - **Steghide**
  - **OpenStego**
  - **zsteg**

---

#### 🔊 5.2.3 **Audio Steganography**

- **Technique**: Embed data in audio files (.mp3, .wav) by modifying:

  - Least significant bits
  - Echo hiding
  - Spread spectrum

- **Challenges**: Audio compression (MP3) may destroy hidden data.
- **Tools**:

  - **DeepSound**
  - **MP3Stego**

- **Detection**:

  - Frequency analysis
  - File integrity comparison

---

### ✅ 5.3 Importance of Steganography in Forensics

- **Cybercriminals use it to hide data** (malware, messages, exfiltrated files).
- **Digital forensics experts** must detect and extract such hidden content.
- Used in:

  - **Terrorism investigations**
  - **Corporate espionage**
  - **Data exfiltration cases**

---

### ✅ 5.4 Anti-Steganography Techniques (Steganalysis)

| **Technique**            | **Function**                           |
| ------------------------ | -------------------------------------- |
| **Visual Inspection**    | Compare images/audio for differences   |
| **Statistical Analysis** | Histogram shifts in images             |
| **Signature Analysis**   | Search for stego tools’ file markers   |
| **Noise Detection**      | Compare signal-to-noise ratio in media |
| **AI/ML Models**         | Classify media as stego/non-stego      |

---

### 📘 **Network Forensics and Steganography – Summary Table (for Semester-End Exam)**

| **Section**                           | **Key Topics**                                                                                                               | **Highlights**                                                                                                                    |
| ------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| **Network Forensics**                 | - Network fundamentals<br>- Types of networks<br>- Network security tools and attacks                                        | Network forensics involves capturing, recording, and analyzing network events for evidence. Tools like Wireshark are widely used. |
| **Intrusion Detection Systems (IDS)** | - Host-Based IDS (HIDS)<br>- Network-Based IDS (NIDS)<br>- Pros & Cons                                                       | IDS detect malicious traffic. HIDS monitors local machines, while NIDS monitors traffic across networks.                          |
| **Email Investigations**              | - Protocols (SMTP, POP3, IMAP)<br>- Email as evidence<br>- Email header & IP tracking<br>- Recovery techniques               | Emails are primary evidence in cybercrimes. Analysts extract, analyze headers, and use tools like MailXaminer and Aid4Mail.       |
| **Android Forensics**                 | - Evolution of Android<br>- Android architecture & file hierarchy<br>- Security features<br>- Data extraction techniques     | Forensics includes manual, logical, and physical extraction. Tools include ADB, Cellebrite, Oxygen.                               |
| **Cyber Forensic Tools**              | - Tool selection<br>- Hardware tools (write blocker, Faraday bag)<br>- Software tools (FTK, EnCase, Autopsy)<br>- PKT vs FKT | Hardware ensures integrity; software performs acquisition and analysis. Tools are chosen based on case type and admissibility.    |
| **Steganography**                     | - Text, image, audio steganography<br>- Tools (Steghide, DeepSound)<br>- LSB insertion<br>- Steganalysis techniques          | Used by criminals to hide data. Analysts detect and extract hidden content using specialized tools and statistical methods.       |

---
