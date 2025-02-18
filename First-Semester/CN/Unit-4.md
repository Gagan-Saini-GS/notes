# Unit-4

## **The Network Layer: Design Issues & Routing**

The **Network Layer (Layer 3)** of the OSI model is responsible for packet forwarding, addressing, and routing across different networks. It ensures that data is transmitted efficiently from the source to the destination, even across multiple interconnected networks.

---

## **Design Issues in the Network Layer**

When designing the Network Layer, several key issues need to be addressed:

### **1. Store-and-Forward Packet Switching**

- Data is transmitted in small units called **packets**.
- Each packet is received, stored, and then forwarded to the next node.
- This ensures error checking and prevents data loss but adds some delay.

### **2 Services Provided to the Transport Layer**

The Network Layer provides different types of services to the Transport Layer:

1. **Connectionless Service (Datagram Approach)**
   - Each packet is treated independently and can take different paths.
   - Example: **IP (Internet Protocol)** follows this approach.
2. **Connection-Oriented Service (Virtual Circuit Approach)**
   - A dedicated path is established before data transmission.
   - Example: **MPLS (Multiprotocol Label Switching)**.

### **3 Addressing**

- The Network Layer assigns **logical addresses (IP addresses)** to devices.
- Ensures unique identification and enables routing across networks.

### **4 Packet Fragmentation and Reassembly**

- If a packet is too large for a network, it must be fragmented into smaller packets.
- The receiving end reassembles these fragments to reconstruct the original data.

### **5 Error Handling and Quality of Service (QoS)**

- The Network Layer must detect lost, duplicated, or corrupted packets.
- QoS mechanisms prioritize critical traffic, ensuring reliable communication for applications like VoIP and video conferencing.

---

## **Routing in the Network Layer**

Routing is the process of determining the best path for data packets to travel across networks. The Network Layer handles **packet forwarding and route determination** using various **routing algorithms**.

### **1 Types of Routing**

Routing can be classified into the following types:

#### **a. Static Routing (Fixed Routing)**

- The routing path is **manually configured** by the network administrator.
- Does not adapt to network changes.
- Suitable for **small and stable networks**.
- Example: Manually configuring a router using a **static routing table**.

#### **b. Dynamic Routing**

- The router **automatically updates** routing tables based on network conditions.
- Uses **routing protocols** to exchange information with other routers.
- Adapts to network failures and topology changes.
- Examples: **RIP (Routing Information Protocol), OSPF (Open Shortest Path First), BGP (Border Gateway Protocol)**.

#### **c. Flooding**

- Every incoming packet is forwarded to **all outgoing links** except the one it came from.
- Simple but inefficient (causes network congestion).
- Used in situations where the best path is unknown.

#### **d. Adaptive Routing**

- Adjusts routes based on real-time network traffic, failures, or congestion.
- Uses algorithms to select the best path dynamically.
- Example: OSPF, which selects routes based on link costs and bandwidth.

### **2 Routing Algorithms**

There are different types of routing algorithms used for determining the best path:

#### **a. Distance Vector Routing**

- Each router maintains a table (vector) of the shortest distance to all network destinations.
- Periodically exchanges updates with neighboring routers.
- **Example:** **RIP (Routing Information Protocol)**
- **Limitation:** Slow convergence (can take time to adapt to failures).

#### **b. Link State Routing**

- Each router maintains a complete map (topology) of the network.
- Updates are sent only when network changes occur, reducing unnecessary traffic.
- **Example:** **OSPF (Open Shortest Path First)**
- **Advantage:** Faster convergence and more efficient than distance vector routing.

#### **c. Hierarchical Routing**

- Large networks are divided into hierarchical regions to reduce routing table size.
- Routers only keep track of paths within their region, reducing overhead.

#### **d. Hybrid Routing**

- Combines both **distance vector** and **link-state** methods.
- Example: **EIGRP (Enhanced Interior Gateway Routing Protocol)**, used in Cisco networks.

### **3 Routing Protocols**

Different routing protocols are used depending on the network scale:

| **Routing Protocol**                               | **Type**        | **Use Case**                                          |
| -------------------------------------------------- | --------------- | ----------------------------------------------------- |
| RIP (Routing Information Protocol)                 | Distance Vector | Small networks, simple but slow convergence           |
| OSPF (Open Shortest Path First)                    | Link State      | Large enterprise networks, fast convergence           |
| BGP (Border Gateway Protocol)                      | Path Vector     | Internet backbone, used by ISPs                       |
| EIGRP (Enhanced Interior Gateway Routing Protocol) | Hybrid          | Cisco networks, combines distance vector & link state |

### **Summary**

1. **Design Issues in Network Layer**
   - Store-and-forward switching, addressing, fragmentation, QoS, and error handling.
2. **Routing Mechanisms**
   - **Static vs. Dynamic Routing, Adaptive Routing, and Flooding.**
3. **Routing Algorithms**
   - **Distance Vector (RIP), Link State (OSPF), Hierarchical, and Hybrid (EIGRP).**
4. **Routing Protocols**
   - **RIP, OSPF, BGP, and EIGRP, used for different types of networks.**

---

## **Routing Algorithms: Link State, Distance Vector, and Flooding**

Routing algorithms determine the best path for data packets in a network. The three primary routing algorithms are:

1. **Link State Routing** (Efficient and scalable)
2. **Distance Vector Routing** (Simple but slow)
3. **Flooding** (Reliable but inefficient)

### **1. Link State Routing**

**Concept:**  
Each router maintains a complete **topology map** of the network and calculates the shortest path using **Dijkstra’s Algorithm**.

#### **How It Works:**

1. **Each router discovers its neighbors** by sending HELLO packets.
2. **Routers measure the link cost (e.g., bandwidth, delay, congestion).**
3. **Each router floods its link-state information** to all routers in the network.
4. **Every router constructs a topology map** based on received updates.
5. **Each router computes the shortest path** to all destinations using **Dijkstra's Algorithm**.

#### **Advantages:**

✅ Faster convergence (quickly adapts to failures).  
✅ Less bandwidth usage (updates sent only on changes).  
✅ More accurate path selection (based on real-time network state).

#### **Disadvantages:**

❌ Requires more memory (stores full network topology).  
❌ Higher processing power needed to compute routes.

#### **Example Routing Protocols:**

- **OSPF (Open Shortest Path First)** – Used in large enterprise networks.
- **IS-IS (Intermediate System to Intermediate System)** – Used in ISPs and backbone networks.

### **2. Distance Vector Routing**

**Concept:**  
Each router maintains a **routing table** that stores distances (hop counts) to all destinations. Routers exchange their routing tables periodically with neighbors.

#### **How It Works:**

1. **Each router starts with knowledge of directly connected neighbors.**
2. **Routers exchange routing tables** with their neighbors at regular intervals.
3. **Routers update their tables** based on received information (Bellman-Ford Algorithm).
4. **The process repeats until all routers have the shortest paths.**

#### **Advantages:**

✅ Simple and easy to implement.  
✅ Low processing power and memory usage.

#### **Disadvantages:**

❌ Slow convergence (takes time to detect failures).  
❌ Prone to **routing loops** (solutions like Split Horizon and Poison Reverse help).  
❌ Bandwidth-intensive (updates sent periodically).

#### **Example Routing Protocols:**

- **RIP (Routing Information Protocol)** – Used in small networks.
- **EIGRP (Enhanced Interior Gateway Routing Protocol)** – Cisco’s improved version, faster than RIP.

### **3. Flooding**

**Concept:**  
Every incoming packet is **sent to all outgoing links**, except the one it came from. No routing tables are needed.

#### **How It Works:**

1. When a router receives a packet, it sends copies of the packet to all neighbors.
2. This process continues until packets reach their destination.
3. To prevent **infinite looping**, mechanisms like **Time-to-Live (TTL)** and **Sequence Numbers** are used.

#### **Advantages:**

✅ Highly reliable (packets reach all possible paths).  
✅ Simple (does not require routing tables).

#### **Disadvantages:**

❌ **Redundant traffic** (network congestion).  
❌ **Inefficient** (wastes bandwidth).  
❌ **Looping issues** (mitigated using TTL).

#### **Use Cases:**

- Used in **network discovery** (e.g., ARP Request in Ethernet).
- Used in **broadcast and multicast networks**.

### **Comparison Table**

| **Routing Algorithm**       | **Efficiency** | **Convergence Time** | **Memory Usage** | **Loop Prevention**                                   | **Use Cases**                  |
| --------------------------- | -------------- | -------------------- | ---------------- | ----------------------------------------------------- | ------------------------------ |
| **Link State Routing**      | High           | Fast                 | High             | No loops                                              | Large networks (OSPF, IS-IS)   |
| **Distance Vector Routing** | Moderate       | Slow                 | Low              | Needs loop prevention (Split Horizon, Poison Reverse) | Small networks (RIP, EIGRP)    |
| **Flooding**                | Low            | Instant              | None             | Uses TTL or Sequence Numbers                          | Discovery & multicast networks |

---

## **Routing Protocols: RIP, IGRP, EIGRP, OSPF**

Routing protocols enable routers to dynamically determine the best path for data packets across a network. They can be classified into:

- **Distance Vector Protocols** (RIP, IGRP, EIGRP)
- **Link State Protocols** (OSPF)

### **1. RIP (Routing Information Protocol)**

- **Type:** Distance Vector
- **Metric:** Hop Count (Max: 15 hops)
- **Algorithm:** Bellman-Ford
- **Administrative Distance (AD):** 120
- **Updates:** Every 30 seconds (causes high bandwidth usage)
- **Loop Prevention:** Split Horizon, Poison Reverse

#### **Advantages:**

✅ Simple and easy to configure  
✅ Works well in **small networks**

#### **Disadvantages:**

❌ **Slow convergence** (takes time to update routes)  
❌ **Limited scalability** (max 15 hops)  
❌ **High bandwidth usage** (frequent updates)

#### **Variants:**

- **RIPv1:** Classful (no subnet masks)
- **RIPv2:** Classless (supports subnet masks, authentication)

#### **Use Case:**

- Small office/home office (SOHO) networks

### **2. IGRP (Interior Gateway Routing Protocol)**

- **Type:** Distance Vector
- **Metric:** Composite (Bandwidth, Delay, Load, Reliability)
- **Algorithm:** Bellman-Ford
- **Administrative Distance (AD):** 100
- **Updates:** Every 90 seconds
- **Loop Prevention:** Hold-down timers, Split Horizon

#### **Advantages:**

✅ Supports larger networks than RIP (max 255 hops)  
✅ Uses multiple metrics for better routing decisions

#### **Disadvantages:**

❌ **Cisco proprietary** (works only on Cisco devices)  
❌ **Higher convergence time than modern protocols**

#### **Use Case:**

- Older Cisco networks (deprecated, replaced by EIGRP)

### **3. EIGRP (Enhanced Interior Gateway Routing Protocol)**

- **Type:** Hybrid (Distance Vector + Link State)
- **Metric:** Composite (Bandwidth, Delay)
- **Algorithm:** DUAL (Diffusing Update Algorithm)
- **Administrative Distance (AD):** 90 (internal), 170 (external)
- **Updates:** Partial updates (only when changes occur)
- **Loop Prevention:** Feasible successor mechanism

#### **Advantages:**

✅ **Fast convergence** (DUAL algorithm quickly recalculates routes)  
✅ **Less bandwidth usage** (only sends updates when needed)  
✅ **Supports load balancing** (equal & unequal cost paths)

#### **Disadvantages:**

❌ **Cisco proprietary** (not available on all routers)  
❌ **More complex configuration than RIP**

#### **Use Case:**

- Medium to large enterprise networks (especially Cisco environments)

### **4. OSPF (Open Shortest Path First)**

- **Type:** Link State
- **Metric:** Cost (Based on bandwidth)
- **Algorithm:** Dijkstra’s Algorithm
- **Administrative Distance (AD):** 110
- **Updates:** Only when network topology changes
- **Loop Prevention:** Hierarchical design with Areas

#### **Advantages:**

✅ **Fast convergence** (reacts quickly to failures)  
✅ **Efficient bandwidth usage** (no periodic updates)  
✅ **Scalable** (supports large networks with multiple areas)  
✅ **Uses authentication for security**

#### **Disadvantages:**

❌ **Higher CPU and memory usage**  
❌ **More complex to configure than RIP/EIGRP**

#### **Use Case:**

- Large enterprise networks and ISPs

### **Comparison Table**

| **Protocol** | **Type**        | **Algorithm** | **Metric**                          | **Admin Distance**            | **Max Hops** | **Best for**                |
| ------------ | --------------- | ------------- | ----------------------------------- | ----------------------------- | ------------ | --------------------------- |
| **RIP**      | Distance Vector | Bellman-Ford  | Hop Count                           | 120                           | 15           | Small networks              |
| **IGRP**     | Distance Vector | Bellman-Ford  | Bandwidth, Delay, Load, Reliability | 100                           | 255          | Legacy Cisco networks       |
| **EIGRP**    | Hybrid          | DUAL          | Bandwidth, Delay                    | 90 (internal), 170 (external) | 255          | Medium-Large Cisco networks |
| **OSPF**     | Link State      | Dijkstra      | Cost (Bandwidth)                    | 110                           | Unlimited    | Large networks, ISPs        |

---

## **Internetworking: Tunneling, Fragmentation, IPv4, IPv6, and BGP**

Internetworking refers to connecting different types of networks, ensuring seamless communication between them. Key concepts include **Tunneling, Fragmentation, IPv4, IPv6, and BGP.**

### **1. Tunneling**

**Concept:**  
Tunneling is a technique used to **encapsulate one network protocol within another** to transport data securely across different networks.

#### **How It Works:**

1. **Encapsulation:** The original packet is wrapped inside another packet with a different protocol header.
2. **Transmission:** The encapsulated packet travels through an intermediate network.
3. **Decapsulation:** At the destination, the outer header is removed, restoring the original packet.

#### **Types of Tunneling:**

- **GRE (Generic Routing Encapsulation):** Supports multiple protocols but lacks encryption.
- **IPsec Tunnel Mode:** Provides encryption and security for secure VPNs.
- **MPLS Tunneling:** Used in service provider networks for traffic engineering.
- **6to4 & Teredo:** IPv6 tunneling over IPv4 networks.

#### **Use Cases:**

✅ VPNs (Virtual Private Networks) for secure remote access.  
✅ IPv6 migration over IPv4 networks.  
✅ Secure communication between different network architectures.

### **2. Fragmentation**

**Concept:**  
Fragmentation occurs when a large packet is broken into smaller pieces to fit within the **Maximum Transmission Unit (MTU)** of the network.

#### **How It Works:**

1. **Sender breaks a large packet** into smaller fragments.
2. **Each fragment has its own header** and is transmitted separately.
3. **Receiver reassembles** fragments into the original packet.

#### **Issues with Fragmentation:**

❌ **Increases latency** (reassembly at the receiver).  
❌ **Consumes processing power** (fragments need to be tracked).  
❌ **Risk of packet loss** (losing one fragment requires retransmission).

#### **IPv4 vs. IPv6 Fragmentation:**

| **Feature**      | **IPv4**                     | **IPv6**                                                   |
| ---------------- | ---------------------------- | ---------------------------------------------------------- |
| Where it happens | At routers or sender         | Only at sender                                             |
| Header field     | Fragment Offset              | Extension Header                                           |
| Impact           | Routers handle fragmentation | End devices handle fragmentation, reducing router workload |

#### **Avoiding Fragmentation:**

- **Path MTU Discovery (PMTUD):** Detects the smallest MTU along a path and adjusts packet size.
- **TCP MSS (Maximum Segment Size) Adjustment:** Ensures TCP packets fit within the MTU.

### **3. IPv4 Basics**

IPv4 (Internet Protocol version 4) is the **most widely used** protocol for addressing and routing data on networks.

#### **Features:**

- **32-bit address space** (e.g., `192.168.1.1`).
- **Supports 4.3 billion addresses** (limited, causing IPv6 adoption).
- **Address classes:** A, B, C, D (Multicast), E (Reserved).
- **Subnetting:** Divides a large network into smaller subnetworks.
- **NAT (Network Address Translation):** Conserves IPv4 addresses by mapping private to public IPs.

#### **Limitations:**

❌ **Limited address space** (IPv4 exhaustion).  
❌ **No built-in security** (IPsec is optional).  
❌ **Fragmentation overhead** affects performance.

### **4. IPv6 Basics**

IPv6 (Internet Protocol version 6) is the next-generation IP addressing system designed to overcome IPv4’s limitations.

#### **Features:**

✅ **128-bit address space** (Supports 340 undecillion addresses).  
✅ **Simplified header** (Improves performance).  
✅ **No need for NAT** (Each device gets a unique global IP).  
✅ **Built-in security** (IPsec is mandatory).  
✅ **Better support for mobile devices and IoT**.

#### **IPv6 Address Format:**

- **Example:** `2001:0db8:85a3:0000:0000:8a2e:0370:7334`
- **Shortened Format:** `2001:db8:85a3::8a2e:370:7334`

### **Key Differences Between IPv4 and IPv6:**

| **Feature**       | **IPv4**            | **IPv6**                 |
| ----------------- | ------------------- | ------------------------ |
| Address Size      | 32-bit              | 128-bit                  |
| Address Example   | `192.168.1.1`       | `2001:db8::ff00:42:8329` |
| Address Count     | ~4.3 billion        | 340 undecillion          |
| NAT Required?     | Yes                 | No                       |
| Security          | Optional (IPsec)    | Mandatory (IPsec)        |
| Header Size       | Complex             | Simplified               |
| Broadcast Support | Yes                 | No (Uses Multicast)      |
| Fragmentation     | By routers & sender | Only by sender           |

#### **Migration Techniques:**

- **Dual Stack:** Devices support both IPv4 & IPv6.
- **Tunneling (6to4, Teredo, ISATAP):** IPv6 packets are sent over IPv4 networks.
- **Translation (NAT64):** IPv6-only networks communicate with IPv4 hosts.

### **5. BGP (Border Gateway Protocol)**

BGP is the **backbone of the Internet**, enabling ISPs and large networks to exchange routing information.

#### **Features:**

- **Type:** Path Vector Routing Protocol.
- **Metric:** Path attributes (AS Path, Next Hop, MED, Local Preference).
- **Updates:** Only when network topology changes.
- **Loop Prevention:** AS Path (Tracks the route to avoid loops).

#### **Types of BGP:**

1. **eBGP (External BGP)** – Used between different ASes (Autonomous Systems).
2. **iBGP (Internal BGP)** – Used within an AS for better routing control.

#### **How BGP Works:**

1. Routers **establish a connection** (TCP Port 179).
2. **Exchange routing updates** (Only changes, not full tables).
3. **Select the best path** based on BGP attributes.
4. **Propagate routes** to other BGP peers.

#### **BGP Attributes (Used for Path Selection):**

- **AS Path:** Shortest path is preferred.
- **Next Hop:** Defines the next router for packet forwarding.
- **Local Preference:** Higher value is preferred within an AS.
- **Multi-Exit Discriminator (MED):** Helps determine the best exit path.

#### **Advantages of BGP:**

✅ **Scalable** – Handles large networks (e.g., ISPs, global enterprises).  
✅ **Policy-Based Routing** – Routes can be controlled based on policies.  
✅ **Reliable & Stable** – Minimizes unnecessary updates.

#### **Disadvantages of BGP:**

❌ **Complex to configure** (Requires expertise).  
❌ **Slow convergence** (Takes time to adapt to changes).  
❌ **Security concerns** (BGP hijacking can disrupt Internet traffic).

#### **Use Cases:**

- **Internet routing (ISPs & cloud providers)**.
- **Multi-homing (enterprises using multiple ISPs for redundancy)**.
- **Traffic engineering (optimizing network paths)**.

### **Summary Table**

| **Feature**              | **Tunneling**                      | **Fragmentation**                        | **IPv4**            | **IPv6**              | **BGP**               |
| ------------------------ | ---------------------------------- | ---------------------------------------- | ------------------- | --------------------- | --------------------- |
| **Purpose**              | Encapsulation for secure transport | Breaking large packets into smaller ones | 32-bit addressing   | 128-bit addressing    | Internet routing      |
| **Key Issue**            | Protocol mismatch, security        | Overhead, latency                        | Address exhaustion  | Migration challenges  | Slow convergence      |
| **Example Technologies** | VPNs, IPsec, MPLS                  | Path MTU Discovery                       | NAT, Subnetting     | Dual Stack, Tunneling | eBGP, iBGP            |
| **Who Uses It?**         | Enterprises, ISPs                  | All IP networks                          | Most networks today | Future networks, IoT  | ISPs, cloud providers |

---

## **Transport Layer Protocols: UDP, TCP, and Their Headers**

The **Transport Layer (Layer 4)** in the OSI model ensures end-to-end communication between applications running on different devices. The two primary transport layer protocols are:

1. **UDP (User Datagram Protocol)** – Fast but unreliable
2. **TCP (Transmission Control Protocol)** – Reliable but slower

### **1. UDP (User Datagram Protocol)**

#### **Concept:**

UDP is a **connectionless, lightweight** transport protocol used for fast data transmission. It does not establish a connection before sending data, nor does it guarantee delivery or error correction.

#### **Key Features:**

✅ **Low overhead** – No connection setup, acknowledgments, or retransmissions  
✅ **Fast transmission** – Ideal for real-time applications  
✅ **No congestion control** – Suitable for streaming and gaming  
✅ **Packet-based communication** – Each message is sent independently

#### **When to Use UDP?**

- **Live streaming** (YouTube Live, Twitch)
- **Online gaming** (Fast but occasional packet loss is acceptable)
- **VoIP (Voice over IP)** (Low latency is critical)
- **DNS (Domain Name System)** (Quick queries, no need for reliability)

#### **UDP Header Format (8 bytes total)**

| **Field**            | **Size (Bytes)** | **Description**                                                |
| -------------------- | ---------------- | -------------------------------------------------------------- |
| **Source Port**      | 2                | Identifies the sender's port number                            |
| **Destination Port** | 2                | Identifies the receiver's port number                          |
| **Length**           | 2                | Total length of the UDP packet (header + data)                 |
| **Checksum**         | 2                | Used for error detection (optional in IPv4, mandatory in IPv6) |

**Example UDP Header (Hex Representation):**

```
4500 003C 1C46 4000 4011 A6EC C0A8 0001
C0A8 0002 0035 0035 0028 FFFF
```

- **0035** = Source port (53 for DNS)
- **0035** = Destination port (53 for DNS)
- **0028** = Length (40 bytes)
- **FFFF** = Checksum

### **2. TCP (Transmission Control Protocol)**

#### **Concept:**

TCP is a **connection-oriented, reliable** transport protocol that ensures complete data delivery in the correct order. It provides **error checking, retransmissions, and flow control** to guarantee data integrity.

#### **Key Features:**

✅ **Reliable** – Uses acknowledgments (ACK) and retransmissions  
✅ **Ordered** – Packets arrive in sequence (stream-based communication)  
✅ **Error-checked** – Detects and corrects corrupted data  
✅ **Flow control** – Prevents sender from overwhelming the receiver  
✅ **Congestion control** – Avoids network congestion

#### **When to Use TCP?**

- **Web browsing (HTTP/HTTPS)** – Reliable page loading
- **Email (SMTP, IMAP, POP3)** – Ensures complete message delivery
- **File transfers (FTP, SFTP)** – Guarantees data integrity
- **Bank transactions** – Accuracy and security are critical

#### **TCP Header Format (20-60 bytes total)**

| **Field**                 | **Size (Bytes)** | **Description**                            |
| ------------------------- | ---------------- | ------------------------------------------ |
| **Source Port**           | 2                | Identifies sender’s port                   |
| **Destination Port**      | 2                | Identifies receiver’s port                 |
| **Sequence Number**       | 4                | Tracks packet order                        |
| **Acknowledgment Number** | 4                | Confirms receipt of data                   |
| **Header Length**         | 4 bits           | Specifies TCP header size                  |
| **Flags (Control Bits)**  | 6 bits           | SYN, ACK, FIN, RST, PSH, URG               |
| **Window Size**           | 2                | Controls flow of data                      |
| **Checksum**              | 2                | Error detection                            |
| **Urgent Pointer**        | 2                | Indicates priority data                    |
| **Options**               | 0-40             | Used for extra features (e.g., timestamps) |

**Key TCP Flags:**

- **SYN (Synchronize)** – Starts connection
- **ACK (Acknowledgment)** – Confirms received data
- **FIN (Finish)** – Ends connection
- **RST (Reset)** – Resets connection
- **PSH (Push)** – Sends data immediately
- **URG (Urgent)** – Marks priority data

### **3. TCP vs. UDP: Key Differences**

| **Feature**         | **TCP**                                          | **UDP**                                 |
| ------------------- | ------------------------------------------------ | --------------------------------------- |
| **Connection Type** | Connection-oriented                              | Connectionless                          |
| **Reliability**     | Reliable (Acknowledgments, retransmissions)      | Unreliable (No ACK, no retransmissions) |
| **Ordering**        | Ensures packets arrive in order                  | No guarantee of order                   |
| **Error Checking**  | Yes (Checksum, retransmissions)                  | Yes (Checksum, but no retransmissions)  |
| **Speed**           | Slower (Overhead for reliability)                | Faster (No error correction)            |
| **Use Cases**       | Web browsing, file transfer, email, transactions | Streaming, VoIP, gaming, DNS            |

### **4. TCP Connection Process (Three-Way Handshake)**

Before sending data, TCP establishes a connection using a **three-way handshake**:

1. **SYN:** Client → Server (`SYN` flag set)
2. **SYN-ACK:** Server → Client (`SYN + ACK` flags set)
3. **ACK:** Client → Server (`ACK` flag set)

**Example:**

```
Client:  SYN →  Server
Server: SYN-ACK → Client
Client:  ACK → Server (Connection Established)
```

#### **TCP Connection Termination (Four-Way Handshake)**

1. **FIN:** Client → Server (Request to close)
2. **ACK:** Server → Client (Acknowledges)
3. **FIN:** Server → Client (Request to close)
4. **ACK:** Client → Server (Acknowledges and closes)

### **5. UDP vs. TCP Use Cases**

| **Use Case**                                        | **Recommended Protocol** |
| --------------------------------------------------- | ------------------------ |
| **Web browsing (HTTP/HTTPS)**                       | TCP                      |
| **File transfers (FTP, SFTP, SMB)**                 | TCP                      |
| **Email (SMTP, IMAP, POP3)**                        | TCP                      |
| **DNS queries**                                     | UDP                      |
| **Online gaming**                                   | UDP                      |
| **Live video streaming (YouTube, Twitch, Netflix)** | UDP                      |
| **VoIP calls (Skype, WhatsApp calls)**              | UDP                      |

### **Summary**

1. **UDP** is **fast but unreliable**, used for real-time applications.
2. **TCP** is **reliable but slower**, used for accurate data transfer.
3. **TCP uses acknowledgments, retransmissions, and flow control** to ensure data delivery.
4. **UDP sends packets without ensuring delivery**, making it ideal for **speed-sensitive** applications.
5. **TCP uses a Three-Way Handshake** for connection establishment and a **Four-Way Handshake** for termination.

---

## **`Gagan Saini`**
