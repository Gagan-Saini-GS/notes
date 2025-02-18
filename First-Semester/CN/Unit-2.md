# Unit-2

## **The Physical Layer: Transmission Media**

The **Physical Layer** is the **first layer** of the **OSI model**, responsible for the transmission of raw data (bits) over a physical medium. It defines the hardware and transmission methods used to send data between devices.

### **Types of Transmission Media**

Transmission media can be classified into two main types:

#### **1. Guided Media (Wired Communication)**

Guided media use **physical cables** to transmit signals. These are more secure, reliable, and less prone to interference.

##### **A. Twisted Pair Cable**

- Consists of **two insulated copper wires twisted together**.
- Used in **Ethernet LANs, telephone lines**.
- **Types:**
  - **Unshielded Twisted Pair (UTP)** – Common in LANs, cheaper but more susceptible to interference.
  - **Shielded Twisted Pair (STP)** – Has extra shielding to reduce interference.
- **Speed:** Up to **10 Gbps** (Cat6 and Cat7 cables).

##### **B. Coaxial Cable**

- Has a **central conductor, insulation, metallic shield, and outer cover**.
- Used for **Cable TV, Internet (older broadband networks)**.
- **Speed:** Up to **10 Gbps**.

##### **C. Fiber Optic Cable**

- Uses **light signals** instead of electricity.
- Faster and more reliable than copper cables, but expensive.
- **Types:**
  - **Single-mode fiber (SMF):** Long-distance, high-speed transmission.
  - **Multi-mode fiber (MMF):** Shorter distances, used in LANs.
- **Speed:** Up to **100 Gbps** or more.

#### **2. Unguided Media (Wireless Communication)**

Unguided media transmits data **through air, space, or water** using electromagnetic waves.

##### **A. Radio Waves**

- Used for **broadcasting, Wi-Fi, Bluetooth, cellular networks**.
- Can travel **long distances**, but prone to interference.

##### **B. Microwaves**

- Used in **satellite communication, Wi-Fi, mobile networks**.
- Requires a **line-of-sight** between sender and receiver.

##### **C. Infrared (IR)**

- Used for **short-range** communication (e.g., TV remote, infrared sensors).
- Cannot pass through obstacles like walls.

##### **D. Satellite Communication**

- Uses **geostationary or low-earth orbit (LEO) satellites** to provide global coverage.
- Used for **GPS, satellite TV, and internet services**.

### **Comparison of Transmission Media**

| Media Type                 | Example Uses                | Speed         | Distance     | Interference Resistance | Cost   |
| -------------------------- | --------------------------- | ------------- | ------------ | ----------------------- | ------ |
| **Twisted Pair (UTP/STP)** | LAN, Telephone lines        | Up to 10 Gbps | Short-Medium | Medium                  | Low    |
| **Coaxial Cable**          | Cable TV, Internet          | Up to 10 Gbps | Medium       | High                    | Medium |
| **Fiber Optic**            | High-speed networks         | 100 Gbps+     | Long         | Very High               | High   |
| **Radio Waves**            | Wi-Fi, FM Radio             | Variable      | Long         | Low                     | Low    |
| **Microwaves**             | Mobile networks, Satellites | High          | Medium       | Medium                  | Medium |
| **Infrared**               | TV remotes                  | Low           | Very Short   | High                    | Low    |
| **Satellite**              | Global communication        | Medium        | Very Long    | High                    | High   |

### **Key Takeaways**

✅ **Guided Media (Wired):** More reliable, faster, but limited by physical cables.  
✅ **Unguided Media (Wireless):** Flexible, used for mobility, but prone to interference.  
✅ **Fiber Optic** is the fastest, **Twisted Pair** is most common, **Radio & Microwave** are used in wireless communication.

---

## **PSTN: Structure of the Telephone System**

The **Public Switched Telephone Network (PSTN)** is the global network of telephone lines, fiber optics, satellites, and switching centers that allow voice communication between users. It is the foundation of traditional **landline telephony** and has evolved to support digital services like **DSL and ISDN**.

### **Structure of the Telephone System**

The PSTN is divided into different components that help in call routing and transmission:

#### **1. Subscriber (User) Section**

- The **end-users** who use telephones to make calls.
- Connected to the telephone exchange via a **local loop (twisted pair cables)**.

#### **2. Local Exchange (Central Office - CO)**

- A telephone switching facility that connects **local subscribers** within a small geographical area.
- It manages **dial tone, call routing, and call switching** for landline phones.

#### **3. Tandem Office (Intermediate Switching Center)**

- Connects multiple local exchanges **within a city or region**.
- Helps in **routing long-distance calls** efficiently.

#### **4. Toll Office (Long-Distance Switching Center)**

- Routes **long-distance calls** between cities or even countries.
- Uses **fiber optic cables, microwave links, or satellites** for communication.

#### **5. International Gateway**

- Connects national PSTN networks to the **global telephone network**.
- Uses **submarine cables, satellites, and high-speed fiber optics**.

### **PSTN Call Routing Example**

1. **Caller dials a number** (e.g., from New York to London).
2. The call is sent to the **Local Exchange (CO)**.
3. If it's a local call, it's connected immediately.
4. If it's a long-distance call, it goes through a **Tandem Office** and then to a **Toll Office**.
5. If it's an international call, it passes through the **International Gateway**.
6. The call reaches the recipient’s **Local Exchange**, which connects to their phone.

### **PSTN Technologies**

🔹 **Analog vs. Digital PSTN**

- **Older PSTN systems** used **analog signals** over twisted pair cables.
- **Modern PSTN systems** use **digital switching** for better call quality and efficiency.

🔹 **Signaling in PSTN**

- **SS7 (Signaling System No. 7)** is the standard protocol used for call setup, routing, and disconnection.
- It supports services like **caller ID, call forwarding, and voicemail**.

🔹 **Circuit-Switched Network**

- PSTN uses **circuit switching**, meaning a **dedicated path** is established for each call until it ends.
- This differs from **packet-switched networks** like the Internet, where data is split into packets and sent independently.

### **Comparison: PSTN vs. VoIP (Modern Telephony)**

| Feature          | PSTN (Traditional)                   | VoIP (Modern Internet Telephony)                |
| ---------------- | ------------------------------------ | ----------------------------------------------- |
| **Technology**   | Circuit-switched                     | Packet-switched (IP-based)                      |
| **Medium**       | Copper wires, fiber optics           | Internet (Wi-Fi, Ethernet)                      |
| **Call Quality** | High, but depends on line conditions | Varies, but often high with good internet       |
| **Cost**         | Expensive for long-distance calls    | Cheaper, especially for international calls     |
| **Flexibility**  | Requires landline phones             | Can use computers, smartphones, IP phones       |
| **Features**     | Limited (basic voice, caller ID)     | Advanced (video calls, messaging, integrations) |

### **Key Takeaways**

✅ PSTN is the **traditional telephone network**, using **circuit switching** to establish calls.  
✅ It consists of **Local Exchanges, Tandem Offices, Toll Offices, and International Gateways**.  
✅ **Modern PSTN systems** have evolved to support **digital transmission and services like DSL & ISDN**.  
✅ **VoIP (Voice over IP)** is replacing PSTN for many users due to **lower costs and better flexibility**.

---

## **Data & Signals: Data Types, Analog & Digital Signals**

In networking, data is transmitted in the form of signals across transmission media. The two primary types of signals used in data transmission are **analog** and **digital** signals. The data itself can be categorized into **analog** and **digital** types, each suited for different applications and transmission methods.

### **1. Data Types**

Data types refer to the form or nature of the data that is being transmitted or received. These are generally classified into two categories:

#### **A. Analog Data**

- **Nature:** Analog data is continuous and can take any value within a range.
- **Example:**
  - Sound waves, temperature, and other natural phenomena are analog.
  - Analog data is usually represented by **continuous waveforms**.

#### **B. Digital Data**

- **Nature:** Digital data is discrete, consisting of binary values (0s and 1s).
- **Example:**
  - Text, images, and numbers in computers.
  - Digital data is represented in a **binary format**.

### **2. Analog vs. Digital Signals**

#### **A. Analog Signals**

- **Nature:** Analog signals are continuous and can vary smoothly over time. They represent **analog data**.
- **Representation:** Represented as a continuous waveform with **amplitude** (height) and **frequency** (rate of oscillation).
- **Example:**
  - A **sine wave** is a common representation of an analog signal.
  - In telephony, **analog signals** were traditionally used for voice communication.
- **Pros:**
  - Can represent the full range of natural phenomena (like sound waves).
  - Simple and inexpensive to produce.
- **Cons:**
  - More susceptible to **noise** and **distortion** during transmission.
  - Limited distance over which the signal can be transmitted clearly without degradation.

#### **B. Digital Signals**

- **Nature:** Digital signals consist of discrete values that represent **binary data** (0s and 1s). They are typically used in digital communication systems.
- **Representation:** Represented as **square waves**, with only two possible voltage levels, usually **high (1)** and **low (0)**.
- **Example:**
  - **Computer networks**, digital telephony (VoIP), and fiber optic communication.
- **Pros:**
  - **Less susceptible to noise** compared to analog signals.
  - Easy to store, process, and replicate without degradation.
  - Can be encrypted, compressed, and error-checked.
- **Cons:**
  - Requires more complex technology and **higher bandwidth** for transmission.

### **3. Modulation Techniques**

Modulation is the process of varying a carrier signal in order to transmit data over a medium. It is used when we want to transmit digital data over an analog channel. There are various modulation techniques, especially for radio waves or telephone lines.

#### **A. Analog Modulation**

- **Amplitude Modulation (AM):** The amplitude (height) of the carrier wave is varied according to the data signal.
  - Example: Used in AM radio.
- **Frequency Modulation (FM):** The frequency of the carrier wave is varied according to the data signal.

  - Example: Used in FM radio.

- **Phase Modulation (PM):** The phase of the carrier wave is changed according to the data signal.
  - Example: Used in some forms of communication and satellite transmission.

#### **B. Digital Modulation**

- **Amplitude Shift Keying (ASK):** The amplitude of the carrier signal is changed to represent binary data.
- **Frequency Shift Keying (FSK):** The frequency of the carrier signal is varied to represent binary data.
- **Phase Shift Keying (PSK):** The phase of the carrier signal is shifted to represent data.
  - Example: Common in **modem communication** (like **DSL** and **ISDN**).

### **4. Modem & Cable Modem**

#### **A. Modem (Modulator-Demodulator)**

- A **modem** converts digital data from a computer or device into analog signals for transmission over **analog phone lines** and vice versa.
- **Function:**
  - **Modulation:** Converts digital data into analog signals for transmission.
  - **Demodulation:** Converts incoming analog signals back into digital data.
- **Example:** A **dial-up modem** that connects to the internet via a traditional phone line.

#### **B. Cable Modem**

- A **cable modem** allows high-speed internet access over **cable TV lines** (coaxial cables).
- Unlike traditional modems, cable modems provide **faster speeds** and **high-bandwidth data transfer**.
- **Function:**
  - Modulates the data for transmission over coaxial cable.
  - Demodulates the incoming signal to be understood by the device.

### **Key Takeaways:**

- **Analog data** is continuous, while **digital data** is discrete (binary).
- **Analog signals** vary smoothly and are used for transmitting **analog data**.
- **Digital signals** are discrete and carry **digital data** (binary), offering better noise resistance and quality.
- **Modulation techniques** (AM, FM, PSK, FSK) are used to transmit digital data over analog channels.
- **Modems** (modulator-demodulator) are used to convert between analog and digital signals, while **cable modems** offer faster internet over cable TV lines.

---

## **Protocols: DSL, ISDN, and Other Networking Protocols**

Let's explore the **DSL (Digital Subscriber Line)**, **ISDN (Integrated Services Digital Network)**, and other important networking protocols, which help in the transmission of data and provide reliable communication over both analog and digital networks.

### **1. DSL (Digital Subscriber Line)**

DSL is a family of **high-speed internet connection technologies** that provide broadband access over **standard copper telephone lines**. Unlike traditional dial-up, DSL can transmit voice and data simultaneously over the same line.

#### **Types of DSL**

- **ADSL (Asymmetric DSL):**

  - **Download speed** is higher than upload speed (asymmetrical).
  - Most commonly used for home broadband because users generally download more data than they upload.
  - **Speeds:** Typically up to **24 Mbps** download and **1 Mbps** upload.

- **SDSL (Symmetric DSL):**

  - Equal upload and download speeds (symmetric).
  - Typically used by businesses needing high-speed uploads and downloads.
  - **Speeds:** Typically up to **2 Mbps** in both directions.

- **VDSL (Very High-Speed DSL):**
  - A faster version of ADSL, supporting very high speeds over short distances.
  - **Speeds:** Up to **100 Mbps** over very short distances, decreasing as distance increases.

#### **Advantages of DSL**

- Uses existing **telephone lines**, so installation is relatively easy.
- **Always on**: Unlike dial-up, DSL does not require a connection to be established every time you want to access the internet.
- Simultaneous voice and data transmission without interference.
- Faster speeds compared to traditional **dial-up connections**.

#### **Limitations of DSL**

- Speed depends on **distance** from the **telephone exchange**.
- Can be affected by line quality and **electromagnetic interference**.

### **2. ISDN (Integrated Services Digital Network)**

ISDN is an older **digital telecommunication standard** that allows voice, video, and data transmission over **standard copper telephone lines**. ISDN offers **higher-quality service** compared to analog telephone systems.

#### **Types of ISDN**

- **BRI (Basic Rate Interface):**

  - Designed for **small businesses** or individual users.
  - Provides **two 64 Kbps B-channels** for data and one 16 Kbps D-channel for signaling.
  - **Total Speed:** Up to **128 Kbps**.

- **PRI (Primary Rate Interface):**
  - Used by **large businesses** or enterprises that require more data channels.
  - Provides **23 B-channels** (64 Kbps each) and one 64 Kbps D-channel for signaling.
  - **Total Speed:** Up to **1.5 Mbps** (in North America) or **2 Mbps** (in Europe).

#### **Features of ISDN**

- Provides **digital signal** transmission, ensuring clearer voice calls and better data transfer speeds compared to analog.
- Can support multiple devices and services like **voice, fax, video conferencing, and data** over a single line.
- Used for **high-quality telephony**, **remote offices**, and **small businesses**.

#### **Limitations of ISDN**

- **Higher cost** compared to DSL or dial-up.
- **Limited availability** in rural or remote areas.
- Slower than modern broadband technologies like **fiber-optic** connections.

### **3. Other Networking Protocols**

#### **A. Frame Relay**

Frame Relay is a **wide-area network (WAN)** protocol used to connect devices over a public or private network. It allows **packet-switching** for transmitting data in **frames**.

- **Main Use:** Used for **connecting branch offices** in large organizations, especially in **legacy networks**.
- **Advantages:**
  - Efficient for **bursty traffic**.
  - Offers **low latency** for real-time communications.
- **Limitations:**
  - Outdated compared to newer technologies like **MPLS**.

#### **B. ATM (Asynchronous Transfer Mode)**

ATM is a **high-speed networking technology** used to transmit **data, voice, and video**. It uses **fixed-size packets** called **cells** for data transfer.

- **Main Use:** Used in **backbone networks** (ISP networks, core routers) for **high-speed data transfer**.
- **Advantages:**
  - **High-throughput** and **low latency** suitable for **real-time applications**.
  - Supports a variety of data types (voice, video, data).
- **Limitations:**
  - Complexity and cost of implementation.
  - Less commonly used today as it has been replaced by **Ethernet**.

#### **C. 802.11 (Wi-Fi)**

802.11 is a set of **IEEE standards** for **wireless networking** (Wi-Fi), commonly used in **home and office** networks.

- **Main Use:** Provides **wireless communication** between devices, commonly used for internet access.
- **Variants:**
  - **802.11a/b/g/n/ac/ax** (Wi-Fi 6) standards for **speed, range**, and **bandwidth** improvements.
- **Advantages:**
  - **High mobility** with **wireless connectivity**.
  - Can support a range of devices (laptops, smartphones, etc.).
- **Limitations:**
  - **Range limitations** (distance from the router).
  - **Interference** from other wireless devices.

#### **D. PPP (Point-to-Point Protocol)**

PPP is a **data link protocol** used to establish a direct connection between two network nodes, typically in **dial-up** and **VPN** connections.

- **Main Use:** Used for **internet access** over **serial lines**, like dial-up connections and **VPN tunnels**.
- **Advantages:**
  - Simple to implement.
  - Supports multiple **authentication** and **encryption** methods.
- **Limitations:**
  - Older technology, largely replaced by **Ethernet** and **Wi-Fi**.

#### **E. HDLC (High-Level Data Link Control)**

HDLC is a **synchronous data link protocol** that provides error-free data communication. It's used in **WANs** and is the foundation of many other protocols.

- **Main Use:** Used for **point-to-point** and **point-to-multipoint** connections in **WANs**.
- **Advantages:**
  - Provides **error correction** and **flow control**.
  - Suitable for **high-throughput applications**.
- **Limitations:**
  - **Not widely used** today, replaced by newer protocols like **PPP** and **Ethernet**.

### **Key Takeaways**

- **DSL** provides broadband over copper lines, with different variations offering asymmetric or symmetric speeds.
- **ISDN** is an older digital standard used for voice, video, and data transmission, offering higher quality than analog systems.
- **Frame Relay** and **ATM** are older WAN technologies, now largely replaced by **MPLS** and **Ethernet**.
- **Wi-Fi (802.11)** allows wireless communication in homes and offices.
- **PPP** and **HDLC** are data link protocols, with PPP used in dial-up and VPN connections, and HDLC being foundational in WAN communications.

---

## **Data Link Layer Design Issues**

The **Data Link Layer** (Layer 2 of the OSI model) is responsible for transferring data between devices on the same network and ensuring that data is delivered accurately and without errors. The design of this layer addresses key issues related to framing, error control, flow control, and how data is transmitted reliably over the network.

### **Key Design Issues of the Data Link Layer**

### **1. Framing**

Framing is the process of dividing the data received from the upper layers into manageable blocks called **frames** for transmission over the network. Each frame typically contains a **header**, **data payload**, and a **trailer**.

#### **Why Framing is Important:**

- **Delimits Data:** It marks the boundaries of a transmitted data unit so that the receiving device knows where the data begins and ends.
- **Error Detection:** The header and trailer often contain information used for **error checking**.
- **Synchronization:** Frames ensure that data is synchronized and can be transmitted at appropriate intervals.

#### **Frame Components:**

- **Header:** Contains control information (e.g., addresses, type of data).
- **Data Payload:** The actual user data being transmitted.
- **Trailer:** Typically contains error detection bits, like **CRC (Cyclic Redundancy Check)**, to ensure the integrity of the data.

### **2. Error Control**

Error control is an essential aspect of the Data Link Layer to ensure the reliable transmission of data. It involves detecting and correcting errors that may occur during the transmission of data over the network.

#### **Types of Errors:**

- **Single-bit errors:** Occur when a single bit is corrupted during transmission.
- **Burst errors:** Occur when a series of bits are corrupted in sequence.

#### **Error Detection Mechanisms:**

- **Parity Check:** Adds a single parity bit to the data to check whether the number of 1's is even or odd.
- **Cyclic Redundancy Check (CRC):** A mathematical algorithm that generates a checksum value, which is compared between the sender and receiver to detect errors.
- **Checksum:** A value derived from a sum of the bits in the message, used to detect errors in data transmission.

#### **Error Correction Mechanisms:**

- **Automatic Repeat Request (ARQ):** If an error is detected, the receiver can request the sender to retransmit the data.
  - **Stop-and-Wait ARQ:** The sender transmits one frame and waits for an acknowledgment before sending the next one.
  - **Go-Back-N ARQ:** The sender can send multiple frames but the receiver will only acknowledge the last correctly received frame.
  - **Selective Repeat ARQ:** Only the frames that were received incorrectly are retransmitted.

### **3. Flow Control**

Flow control ensures that data is sent at an appropriate rate, preventing congestion or data loss. It is particularly important when the sender is faster than the receiver.

#### **Flow Control Mechanisms:**

- **Stop-and-Wait Protocol:** The sender waits for an acknowledgment after sending each frame before proceeding with the next one.
- **Sliding Window Protocol:** The sender can send multiple frames before receiving an acknowledgment. The receiver can manage the flow of data by sliding the window size, which controls the number of frames allowed in transit at once.
- **Credit-Based Flow Control:** This is a more complex method that provides a more efficient mechanism for managing the amount of data sent.

### **Protocols for Data Link Layer:**

#### **A. FDDI (Fiber Distributed Data Interface)**

FDDI is a high-speed networking standard used to connect devices over a **fiber-optic backbone**. It is commonly used for **LANs** and **backbone networks** due to its reliability and speed.

- **Speed:** Up to **100 Mbps**.
- **Topology:** It uses a **dual-ring topology** for fault tolerance, where data can flow in either direction around the network.

#### **B. CDDI (Copper Distributed Data Interface)**

CDDI is the copper-based counterpart to FDDI, providing similar functionality but using **twisted pair cables** instead of fiber optics.

- **Speed:** Also supports speeds up to **100 Mbps**.
- **Topology:** Uses a similar **dual-ring topology** like FDDI, providing **redundancy and fault tolerance**.

#### **C. Frame Relay**

Frame Relay is a **WAN protocol** used to connect devices in a **packet-switched network**. It provides **efficient data transfer** for bursty traffic and low-delay applications.

- **Speed:** Typically supports speeds ranging from **56 Kbps to 1.5 Mbps**.
- **Error Control:** It provides **error detection** but relies on higher layers for **error correction**.
- **Applications:** Commonly used for **connecting branch offices** in large organizations.

#### **D. ATM (Asynchronous Transfer Mode)**

ATM is a high-performance networking technology that supports **voice, video, and data** transfer in a **cell-based** format. It is widely used in **backbone networks** and **high-speed WANs**.

- **Speed:** Can support speeds of up to **10 Gbps**.
- **Cell Size:** Uses **fixed-size 53-byte cells**, which allow for **efficient and predictable transmission**.

#### **E. 802.11 (Wi-Fi)**

Wi-Fi (IEEE 802.11) is a set of protocols used for **wireless communication** in local area networks (LANs). It supports **high-speed wireless data transmission** in homes, businesses, and public spaces.

- **Speed:** Wi-Fi speeds can range from **11 Mbps (802.11b)** to **10 Gbps (Wi-Fi 6)**.
- **Technology:** Uses **spread spectrum** and **orthogonal frequency-division multiplexing (OFDM)** for efficient spectrum usage.

#### **F. PPP (Point-to-Point Protocol)**

PPP is a **data link layer protocol** used to establish a direct connection between two nodes. It is widely used for **dial-up connections** and **VPNs**.

- **Main Use:** Used for **internet access** over serial lines (like **telephone lines** or **fiber connections**).
- **Protocols Supported:** Supports **authentication**, **compression**, and **encryption** for secure communication.

#### **G. HDLC (High-Level Data Link Control)**

HDLC is a **synchronous data link protocol** that provides error-free communication over a **serial link**.

- **Main Use:** Used in **WANs**, especially in **point-to-point** and **multipoint** connections.
- **Features:** Provides **error detection**, **flow control**, and **data link synchronization**.

### **Key Takeaways:**

- **Framing** breaks data into manageable units for transmission.
- **Error Control** ensures data integrity by detecting and correcting errors.
- **Flow Control** prevents congestion by regulating the rate of data transfer.
- **Protocols like FDDI, CDDI, Frame Relay, ATM, and 802.11** ensure reliable communication, each suited for specific types of networks and traffic patterns.

---

## **`Gagan Saini`**
