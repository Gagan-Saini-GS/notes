# Unit-4

## **Software Project Planning & Software Cost Estimation**

Software Project Planning and Cost Estimation are crucial for the **successful execution of a software project**. They help in **resource allocation, risk management, timeline scheduling, and budgeting**.

### **Software Project Planning**

Software Project Planning is the **process of defining project goals, scope, schedule, resources, and risks** to ensure successful project completion.

### **Key Aspects of Project Planning**

#### **1. Project Scope**

- Defines the **boundaries** of the project.
- Includes **functional and non-functional requirements**.
- Helps in preventing **scope creep** (uncontrolled changes in requirements).

🔹 **Example:** An e-commerce project scope may include **user authentication, product catalog, payment gateway, and order tracking**.

#### **2. Work Breakdown Structure (WBS)**

- Divides the project into **smaller manageable tasks**.
- Helps in **assigning responsibilities and tracking progress**.

🔹 **Example:**  
For a **Hospital Management System**, WBS may include:

1. **Requirement Analysis**
2. **UI/UX Design**
3. **Database Development**
4. **Module Implementation (Patient, Doctor, Billing, etc.)**
5. **Testing & Deployment**

#### **3. Project Scheduling**

- Defines **when** each task should be completed.
- Uses **Gantt Charts, PERT (Program Evaluation Review Technique), and Critical Path Method (CPM)**.

🔹 **Example:**

- **Gantt Chart** shows tasks along a **timeline**.
- **CPM** identifies the **longest sequence of dependent tasks**.

✅ **Use:** Helps in meeting deadlines and avoiding delays.

#### **4. Resource Allocation**

- Assigns **human resources, hardware, and software** to different tasks.
- Ensures optimal **utilization of developers, testers, and designers**.

🔹 **Example:**

- **5 developers** for backend coding.
- **2 UI designers** for frontend work.

#### **5. Risk Management**

- Identifies **potential risks** (technical failures, budget overruns, delays).
- Creates **mitigation strategies** (backup plans, alternative technologies).

🔹 **Example:**  
Risk: **A key developer leaves the project.**  
Solution: **Have extra developers trained for backup.**

---

## **Software Cost Estimation**

Software Cost Estimation predicts the **effort, time, and cost** needed for software development.

### **1. Factors Affecting Cost Estimation**

- **Size of the software** (Small, Medium, Large).
- **Complexity** (Simple CRUD application vs AI-based software).
- **Technology used** (Open-source vs Paid tools).
- **Development team** (In-house vs Outsourced).

### **2. Cost Estimation Techniques**

#### **1. Expert Judgment**

- Based on experience and previous projects.
- **Pros:** Quick, useful for small projects.
- **Cons:** Can be biased or inaccurate.

#### **2. Algorithmic Models (COCOMO)**

COCOMO (**COnstructive COst MOdel**) estimates cost based on **project size and complexity**.

##### **COCOMO Types:**

- **Basic COCOMO** → Estimates effort based on lines of code (LOC).
- **Intermediate COCOMO** → Adds cost drivers (team experience, tools, etc.).
- **Detailed COCOMO** → Breaks project into **modules** and estimates cost for each.

🔹 **Example:**  
A **large banking system** may require **100,000 LOC**. COCOMO estimates **effort in person-months and cost**.

#### **3. Function Point Analysis (FPA)**

- Measures project size based on **functional features** (Inputs, Outputs, Queries, Files).
- **More accurate than LOC-based models** since it **doesn’t depend on coding style**.

🔹 **Example:**

- **Login system** (2 function points).
- **Order processing** (5 function points).
- **Payment processing** (8 function points).
- Total: **15 function points → Estimated cost based on complexity.**

#### **4. Use-Case Based Estimation**

- Estimates cost by analyzing **use cases** (User interactions with the system).
- Helps in estimating based on **real-world scenarios**.

🔹 **Example:**  
For an **Online Shopping System**:

1. **Customer browses products** → 3 points
2. **Customer adds items to cart** → 5 points
3. **Customer completes payment** → 8 points

- Total complexity = **16 points** → Used for cost estimation.

### **Conclusion**

- **Software Project Planning** ensures the **successful execution of a project** by defining **scope, schedule, and resources**.
- **Software Cost Estimation** helps in predicting the **budget and effort needed** for development using techniques like **COCOMO, Function Point Analysis, and Expert Judgment**.

---

## **Software Project Management Topics**

### **1. Business Case**

A **Business Case** justifies why a project should be initiated by evaluating its **benefits, costs, and risks**. It helps stakeholders decide whether the project is **worth investing in**.

#### **Key Components of a Business Case:**

1. **Executive Summary** → Brief overview of the project.
2. **Problem Statement** → What problem the project aims to solve.
3. **Proposed Solution** → How the software will address the problem.
4. **Benefits & Value** → Business advantages (cost reduction, efficiency, revenue growth).
5. **Cost Estimation** → Budget and funding requirements.
6. **Risk Analysis** → Potential risks and mitigation strategies.
7. **Recommendations** → Final decision on whether to proceed.

✅ **Example:**  
A company considering an **automated payroll system** would create a business case showing **how automation reduces errors, saves time, and improves compliance**.

### **2. Project Selection and Approval**

Once multiple project proposals exist, organizations must **select and approve** the most beneficial project.

#### **Selection Criteria:**

- **Strategic Alignment** → Does the project align with company goals?
- **Financial Feasibility** → ROI (Return on Investment), NPV (Net Present Value).
- **Risk Assessment** → High-risk vs. low-risk projects.
- **Market Demand** → Customer needs and industry trends.
- **Technical Feasibility** → Available resources and technology compatibility.

#### **Project Selection Methods:**

1. **Benefit Measurement Methods:**

   - **Cost-Benefit Analysis (CBA)** → Compares expected costs vs. benefits.
   - **Scoring Models** → Assigns scores based on multiple criteria.
   - **Payback Period** → Time taken to recover initial investment.

2. **Mathematical Models:**
   - **Linear Programming, Decision Trees, or Economic Models** for complex decisions.

✅ **Example:**  
A company deciding between **Developing a new e-commerce platform vs. Upgrading an existing system** might use **CBA & Risk Analysis** to choose the best option.

### **3. Project Charter**

A **Project Charter** is a formal document that **authorizes** the project and outlines its **objectives, scope, stakeholders, and deliverables**.

#### **Key Components of a Project Charter:**

1. **Project Title & Description** → Brief summary.
2. **Objectives** → What the project aims to achieve.
3. **Scope** → Boundaries of the project (what is included/excluded).
4. **Stakeholders** → People involved (Project Manager, Clients, Developers).
5. **Budget & Timeline** → Estimated cost and project duration.
6. **Risks & Assumptions** → Potential risks and key assumptions.
7. **Approval Authority** → Who authorizes the project (Sponsor, CEO).

✅ **Example:**  
A **Project Charter for a Mobile Banking App** would include:

- Objective: **Develop a secure mobile banking application**.
- Scope: **Features like account management, fund transfers, and bill payments**.
- Budget: **$500,000**.
- Timeline: **6 months**.
- Stakeholders: **Banking Executives, Developers, Customers**.

### **4. Project Scope Management**

**Project Scope Management** ensures the project stays within its **defined boundaries** and avoids unnecessary changes.

#### **Key Components of Scope Management:**

1. **Scope Planning** → Defining how scope will be managed.
2. **Scope Definition** → Documenting project deliverables.
3. **Work Breakdown Structure (WBS)** → Breaking down tasks into smaller parts.
4. **Scope Verification** → Ensuring all deliverables are met.
5. **Scope Control** → Managing changes to prevent **scope creep**.

✅ **Example:**  
For an **E-commerce Website**, the scope may include:

- **Included**: User registration, shopping cart, payment integration.
- **Excluded**: AI-based recommendations, social media integration.

📌 **Importance of Scope Management:**

- Prevents **delays and budget overruns**.
- Ensures **clear expectations** between teams.
- Helps in **tracking project progress efficiently**.

### **Conclusion**

- **Business Case** justifies why a project should start.
- **Project Selection & Approval** ensures the most valuable project is chosen.
- **Project Charter** formally authorizes the project.
- **Project Scope Management** ensures the project stays on track.

---

## **Work Breakdown Structure (WBS) & Software Estimation**

### **1. Work Breakdown Structure (WBS)**

A **Work Breakdown Structure (WBS)** is a hierarchical decomposition of a project into **smaller, manageable tasks**. It helps in **planning, resource allocation, and tracking progress**.

### **Key Characteristics of WBS:**

✅ **Hierarchical** → Breaks the project into levels.  
✅ **Deliverable-Oriented** → Focuses on project outputs.  
✅ **Measurable** → Each task has a clear completion point.

---

### **1.1. Levels of WBS**

A typical WBS has **four levels**:

1. **Level 1: Project Name** → The entire project.
2. **Level 2: Major Phases** → Key stages (e.g., Requirements, Design, Development).
3. **Level 3: Subtasks** → More detailed work units under each phase.
4. **Level 4: Work Packages** → Smallest tasks that can be assigned and tracked.

📌 **Example: WBS for an E-commerce Website**

| **Level 1**            | **Level 2**          | **Level 3**                | **Level 4**         |
| ---------------------- | -------------------- | -------------------------- | ------------------- |
| **E-commerce Website** | Requirement Analysis | Gather Client Requirements | Conduct Meetings    |
|                        |                      | Define System Scope        | Identify Features   |
|                        | Design               | UI/UX Prototyping          | Create Wireframes   |
|                        |                      | Database Design            | ER Diagrams         |
|                        | Development          | Backend Development        | Payment Integration |
|                        | Testing              | Functional Testing         | Test Payment System |
|                        | Deployment           | Deploy on Server           | Domain Setup        |

✅ **Use of WBS:**

- Helps in **budgeting, scheduling, and tracking progress**.
- Improves **task delegation and accountability**.
- Reduces the risk of **missed tasks and scope creep**.

---

## **2. Software Estimation**

Software estimation predicts **effort, time, and cost** for software development.

### **2.1. Size Estimation using Function Point Analysis (FPA)**

**Function Point Analysis (FPA)** measures the size of a software system based on **functional components** instead of lines of code (LOC).

📌 **Why Use Function Points?**

- Language-independent (unlike LOC).
- Better for estimating effort and productivity.
- Useful for early-stage project estimation.

---

### **2.2. Function Point Calculation**

Function Points (FP) are calculated using the formula:

` {FP} =  {UFP} X  {VAF}`

Where:

- **UFP (Unadjusted Function Points)** = Sum of function component weights.
- **VAF (Value Adjustment Factor)** = 0.65 + (0.01 × Total Complexity Factors).

---

### **Step 1: Identify Function Components**

FPA classifies system functionalities into **five categories**:

| **Function Type**                  | **Example**                   | **Complexity (Low/Avg/High)** | **Weights**                  |
| ---------------------------------- | ----------------------------- | ----------------------------- | ---------------------------- |
| **External Inputs (EI)**           | User enters login credentials | 3 / 4 / 6                     | Low = 3, Avg = 4, High = 6   |
| **External Outputs (EO)**          | System generates reports      | 4 / 5 / 7                     | Low = 4, Avg = 5, High = 7   |
| **External Inquiries (EQ)**        | User searches for a product   | 3 / 4 / 6                     | Low = 3, Avg = 4, High = 6   |
| **Internal Logical Files (ILF)**   | Customer database             | 7 / 10 / 15                   | Low = 7, Avg = 10, High = 15 |
| **External Interface Files (EIF)** | Payment Gateway API           | 5 / 7 / 10                    | Low = 5, Avg = 7, High = 10  |

---

### **Step 2: Calculate Unadjusted Function Points (UFP)**

Let’s assume an **E-commerce System** has the following function counts:

| **Function Type**              | **Count** | **Complexity (Avg)** | **Weight** | **Total FP**    |
| ------------------------------ | --------- | -------------------- | ---------- | --------------- |
| External Inputs (EI)           | 5         | Avg                  | 4          | **5 × 4 = 20**  |
| External Outputs (EO)          | 3         | Avg                  | 5          | **3 × 5 = 15**  |
| External Inquiries (EQ)        | 4         | Avg                  | 4          | **4 × 4 = 16**  |
| Internal Logical Files (ILF)   | 2         | Avg                  | 10         | **2 × 10 = 20** |
| External Interface Files (EIF) | 1         | Avg                  | 7          | **1 × 7 = 7**   |

🔹 **Unadjusted Function Points (UFP) = 20 + 15 + 16 + 20 + 7 = 78**

---

### **Step 3: Calculate Value Adjustment Factor (VAF)**

VAF is determined based on **14 general system characteristics (GSCs)** (e.g., performance, complexity, reusability). Each factor is rated from **0 to 5**.

` {VAF} = 0.65 + (0.01 X  {Total GSC Score})`

Assume Total GSC Score = **40**, then:

` {VAF} = 0.65 + (0.01 X 40) = 1.05`

---

### **Step 4: Compute Final Function Points (FP)**

` {FP} =  {UFP} X {VAF} = 78 X 1.05 = 81.9`

🔹 **Final Function Points ≈ 82**

---

### **2.3. Effort Estimation using Function Points**

Effort can be estimated using the formula:

` {Effort (Person-Months)} =  {Function Points} X {Productivity Factor}`

Assume **Productivity Factor = 1.5** (based on industry data), then:

` {Effort} = 82 X 1.5 = 123  { person-months}`

---

### **Conclusion**

- **WBS** helps in breaking the project into manageable parts for better execution.
- **Function Point Analysis** provides an **accurate size estimation** independent of programming language.
- **Effort estimation** helps in **budgeting and scheduling software projects effectively**.

---

## **Cost Estimation: COCOMO & COCOMO-II (Numericals)**

Cost estimation helps in predicting the **effort, time, and cost** required for software development.

### **1. COCOMO (Constructive Cost Model) - Basic Model**

COCOMO estimates effort based on **Lines of Code (LOC)** and classifies projects into three categories:

| **Project Type**  | **Description**              | **Examples**                       |
| ----------------- | ---------------------------- | ---------------------------------- |
| **Organic**       | Small teams, simple projects | Payroll System, Inventory System   |
| **Semi-Detached** | Medium complexity            | Banking Software, ERP System       |
| **Embedded**      | Highly complex, real-time    | Military Systems, AI-based systems |

#### **1.1. COCOMO Basic Model Formula**

The **effort (E)** required for a software project is given by:

`E = a(KLOC)^b`

Where:

- **KLOC** = Thousand Lines of Code
- **a, b** = Constants based on project type

Once effort is calculated, development time (**T**) is estimated using:

`T = c(E)^d`

Where:

- **c, d** = Constants based on project type

#### **1.2. COCOMO Constants Table**

| **Project Type**  | **a** | **b** | **c** | **d** |
| ----------------- | ----- | ----- | ----- | ----- |
| **Organic**       | 2.4   | 1.05  | 2.5   | 0.38  |
| **Semi-Detached** | 3.0   | 1.12  | 2.5   | 0.35  |
| **Embedded**      | 3.6   | 1.20  | 2.5   | 0.32  |

#### **1.3. COCOMO Numerical Example**

**Example 1: Estimating Effort & Development Time**

A **Payroll Management System** requires **40,000 LOC (40 KLOC)**. It is an **Organic** project.

Using COCOMO basic model:

`E = 2.4 (40)^{1.05}`

`E = 2.4 X 44.68`

`E ≈ 107.2 { Person-Months}`

Now, calculate Development Time (**T**):

`T = 2.5 (107.2)^{0.38}`

`T = 2.5 X 8.26`

`T ≈ 20.65 { months}`

✅ **Final Estimate:**

- **Effort:** 107.2 **Person-Months**
- **Development Time:** 20.65 **months**

### **2. COCOMO-II (Early Design Model)**

COCOMO-II improves upon the basic COCOMO model by considering **multiple cost drivers** and is used for modern software projects.

COCOMO-II has **three models**:

1. **Application Composition Model** → Used for **rapid development** with high reuse.
2. **Early Design Model** → Used in the **initial planning phase** (Estimates based on Function Points).
3. **Post-Architecture Model** → Used in the **detailed design phase** with full cost drivers.

#### **2.1. COCOMO-II Early Design Model Formula**

`E = A X (KLOC)^{B} X \prod EM_i`

Where:

- **A = 2.94** (Constant)
- **B** = Scaling Factor (Usually **1.1 - 1.2**)
- **EM** = Effort Multipliers (Cost drivers like complexity, experience, reliability)

#### **2.2. COCOMO-II Early Design Model Numerical Example**

**Example 2: Estimating Effort using COCOMO-II Early Design Model**

A **Banking System** has **50 KLOC** and the following cost drivers:

- **Complexity (EM1) = 1.3**
- **Experience Factor (EM2) = 0.9**
- **Required Reliability (EM3) = 1.2**

Using **B = 1.12**, calculate **Effort (E)**:

`E = 2.94 X (50)^{1.12} X (1.3 X 0.9 X 1.2)`

`E = 2.94 X 60.22 X 1.404`

`E = 2.94 X 84.54`

`E ≈ 248.55 { Person-Months}`

✅ **Final Estimate:**

- **Effort:** 248.55 **Person-Months**

### **Comparison: COCOMO vs COCOMO-II**

| **Factor**                 | **COCOMO**                       | **COCOMO-II**                                |
| -------------------------- | -------------------------------- | -------------------------------------------- |
| **Project Classification** | Organic, Semi-Detached, Embedded | Application, Early Design, Post-Architecture |
| **Formula Type**           | Simple                           | More Detailed                                |
| **Effort Multipliers**     | No                               | Yes                                          |
| **Used For**               | Legacy Systems                   | Modern Software                              |

### **Conclusion**

- **COCOMO Basic Model** is useful for **quick estimation** based on LOC.
- **COCOMO-II Early Design Model** improves accuracy by considering **cost drivers**.
- **Numericals help** in real-world project estimation.

---

## **`Gagan Saini`**
