# Unit 4

## 🔐 Securing the Cloud

### **1. Cloud Information Security Fundamentals**

Cloud information security refers to **safeguarding data, applications, and infrastructure** in a cloud environment from cyber threats, unauthorized access, data breaches, and service disruptions.

**Core Principles (CIA Triad):**

- **Confidentiality:** Only authorized users should access data.
- **Integrity:** Data must not be tampered with during storage/transmission.
- **Availability:** Services/data must be accessible when needed.

Additional Security Concepts:

- **Authentication & Authorization**
- **Non-repudiation**
- **Accountability (Auditing/Logging)**

---

### **2. Cloud Security Services**

These are tools and practices provided by cloud service providers (CSPs) or third parties to protect cloud environments:

| Security Service                           | Description                                                                   |
| ------------------------------------------ | ----------------------------------------------------------------------------- |
| **IAM (Identity & Access Management)**     | Controls user access to resources. Examples: AWS IAM, Azure Active Directory. |
| **Encryption (Data at rest / in transit)** | Protects data using cryptographic techniques (AES, RSA, TLS/SSL).             |
| **Firewalls & Perimeter Security**         | Virtual firewalls filter traffic. E.g., AWS Security Groups.                  |
| **Security Monitoring & SIEM**             | Real-time monitoring of security events. E.g., Splunk, Azure Sentinel.        |
| **Intrusion Detection Systems (IDS)**      | Detect malicious activities in the cloud.                                     |
| **Backup & Recovery**                      | Ensures business continuity in case of data loss.                             |

---

### **3. Cloud Security Design Principles**

Security must be **built-in from the start** using these core principles:

- **Least Privilege:** Users get only the permissions they need.
- **Defense in Depth:** Use layered security (firewall + IAM + encryption).
- **Fail-Safe Defaults:** Deny access by default unless explicitly allowed.
- **Separation of Duties:** Prevent abuse of privilege by distributing responsibilities.
- **Minimize Attack Surface:** Reduce open ports, exposed services.
- **Audit & Logging:** Maintain logs to track and investigate activities.
- **Secure-by-Design:** Code and architecture should consider security from the beginning.

---

### **4. Policy Implementation in Cloud Security**

Security policies define **rules, controls, and responsibilities** in cloud usage.

Key Policies Include:

- **Access Control Policy**
- **Password and Identity Management Policy**
- **Data Retention & Disposal Policy**
- **Incident Response Policy**
- **Acceptable Use Policy**
- **Encryption Policy**

Implementation Tools:

- IAM roles, permission sets, MFA enforcement, automatic policy validation.

---

### **5. Cloud Computing Security Challenges**

| Challenge                        | Description                                              |
| -------------------------------- | -------------------------------------------------------- |
| **Data Breaches**                | Unauthorized access to sensitive data.                   |
| **Data Loss**                    | Due to accidental deletion, corruption, or failure.      |
| **Account Hijacking**            | Credential theft and misuse.                             |
| **Insecure APIs**                | Exploitable interfaces or tokens.                        |
| **Misconfigured Cloud Settings** | Open buckets, permissive roles.                          |
| **Denial of Service (DoS)**      | Flooding services to make them unavailable.              |
| **Insider Threats**              | Malicious or negligent employees.                        |
| **Shared Technology Risks**      | Hypervisor vulnerabilities in multi-tenant environments. |

---

### **6. Cloud Computing Security Architecture**

Cloud security architecture is a **framework** that defines how security controls are deployed across cloud layers.

**Layers:**

- **Application Layer:** Secure SDLC, code reviews, web app firewalls (WAF).
- **Network Layer:** VPNs, subnets, NACLs, virtual firewalls.
- **Data Layer:** Encryption, tokenization, hashing.
- **Identity Layer:** IAM, SSO, RBAC, MFA.
- **Physical Layer:** Secured data centers, surveillance, access control.

**Security Models:**

- **Zero Trust Model:** Never trust, always verify.
- **Shared Responsibility Model:** Security roles are shared between provider and consumer.

---

### **7. Legal Issues in Cloud Computing**

Cloud introduces **jurisdictional and compliance challenges**:

- **Data Location & Sovereignty:** Where is the data stored? What country's laws apply?
- **Compliance Requirements:** GDPR (EU), HIPAA (US), PCI-DSS, etc.
- **Data Retention & Disposal Laws:** How long data must be kept, and how it must be deleted.
- **Third-party Responsibility:** Can CSPs be held accountable for a breach?
- **E-discovery & Forensics:** Legal right to access cloud logs, emails for investigation.
- **Contractual Obligations:** Security clauses in SLA and contracts must be clearly defined.

---

## 🛡️ Data Security in Cloud

---

### **1. Risk Mitigation in Cloud Data Security**

Key Risk Mitigation Strategies:

- **Data Encryption:** End-to-end encryption for both at-rest and in-transit data.
- **Redundancy & Backup:** Prevents data loss due to corruption or failure.
- **Access Control & Audit Logs:** Limit access and maintain full traceability.
- **Tokenization & Masking:** Protect sensitive data (e.g., card numbers).
- **Data Classification:** Label data based on sensitivity for appropriate handling.
- **Security Patching:** Ensure systems are always updated.

---

### **2. Understanding and Identification of Threats in Cloud**

| Threat                     | Explanation                                          |
| -------------------------- | ---------------------------------------------------- |
| **Malware Injection**      | Malicious code injected into cloud applications.     |
| **Side-Channel Attacks**   | Leaking information via shared resources.            |
| **VM Escape**              | Attacker breaks out of VM to access host/hypervisor. |
| **Data Leakage via APIs**  | Improperly secured APIs expose user data.            |
| **Shadow IT**              | Unauthorized use of cloud services.                  |
| **Insecure Data Deletion** | Improper data disposal may leave data recoverable.   |

---

### **3. SLA – Service Level Agreements**

SLAs are **contracts** between CSP and customer that define:

- **Uptime Guarantees:** E.g., 99.99% availability.
- **Data Ownership:** Who owns uploaded data?
- **Backup and Recovery Terms**
- **Security Responsibility:** What the provider secures vs. what the client secures.
- **Incident Response Time:** Defined timelines for addressing issues.
- **Penalties for SLA Violation**

**Tip:** Always ensure **security-related SLAs** are well-defined before adoption.

---

### **4. Trust Management in Cloud**

Trust Management involves **evaluating, establishing, and maintaining trust** in the cloud provider and the infrastructure.

**Elements:**

- **Provider Transparency:** Clear security posture and compliance reports (SOC 2, ISO 27001).
- **Customer Control:** Tools to manage access, encryption keys, and logs.
- **Certifications & Audits:** Prove provider’s security capabilities.
- **Third-Party Assessments:** Independent audits increase trust.
- **Reputation & History:** Past security incidents and resolution track record.

---

## ✅ Summary Table

| Topic                           | Key Concepts                                       |
| ------------------------------- | -------------------------------------------------- |
| **Cloud Security Fundamentals** | CIA triad, IAM, encryption, firewalls              |
| **Security Services**           | IAM, SIEM, IDS, backup                             |
| **Design Principles**           | Least privilege, defense in depth                  |
| **Policy Implementation**       | Access control, encryption, auditing               |
| **Security Challenges**         | Data breach, account hijacking, insider threats    |
| **Security Architecture**       | Application, network, data, identity layers        |
| **Legal Issues**                | Data sovereignty, compliance, liability            |
| **Data Security**               | Threat identification, risk mitigation, encryption |
| **SLA**                         | Availability, data rights, responsibilities        |
| **Trust Management**            | Transparency, compliance, control                  |

---
