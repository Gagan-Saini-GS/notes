# Unit 1

## 🌥️ **Introduction to Cloud Computing**

### **1. Cloud Computing at a Glance**

Cloud Computing refers to the delivery of computing services—such as servers, storage, databases, networking, software, analytics, and intelligence—over the Internet ("the cloud") to offer faster innovation, flexible resources, and economies of scale.

Key Idea:

> “Use resources over the internet, on-demand, without owning them physically.”

#### 🔹 Key Components:

- **Client devices**: Phones, laptops, desktops.
- **Datacenters**: Massive facilities with servers.
- **Cloud services**: Compute, storage, networking, databases, ML, etc.

#### 🔹 Core Concept:

Cloud = Internet + Utility Computing + Distributed Systems + Virtualization

---

### **2. Vision of Cloud Computing**

The vision of cloud computing is:

- **On-demand computing as a utility**: Just like electricity or water.
- **Elastic and scalable**: Auto-scaling of resources based on need.
- **Minimal user management**: Users focus on usage, not infrastructure.

**Future vision:**

- Everything as a Service (**XaaS**)
- Serverless architecture
- Edge + AI integration
- Green, sustainable computing

---

### **3. Defining a Cloud**

A **Cloud** is a model that enables:

- Ubiquitous
- Convenient
- On-demand network access
- To a shared pool of configurable computing resources

**Definition by NIST** (National Institute of Standards and Technology):

> “A model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources...”

---

### **4. Cloud Computing Reference Model**

A **reference model** explains the architecture of cloud in layers:

```
+----------------------+
|     Applications     | → SaaS (e.g., Gmail, Salesforce)
+----------------------+
|   Platform Services  | → PaaS (e.g., Heroku, Google App Engine)
+----------------------+
| Infrastructure Layer | → IaaS (e.g., AWS EC2, Azure VMs)
+----------------------+
| Virtualization Layer |
+----------------------+
| Physical Resources   | → Servers, storage, networking
+----------------------+
```

---

### **5. Characteristics of Cloud Computing**

🔹 **On-demand self-service**: Users can provision resources themselves.

🔹 **Broad network access**: Services are available over the network (e.g., Internet) and accessible through standard devices.

🔹 **Resource pooling**: Resources are shared among users using multi-tenancy.

🔹 **Rapid elasticity**: Resources scale up/down automatically.

🔹 **Measured service**: Usage is monitored and billed accordingly.

---

### **6. Benefits of Cloud Computing**

- 💸 **Cost Efficiency**: Pay-as-you-go model reduces upfront investments.
- ⚡ **Scalability**: Instantly scale up or down based on demand.
- 🛠️ **Flexibility**: Access data and apps from anywhere.
- 🔒 **Reliability**: Backup, disaster recovery, and redundancy built-in.
- ⏱️ **Speed**: Fast provisioning of resources.
- 🔄 **Automatic Updates**: Software and infrastructure updates are handled by the provider.

---

### **7. Challenges Ahead**

Despite its popularity, cloud faces several challenges:

- **Security & Privacy**: Data in transit and at rest must be protected.
- **Vendor Lock-in**: Migration between providers can be difficult.
- **Downtime**: Internet dependency can cause accessibility issues.
- **Latency**: Real-time applications may suffer delays.
- **Legal & Regulatory Compliance**: Data residency, GDPR, HIPAA, etc.
- **Complexity in hybrid environments**

---

### **8. Historical Developments of Cloud Computing**

Understanding the evolution helps appreciate the depth of cloud systems:

#### 📜 **Timeline & Key Milestones:**

- **1960s** – John McCarthy (AI pioneer) proposed the idea of **computing as a utility**.
- **1970s-1980s** – Mainframe and time-sharing systems emerged. IBM introduced **virtualization**.
- **1990s** – Rise of **Internet & Web services**; ASPs (Application Service Providers) offered basic online services.
- **2000s** – Emergence of **grid computing** and **SaaS models**. Salesforce (1999) offered cloud-based CRM.
- **2006** – **Amazon Web Services (AWS)** launched EC2 & S3—landmark for IaaS.
- **2010s** – Cloud becomes mainstream with Microsoft Azure, Google Cloud, IBM Cloud, etc.
- **2020s** – Rise of **serverless**, **multi-cloud**, **edge computing**, and **AI integration** in the cloud.

---

### **9. Risks and Approaches of Migration into Cloud**

#### ⚠️ Risks of Cloud Migration:

- **Data Loss**: Poor backup or sync failures.
- **Security Vulnerabilities**: Misconfigured permissions, exposure.
- **Downtime**: Improper migration strategy can disrupt services.
- **Vendor Lock-in**: Difficulty switching providers.
- **Compliance Risks**: Violating regulations due to storage location.
- **Cost Overruns**: Poor resource planning increases bills.

#### ✅ Approaches to Migration:

1. **Rehosting (Lift & Shift)**:

   - Move applications "as-is" to the cloud.
   - Quick but may not utilize cloud-native benefits.

2. **Refactoring (Re-architecting)**:

   - Modify the app to use cloud-native services (e.g., using serverless).

3. **Replatforming**:

   - Minor modifications while shifting to a new platform (e.g., moving DB to managed service).

4. **Repurchasing**:

   - Switch to different cloud-based software (e.g., CRM → Salesforce).

5. **Retiring**:

   - Remove outdated apps during migration.

6. **Retaining**:

   - Keep apps on-premise if not suitable for migration.

---

### **10. Types of Clouds**

#### ☁️ **Based on Deployment:**

| Type                | Description                                                             | Example Use-Case                        |
| ------------------- | ----------------------------------------------------------------------- | --------------------------------------- |
| **Public Cloud**    | Shared resources on the Internet. Owned by 3rd party providers.         | Startups using AWS, Azure               |
| **Private Cloud**   | Used by one organization only. More control & security.                 | Banks, government                       |
| **Hybrid Cloud**    | Combines public + private clouds with integration.                      | Enterprises running legacy + cloud      |
| **Community Cloud** | Shared infrastructure for specific community (e.g., health, education). | Hospitals sharing patient data platform |

---

### **11. Service Models**

These models define what kind of services cloud offers to users.

#### 🔹 **IaaS (Infrastructure as a Service)**

- Provides: Virtual machines, storage, network.
- User manages: OS, runtime, apps.
- Example: AWS EC2, Google Compute Engine, Microsoft Azure VMs

#### 🔹 **PaaS (Platform as a Service)**

- Provides: Application platform with OS, DB, and tools.
- User manages: Applications & data.
- Example: Heroku, Google App Engine, Azure App Services

#### 🔹 **SaaS (Software as a Service)**

- Provides: Complete applications accessed over the internet.
- User manages: Just user accounts & settings.
- Example: Gmail, Dropbox, Salesforce

#### 🔹 Additional Emerging Models:

- **FaaS** (Function as a Service): Serverless functions (e.g., AWS Lambda)
- **BaaS** (Backend as a Service): Firebase, Supabase
- **DaaS** (Desktop as a Service): Amazon WorkSpaces

---

### **12. Cloud Reference Model (Expanded View)**

The **Cloud Reference Model** is often layered and maps service models with system architecture.

#### 🧱 **Layers Overview:**

| Layer                       | Description                            | Linked with             |
| --------------------------- | -------------------------------------- | ----------------------- |
| **Application Layer**       | Apps provided as SaaS to end-users     | SaaS                    |
| **Platform Layer**          | Platforms to deploy and manage apps    | PaaS                    |
| **Infrastructure Layer**    | Compute, storage, network resources    | IaaS                    |
| **Virtualization Layer**    | Abstraction of physical resources      | Hypervisors, Containers |
| **Physical Resource Layer** | Physical servers, storage, and network | Data Centers            |

This model helps in:

- Designing cloud systems
- Identifying security responsibilities (shared responsibility model)
- Mapping migration strategies

---

## ✅ Summary Table

| Topic                | Key Points                                       |
| -------------------- | ------------------------------------------------ |
| Cloud Overview       | Internet-based computing, resource pooling       |
| Vision               | Utility computing, scalable services             |
| Definition           | On-demand access to shared resources             |
| Ref Model            | Layers: App → Infra → Virtual → Physical         |
| Characteristics      | On-demand, broad access, elasticity, pooling     |
| Benefits             | Cost-effective, scalable, reliable, fast         |
| Challenges           | Security, compliance, latency, lock-in           |
| History              | 1960s concept → 2006 AWS → Serverless, AI        |
| Migration Risks      | Downtime, data loss, compliance, cost            |
| Migration Approaches | Lift & shift, replatform, refactor, repurchase   |
| Cloud Types          | Public, Private, Hybrid, Community               |
| Service Models       | IaaS, PaaS, SaaS (+ FaaS, BaaS, DaaS)            |
| Reference Model      | Layered model mapping services to infrastructure |

---
