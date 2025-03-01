# Unit-3

## **Types of Requirements in Software Project Management**

In **Software Project Management (SPM)**, requirements define what the software system should do. They are categorized into different types:

1. **Functional Requirements (FRs)**

   - Define what the system must do.
   - Specify software behavior and functionality.
   - Example: "The system should allow users to log in using email and password."

2. **Non-Functional Requirements (NFRs)**

   - Define system constraints and qualities like performance, security, and usability.
   - Example: "The system should load within 3 seconds."

3. **Business Requirements**

   - High-level requirements focusing on business goals and objectives.
   - Example: "The software should help increase customer engagement by 20%."

4. **User Requirements**

   - Describe user needs and interactions with the system.
   - Example: "Users should be able to reset their password via email."

5. **System Requirements**

   - Technical details specifying hardware, software, and configurations.
   - Example: "The system should support Windows, macOS, and Linux."

6. **Regulatory Requirements**

   - Compliance-related requirements enforced by laws and standards.
   - Example: "The system should comply with GDPR for data protection."

7. **Interface Requirements**
   - Define interactions between software components or with external systems.
   - Example: "The system should integrate with PayPal for payment processing."

---

## **Feasibility Study in Software Project Management**

A **Feasibility Study** is conducted to determine whether a project is viable before committing resources. It evaluates different aspects of the project:

1. **Technical Feasibility**

   - Evaluates if the project can be developed with existing technology.
   - Considers hardware, software, and technical skills.
   - Example: "Can our existing system integrate AI-based recommendations?"

2. **Economic Feasibility (Cost-Benefit Analysis)**

   - Determines if the project is financially viable.
   - Compares costs (development, maintenance) against expected benefits (profit, savings).
   - Example: "Will investing $100,000 in development yield significant returns?"

3. **Operational Feasibility**

   - Analyzes whether the system will function smoothly in the organization.
   - Considers user acceptance, ease of use, and training needs.
   - Example: "Can employees easily adapt to the new CRM system?"

4. **Legal Feasibility**

   - Ensures the project follows laws, regulations, and compliance standards.
   - Example: "Does the software comply with data protection laws?"

5. **Schedule Feasibility**
   - Evaluates if the project can be completed within the given timeframe.
   - Example: "Can we deliver the project in 6 months with the available resources?"

A feasibility study helps decide whether to proceed with a project or reconsider its approach.

---

## **Requirement Elicitation Techniques in Software Project Management**

Requirement elicitation is the process of gathering requirements from stakeholders. Several techniques are used to ensure clear and complete requirements. Here are some key techniques:

### **1. Interviews**

- A face-to-face or virtual discussion with stakeholders to collect requirements.
- Can be **structured** (predefined questions) or **unstructured** (open-ended discussions).
- Helps in understanding detailed requirements and expectations.

✅ **Advantages:**

- Allows in-depth discussions.
- Can clarify vague requirements immediately.

❌ **Disadvantages:**

- Time-consuming.
- Risk of missing important details if questions are not well-prepared.

🔹 **Example:**  
A project manager interviews a sales team to understand the features required in a new CRM software.

### **2. Questionnaire**

- A set of structured questions given to stakeholders to collect information.
- Can be **open-ended** (free-text responses) or **closed-ended** (multiple choice, yes/no).
- Useful when gathering data from a large number of users.

✅ **Advantages:**

- Saves time for both parties.
- Can collect responses from many stakeholders.

❌ **Disadvantages:**

- Lacks real-time clarification of answers.
- Response rates may be low if participants are not motivated.

🔹 **Example:**  
A software company sends an online questionnaire to customers asking about desired features in a mobile banking app.

### **3. Brainstorming**

- A creative group discussion to generate new ideas and solutions.
- Encourages free thinking and idea sharing among team members and stakeholders.
- Often used in the early stages of requirement gathering.

✅ **Advantages:**

- Encourages innovation.
- Helps in identifying new opportunities and improvements.

❌ **Disadvantages:**

- Can be unstructured and unproductive without proper moderation.
- Some participants may dominate the discussion, limiting input from others.

🔹 **Example:**  
A development team brainstorms ideas for a new e-commerce platform's unique features.

### **4. Facilitated Application Specification Technique (FAST)**

- A structured workshop involving key stakeholders, developers, and facilitators.
- The goal is to collaboratively define system requirements and resolve conflicts.
- Encourages real-time interaction and feedback.

✅ **Advantages:**

- Reduces misunderstandings.
- Ensures stakeholder involvement from the start.

❌ **Disadvantages:**

- Requires skilled facilitators.
- Can be difficult to coordinate schedules for all participants.

🔹 **Example:**  
A team organizes a FAST session with doctors and nurses to define requirements for a hospital management system.

Each technique has its strengths and weaknesses. The best approach is often a **combination** of these techniques to ensure complete and accurate requirements.

---

## **Requirement Analysis and Design in Software Project Management**

Requirement analysis and design help in structuring and documenting system requirements for development. Two important tools used in this phase are **Data Flow Diagram (DFD)** and **Data Dictionary**.

### **1. Data Flow Diagram (DFD)**

A **Data Flow Diagram (DFD)** is a graphical representation of how data moves through a system. It focuses on the flow of information rather than on the system’s logic.

#### **DFD Components**

1. **External Entities (Sources/Sinks)**

   - Represent users, systems, or organizations that interact with the system.
   - Example: "Customer," "Bank," or "Supplier."

2. **Processes**

   - Represent operations that transform input data into output data.
   - Example: "Process Order," "Generate Report."

3. **Data Stores**

   - Represent storage locations where data is held.
   - Example: "Customer Database," "Order Records."

4. **Data Flows**
   - Represent the movement of data between entities, processes, and data stores.
   - Example: "Customer sends order details."

#### **DFD Levels**

- **Level 0 (Context Diagram)** → The highest level, showing the system as a single process interacting with external entities.
- **Level 1** → Expands the main process into multiple sub-processes.
- **Level 2 and beyond** → Further breakdown of sub-processes for detailed analysis.

✅ **Advantages:**

- Provides a clear visual understanding of system processes.
- Helps identify redundancies and inefficiencies.

❌ **Disadvantages:**

- Does not show decision-making logic.
- Can become complex for large systems.

🔹 **Example:**  
A DFD for an online shopping system would show processes like **"Customer Places Order,"** data stores like **"Order Database,"** and external entities like **"Customer"** and **"Bank."**

### **2. Data Dictionary**

A **Data Dictionary** is a collection of descriptions of data elements in a system. It helps standardize definitions, making communication clear between developers, designers, and stakeholders.

#### **Data Dictionary Elements**

1. **Data Element Name** → The name of the data field. _(Example: Customer_ID)_
2. **Data Type** → The type of data (Integer, String, Date, etc.). _(Example: Integer)_
3. **Size** → The maximum length of the data. _(Example: 10 characters)_
4. **Description** → The meaning or purpose of the data element. _(Example: Unique ID for each customer)_
5. **Valid Values** → Allowed values or range. _(Example: 1000-9999)_
6. **Relationships** → Dependencies between data elements. _(Example: "Customer_ID" is related to "Order_ID")_

✅ **Advantages:**

- Improves data consistency and communication among teams.
- Helps in database design and system documentation.

❌ **Disadvantages:**

- Needs continuous updating as the system evolves.
- Can be complex for large projects.

🔹 **Example:**  
| Data Element | Data Type | Size | Description | Valid Values |  
|-------------|----------|------|-------------|--------------|  
| Customer_ID | Integer | 10 | Unique customer ID | 1000-9999 |  
| Name | String | 50 | Full name of customer | A-Z only |  
| Order_Date | Date | - | Date when order was placed | YYYY-MM-DD |

### **Conclusion**

- **DFD** helps visualize how data moves through the system.
- **Data Dictionary** helps define and standardize data elements.
- Both tools are essential in system analysis and design to ensure **clarity, accuracy, and efficiency** in software development.

---

## **Software Requirement Specification (SRS)**

A **Software Requirement Specification (SRS)** is a formal document that outlines the software system’s requirements in detail. It serves as a blueprint for developers, designers, and stakeholders to ensure that the final product meets business and technical needs.

### **1. Purpose of SRS**

- Clearly defines what the software should do.
- Acts as a communication bridge between stakeholders and the development team.
- Reduces misunderstandings and changes during development.
- Helps in project planning, cost estimation, and testing.

### **2. Structure of SRS (IEEE 830 Standard)**

A well-structured SRS typically includes the following sections:

#### **1. Introduction**

- **Purpose** → Why the system is being developed.
- **Scope** → What the system will and won’t cover.
- **Definitions, Acronyms, and Abbreviations** → Technical terms used.
- **References** → Links to external documents, laws, or standards.
- **Overview** → Summary of the document structure.

#### **2. Overall Description**

- **Product Perspective** → How the system fits into existing environments.
- **Product Functions** → Key features of the software.
- **User Characteristics** → Expected skill level of users.
- **Constraints** → Hardware, software, and regulatory limitations.
- **Assumptions and Dependencies** → External factors affecting the project.

#### **3. Specific Requirements**

- **Functional Requirements** → Features and behavior of the system.
- **Non-Functional Requirements** → Performance, security, usability, etc.
- **Interface Requirements** → User, hardware, software, and communication interfaces.
- **System Models** → Diagrams like DFDs, ER diagrams, etc.

#### **4. Appendices (Optional)**

- Additional information, tables, or data references.

#### **5. Index (Optional)**

- Quick reference to key terms and sections.

### **3. Types of Requirements in SRS**

1. **Functional Requirements**

   - Describe what the system should do.
   - Example: "The system shall allow users to reset passwords via email."

2. **Non-Functional Requirements (NFRs)**

   - Define system qualities like speed, security, and reliability.
   - Example: "The system should handle 10,000 simultaneous users."

3. **User Requirements**

   - Specify user needs and interactions.
   - Example: "Users should be able to track their order status."

4. **System Requirements**
   - Define technical aspects like hardware and software dependencies.
   - Example: "The software should run on Windows, Linux, and macOS."

### **4. Benefits of SRS**

✅ **Clear Communication** → Ensures everyone understands system requirements.  
✅ **Reduced Development Costs** → Avoids costly changes later in the project.  
✅ **Better Testing & Validation** → Provides clear benchmarks for testing.  
✅ **Efficient Project Management** → Helps in timeline and resource planning.

### **Conclusion**

An **SRS document** is critical for successful software development. It provides a **clear roadmap** for developers, testers, and stakeholders, ensuring the final product meets user expectations.

---

## **Object-Oriented Analysis and Design (OOAD)**

### **What is OOAD?**

Object-Oriented Analysis and Design (OOAD) is a method used to analyze, design, and develop software using **object-oriented principles** like **encapsulation, inheritance, and polymorphism**. It helps in building flexible, scalable, and maintainable systems.

### **1. UML (Unified Modeling Language) Overview**

**UML (Unified Modeling Language)** is a standardized way to visualize the structure and behavior of an object-oriented system. It provides a set of diagrams to represent different aspects of software design.

✅ **Purpose of UML:**

- Helps in **system analysis, design, and documentation**.
- Improves **communication** between developers, designers, and stakeholders.
- Allows for **better system understanding and maintainability**.

### **2. The Nature and Purpose of Models**

A **model** is a simplified representation of a system that helps in understanding and designing it before actual implementation.

🔹 **Purpose of Models in OOAD:**

1. **Visualization** → Provides a clear picture of system structure and behavior.
2. **Specification** → Defines the blueprint for developers to follow.
3. **Documentation** → Helps in maintaining the system over time.
4. **Analysis & Design** → Ensures a well-structured system before coding begins.

---

## **UML Diagrams in OOAD**

UML diagrams are divided into **Structural Diagrams** and **Behavioral Diagrams**.

### **A. Structural Diagrams** (Show the system's architecture)

#### **1. Class Diagram**

- Represents **classes, attributes, methods, and relationships** in the system.
- Shows **inheritance, associations, composition, and aggregation**.

🔹 **Example:** A **Bank Account** class with attributes (balance, account number) and methods (deposit, withdraw).

✅ **Use:** Helps in designing the system’s data structure.

#### **2. Object Diagram**

- Represents **real-world instances of classes** with specific data values.
- Similar to class diagrams but shows actual objects.

🔹 **Example:** An object of **Bank Account** class with specific values:

- Account No: **123456**
- Balance: **$5000**

✅ **Use:** Helps in understanding real-world implementation of classes.

#### **3. Deployment Diagram**

- Represents **hardware and software components** of the system.
- Shows **nodes (servers, databases, etc.) and connections** between them.

🔹 **Example:** A web-based application’s deployment with a **client, web server, and database server**.

✅ **Use:** Helps in understanding system deployment and infrastructure.

### **B. Behavioral Diagrams** (Show system behavior and workflows)

#### **4. Use Case Diagram**

- Represents **user interactions** with the system.
- Shows **actors (users, external systems) and use cases (system functions).**

🔹 **Example:** A **user placing an order** in an e-commerce system.

✅ **Use:** Helps in understanding **system functionality from a user perspective**.

#### **5. Activity Diagram**

- Represents **workflow and processes** in the system.
- Shows **decision points, loops, and parallel activities**.

🔹 **Example:** A **login process** with authentication steps.

✅ **Use:** Helps in understanding **business logic and process flow**.

#### **6. Sequence Diagram**

- Represents **interaction between objects over time**.
- Shows **message flow in a sequential order**.

🔹 **Example:** A **customer ordering a product** – involves user, order system, and payment gateway interactions.

✅ **Use:** Helps in designing **system interactions and message flow**.

#### **7. State Transition Diagram**

- Represents **states of an object and transitions between states**.
- Shows how an object behaves based on **events and conditions**.

🔹 **Example:** A **traffic light system** with states (Red, Yellow, Green) and transitions (Timer Expired).

✅ **Use:** Helps in designing **systems with multiple states and transitions**.

### **Conclusion**

- **UML diagrams** help in effectively designing, documenting, and understanding software systems.
- **Structural diagrams** define the architecture, while **behavioral diagrams** define interactions and workflows.
- **OOAD with UML** makes software development more structured and efficient.

---

## **`Gagan Saini`**
