# Unit-3

## **The Medium Access Sub-Layer & Multiple Access Protocols**

The **Medium Access Control (MAC) sub-layer** is part of the **Data Link Layer (Layer 2)** in the OSI model. It is responsible for **coordinating access to the shared communication medium** and ensuring that multiple devices can transmit data efficiently **without collisions or interference**.

When multiple devices share the same communication medium (such as a **Wi-Fi network, Ethernet, or satellite link**), a method is needed to **regulate access** to avoid data collisions. This is where **Multiple Access Protocols** come into play.

### **Multiple Access Protocols**

Multiple Access Protocols are techniques that allow multiple devices to share the same communication channel **efficiently**. These protocols can be classified into the following categories:

1. **Random Access Protocols (Contention-Based)**

   - ALOHA
   - CSMA (Carrier Sense Multiple Access)

2. **Controlled Access Protocols**

   - Reservation
   - Polling
   - Token Passing

3. **Channelization Protocols (Scheduled Access)**
   - FDMA (Frequency Division Multiple Access)
   - TDMA (Time Division Multiple Access)
   - CDMA (Code Division Multiple Access)

We will focus on **ALOHA and CSMA**, which fall under **Random Access Protocols**.

### **1. ALOHA Protocol**

ALOHA is one of the simplest **random access** protocols developed for **wireless communication**. It was initially designed for **satellite networks** but is also used in **wireless LANs (Wi-Fi)**.

#### **Types of ALOHA**

##### **1.1 Pure ALOHA**

- Any device **can transmit data at any time**.
- If a collision occurs, the device waits for a **random time** before retransmitting.
- **Very inefficient** because collisions are frequent.

##### **Efficiency of Pure ALOHA:**

- The maximum efficiency is **18.4%** (only 18.4% of the time is used for successful transmission).

#### **1.2 Slotted ALOHA**

- Time is divided into **fixed slots**.
- Devices can **only transmit at the beginning of a slot**.
- **Reduces collisions** compared to Pure ALOHA.

##### **Efficiency of Slotted ALOHA:**

- The maximum efficiency is **36.8%** (twice that of Pure ALOHA).

### **Comparison: Pure ALOHA vs. Slotted ALOHA**

| Feature         | Pure ALOHA   | Slotted ALOHA |
| --------------- | ------------ | ------------- |
| Time Slots      | No           | Yes           |
| Collision Risk  | High         | Lower         |
| Efficiency      | 18.4%        | 36.8%         |
| Synchronization | Not Required | Required      |

### **2. CSMA (Carrier Sense Multiple Access)**

CSMA improves on ALOHA by **listening to the channel** before transmitting. If the channel is **busy**, the device waits before sending data, reducing the chance of collisions.

#### **Types of CSMA:**

##### **2.1 Persistent CSMA**

- A device **continuously senses** the channel.
- If the channel is **idle**, it transmits immediately.
- If the channel is **busy**, it keeps sensing until it becomes idle, then transmits.
- **Higher collision risk** if multiple devices wait and transmit at the same time.

##### **2.2 Non-Persistent CSMA**

- A device **checks the channel** before transmitting.
- If the channel is **busy**, it waits for a **random amount of time** before sensing again.
- **Fewer collisions** but **higher waiting time**.

##### **2.3 p-Persistent CSMA (for Slotted Channels)**

- Used in **time-slotted networks**.
- If the channel is **idle**, the device transmits with a probability **p**.
- If the channel is **busy**, it waits for the next time slot.

### **CSMA with Collision Detection (CSMA/CD) – Used in Ethernet**

- If a device **detects a collision while transmitting**, it **stops sending data** immediately.
- The device then waits for a **random time** before retransmitting.
- **Used in Ethernet (Wired LANs).**

### **CSMA with Collision Avoidance (CSMA/CA) – Used in Wi-Fi (802.11)**

- Unlike CSMA/CD, which **detects collisions**, CSMA/CA **tries to prevent collisions before they happen**.
- Devices use **RTS (Request to Send) and CTS (Clear to Send)** signals before transmission.
- **Used in Wireless Networks (Wi-Fi).**

### **Comparison of ALOHA and CSMA**

| Feature         | ALOHA               | CSMA            |
| --------------- | ------------------- | --------------- |
| Channel Sensing | No                  | Yes             |
| Collision Rate  | High                | Lower           |
| Efficiency      | Low (18.4-36.8%)    | Higher (>50%)   |
| Used In         | Wireless, satellite | Ethernet, Wi-Fi |

### **Key Takeaways**

✅ **ALOHA** is a simple protocol but has **high collision probability**.  
✅ **Slotted ALOHA** improves efficiency by allowing transmission only at fixed time slots.  
✅ **CSMA** reduces collisions by listening to the channel before transmitting.  
✅ **CSMA/CD** (Ethernet) **detects collisions** and retransmits after a random time.  
✅ **CSMA/CA** (Wi-Fi) **avoids collisions** using RTS/CTS signals.

---

## Ethernet

Ethernet has evolved over time to support higher speeds and more efficient network communication. Here’s an overview of some key Ethernet technologies:

### **Switched Ethernet**

- Uses network switches instead of hubs, reducing collisions and improving efficiency.
- Each device gets a dedicated bandwidth instead of sharing it with all devices.
- Operates in full-duplex mode, allowing simultaneous data transmission and reception.

### **Fast Ethernet (100 Mbps - IEEE 802.3u)**

- Introduced to improve speed from the original 10 Mbps Ethernet.
- Uses Cat5 or higher cables for transmission.
- Includes standards like **100BASE-TX (twisted pair), 100BASE-FX (fiber optic)**, etc.

### **Gigabit Ethernet (1 Gbps - IEEE 802.3z & 802.3ab)**

- A significant speed upgrade to support high-bandwidth applications.
- Uses both fiber optic and twisted pair cables (**1000BASE-T, 1000BASE-SX, 1000BASE-LX**).
- Commonly used in modern networks, including home, enterprise, and data centers.

---

## **DLL Switching and Internetworking Devices**

The **Data Link Layer (DLL)** plays a crucial role in switching and internetworking by ensuring efficient communication between devices within and across networks. Various networking devices operate at this layer and higher layers to facilitate data transmission. Let’s go through them in detail:

### **1. Internetworking**

Internetworking refers to the process of connecting multiple networks to function as a single unified system. It allows communication between different types of networks, whether they use similar or different technologies. Internetworking is achieved using devices like **repeaters, hubs, bridges, switches, routers, gateways, and VLANs**.

### **2. Repeaters**

- **Layer:** Operates at **Physical Layer (Layer 1)**.
- **Function:** Amplifies and regenerates weak or distorted signals to extend the reach of a network.
- **Use Case:** Used in long-distance communication to overcome signal degradation over large distances.
- **Example:** Used in fiber optic and Ethernet networks to boost signals.

### **3. Hubs**

- **Layer:** Operates at **Physical Layer (Layer 1)**.
- **Function:** A hub is a basic networking device that broadcasts incoming data to all connected devices, without filtering or directing traffic.
- **Types of Hubs:**
  - **Active Hub:** Regenerates and boosts the signal.
  - **Passive Hub:** Just forwards the signal without amplification.
  - **Intelligent Hub:** Can monitor traffic and manage network performance.
- **Limitation:** Since it sends data to all devices, it increases network congestion and collisions.

### **4. Bridges**

- **Layer:** Operates at **Data Link Layer (Layer 2)**.
- **Function:** Connects two or more LAN segments and filters traffic based on MAC addresses.
- **Features:**
  - Reduces network collisions by segmenting traffic.
  - Learns MAC addresses and forwards frames intelligently.
- **Use Case:** Used to divide a large network into smaller, more manageable sections.

### **5. Switches**

- **Layer:** Operates at **Data Link Layer (Layer 2)**, but some work at Layer 3 (multilayer switches).
- **Function:** A switch is an advanced version of a bridge that uses MAC addresses to forward frames to the correct device.
- **Advantages:**
  - Supports full-duplex communication.
  - Reduces network congestion by directing traffic efficiently.
  - Faster and more intelligent than hubs.
- **Use Case:** Found in almost all modern LANs, improving network efficiency.

### **6. Routers**

- **Layer:** Operates at **Network Layer (Layer 3)**.
- **Function:** Routes data packets between different networks based on IP addresses.
- **Features:**
  - Connects different networks (e.g., LAN to WAN, Internet).
  - Uses routing protocols like RIP, OSPF, and BGP to determine the best path.
  - Supports Network Address Translation (NAT) for Internet communication.
- **Use Case:** Used in home networks, enterprises, and ISPs to direct traffic between different networks.

### **7. Gateways**

- **Layer:** Operates at **Multiple Layers (Layer 4 - Layer 7)**.
- **Function:** A gateway translates data between different network architectures and communication protocols (e.g., TCP/IP to OSI).
- **Example Use Cases:**
  - Email gateways translating between SMTP and X.400.
  - VoIP gateways translating between traditional telephony and Internet-based voice communication.
- **Key Difference from Routers:** While routers direct traffic based on IP addresses, gateways **convert protocols** and facilitate communication between different types of networks.

### **8. Virtual LANs (VLANs)**

- **Layer:** Operates at **Data Link Layer (Layer 2), but can be managed at Layer 3**.
- **Function:** A VLAN is a logical grouping of devices within a network, created to segment traffic for better management and security.
- **Advantages:**
  - Reduces broadcast traffic.
  - Enhances security by isolating groups of devices.
  - Increases flexibility by allowing devices to be grouped logically rather than physically.
- **Example:** A company can use VLANs to separate HR, Finance, and IT departments, even if they are on the same physical switch.

### **Summary Table**

| **Device**   | **Layer**                   | **Function**                                                  |
| ------------ | --------------------------- | ------------------------------------------------------------- |
| **Repeater** | Physical (1)                | Amplifies signal                                              |
| **Hub**      | Physical (1)                | Broadcasts data to all ports                                  |
| **Bridge**   | Data Link (2)               | Connects LAN segments, filters by MAC                         |
| **Switch**   | Data Link (2)               | Directs frames to specific devices (MAC-based switching)      |
| **Router**   | Network (3)                 | Directs packets between different networks (IP-based routing) |
| **Gateway**  | Multiple (4-7)              | Translates between different network protocols                |
| **VLAN**     | Data Link (2) / Network (3) | Creates logical network segments                              |

---

## **`Gagan Saini`**
