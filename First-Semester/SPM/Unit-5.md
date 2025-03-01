# Unit-5

## **Project Scheduling and Procurement Management in Software Project Management**

In software project management, **Project Scheduling** and **Procurement Management** are two critical components that ensure a project's timely completion and efficient resource utilization. Here's an overview of each:

### **1. Project Scheduling**

Project scheduling involves defining tasks, allocating resources, setting timelines, and ensuring that all project activities are completed within the planned timeframe. It is a core aspect of **Project Planning** and plays a crucial role in managing software development life cycles.

#### **Key Aspects of Project Scheduling:**

1. **Work Breakdown Structure (WBS):**

   - Decomposing the project into smaller, manageable tasks.
   - Organizing tasks hierarchically for better tracking.

2. **Task Dependencies:**

   - Identifying dependencies between tasks (e.g., Task B starts only after Task A is completed).
   - Types of dependencies: Finish-to-Start (FS), Start-to-Start (SS), etc.

3. **Estimating Task Duration:**

   - Using techniques like expert judgment, historical data, and estimation models (COCOMO, Function Points).
   - Applying estimation techniques like **PERT (Program Evaluation and Review Technique)** and **Critical Path Method (CPM).**

4. **Resource Allocation:**

   - Assigning developers, testers, designers, and other team members to specific tasks.
   - Balancing workloads to avoid resource overutilization.

5. **Scheduling Tools & Techniques:**

   - **Gantt Charts:** Visual timeline of project activities.
   - **PERT/CPM:** Used to analyze the critical path and project duration.
   - **Agile and Scrum Frameworks:** Iterative and flexible scheduling approaches.

6. **Risk Management in Scheduling:**
   - Identifying potential risks that can delay the project.
   - Implementing mitigation strategies like buffer time and alternate task assignments.

### **2. Procurement Management**

Procurement Management deals with acquiring external products, services, and resources required for project execution. In software development, procurement can include software licenses, cloud services, development tools, and outsourced services.

#### **Key Aspects of Procurement Management:**

1. **Procurement Planning:**

   - Identifying project needs and determining what to purchase externally.
   - Deciding on procurement methods (buy vs. build decision).

2. **Vendor Selection and Contracting:**

   - Evaluating vendors based on cost, reliability, and quality.
   - Negotiating contracts and service-level agreements (SLAs).

3. **Procurement Execution:**

   - Managing the procurement lifecycle, including ordering, invoicing, and delivery.
   - Ensuring compliance with contract terms.

4. **Monitoring and Control:**

   - Tracking vendor performance and service delivery.
   - Managing changes in procurement requirements.

5. **Procurement Closure:**
   - Verifying that all contractual obligations have been met.
   - Completing payments and closing procurement contracts.

### **Integration of Project Scheduling and Procurement Management**

- Timely procurement ensures that resources (software, hardware, third-party services) are available as per the schedule.
- Delays in procurement can impact project schedules and lead to missed deadlines.
- Close coordination between project managers and procurement teams is essential for smooth execution.

### **Conclusion**

Project Scheduling and Procurement Management are interconnected processes in software project management. Proper planning, tracking, and risk management in these areas help ensure the successful delivery of software projects within scope, budget, and timeline.

---

## Relationship b/w People

The **relationship between people in software project management** is crucial for the success of a project. Effective collaboration, communication, and teamwork among stakeholders ensure that projects are delivered on time, within budget, and with the desired quality. Here’s how different relationships impact project success:

### **1. Project Manager and Team Members**

- The **Project Manager (PM)** leads the software team, assigns tasks, and ensures the project stays on track.
- The PM must maintain a **balance between leadership and collaboration** to keep team members motivated and productive.
- Frequent **status meetings, one-on-one check-ins, and performance feedback** help maintain a healthy relationship.

### **2. Developers and QA/Testers**

- Developers and **Quality Assurance (QA) teams** must work closely to identify and fix software bugs.
- A **collaborative relationship** between these groups ensures **faster debugging and smoother releases**.
- Agile methodologies like **Scrum** promote continuous integration and communication between developers and testers.

### **3. Clients and Project Team**

- The project team must **understand client expectations** and ensure that software meets business needs.
- **Clear communication, requirement gathering, and regular updates** are essential for a strong client-team relationship.
- Misunderstandings or lack of engagement can lead to scope creep and dissatisfaction.

### **4. Stakeholders and Project Team**

- Stakeholders (executives, investors, or business units) influence project priorities and funding.
- The project manager acts as a **bridge between stakeholders and the team**, ensuring business objectives align with technical execution.
- **Regular progress reports and stakeholder meetings** keep everyone aligned.

### **5. Cross-Functional Teams** (e.g., UI/UX Designers, DevOps, Security, Marketing)

- Software projects often involve multiple departments like **UI/UX designers, DevOps engineers, security teams, and marketing teams**.
- Effective **cross-team communication and collaboration tools** (like Jira, Slack, and Confluence) ensure smooth integration between different roles.

### **6. Vendors and Project Team (Procurement Relationship)**

- Vendors provide **software tools, cloud services, or outsourced development**.
- Strong relationships with vendors ensure **timely delivery, cost control, and quality compliance**.
- Contracts and service-level agreements (SLAs) define clear expectations between both parties.

### **7. Leadership and Teams (Organizational Culture)**

- A **positive work culture** leads to **higher employee satisfaction and better project outcomes**.
- Leadership must **support innovation, provide career growth opportunities, and resolve conflicts effectively**.
- Strong leadership fosters **trust and motivation**, driving teams to deliver their best work.

### **Conclusion**

Successful software projects depend on strong interpersonal relationships. **Clear communication, collaboration, and trust** among all stakeholders—developers, testers, managers, clients, and vendors—are critical for smooth project execution.

---

## **Effort & Scheduling in Software Project Management**

Effort estimation, staffing levels, and schedule management are crucial for **on-time and within-budget software project delivery**. Here’s an in-depth look at these topics with a numerical example for **Critical Path Method (CPM).**

### **1. Staffing Level Estimation**

Staffing level estimation ensures that the right number of personnel is allocated at different project stages.

#### **Techniques for Staffing Estimation:**

1. **Putnam-Norden-Rayleigh Curve** – Describes how staffing levels vary over time.
2. **COCOMO Model (Constructive Cost Model)** – Uses software size (in KLOC) to estimate effort.
3. **Expert Judgment** – Based on past projects and experience.

📌 **Example Formula (Putnam Model):**  
`Effort (E) = ((K X Size)^3/2) / (T^4)`

where:

- **Effort (E)** = person-months
- **Size** = estimated software size (KLOC)
- **T** = project duration in months
- **K** = productivity factor

### **2. Effect of Schedule Change on Cost**

- Reducing the schedule **increases cost** due to overtime, increased resource allocation, and inefficiencies.
- Extending the schedule **may reduce productivity** and increase overhead costs.

📌 **Example:**

- A project originally estimated at **6 months** with a cost of **$500,000** is compressed to **4 months**.
- The cost may increase due to **additional hiring, training, or overtime pay** to meet deadlines.
- The new cost could rise to **$650,000-$700,000**, depending on factors like resource availability.

**Brook’s Law:**  
_"Adding more people to a late project makes it later."_ – More people require training, increasing communication overhead.

### **3. Project Schedule**

A project schedule outlines tasks, dependencies, milestones, and deadlines.

#### **Key Scheduling Tools:**

- **Gantt Charts** – Timeline view of tasks.
- **PERT (Program Evaluation and Review Technique)** – Estimates time using optimistic, pessimistic, and most likely estimates.
- **CPM (Critical Path Method)** – Determines the longest path in a project to identify the minimum project duration.

### **4. Schedule Control**

Schedule control ensures that a project stays on track.

#### **Methods to Maintain Schedule:**

1. **Regular Progress Tracking** – Using software like **JIRA, MS Project, or Trello**.
2. **Variance Analysis** – Comparing actual vs. planned progress.
3. **Risk Mitigation** – Identifying risks early and adjusting schedules.
4. **Fast Tracking** – Running tasks in parallel to reduce schedule length.
5. **Crashing** – Adding extra resources to speed up critical tasks.

### **5. Critical Path Method (CPM) – Numerical Example**

The **Critical Path Method (CPM)** is used to determine the **longest** path through a project, which defines the shortest possible completion time.

📌 **Example:**
Consider a software project with the following tasks and dependencies:

| Task | Duration (Days) | Dependencies |
| ---- | --------------- | ------------ |
| A    | 4               | -            |
| B    | 5               | A            |
| C    | 6               | A            |
| D    | 3               | B            |
| E    | 2               | B, C         |
| F    | 4               | D            |
| G    | 3               | E, F         |

#### **Step 1: Identify Paths**

- **Path 1:** A → B → D → F → G = **4 + 5 + 3 + 4 + 3 = 19 days**
- **Path 2:** A → B → E → G = **4 + 5 + 2 + 3 = 14 days**
- **Path 3:** A → C → E → G = **4 + 6 + 2 + 3 = 15 days**

#### **Step 2: Find Critical Path**

- The longest path is **A → B → D → F → G** (19 days).
- This is the **Critical Path**, meaning the project cannot be completed in less than **19 days**.

#### **Step 3: Slack Calculation**

- Slack (or float) is the time a task can be delayed without delaying the project.
- **Tasks on the Critical Path have zero slack**.

### **Conclusion**

- Staffing estimation ensures adequate resource allocation.
- Schedule changes affect costs significantly.
- Project scheduling tools like Gantt Charts, PERT, and CPM are essential.
- Schedule control keeps projects on track through monitoring and adjustments.
- CPM helps determine the shortest project duration.

---

## **Basics of Procurement Management & Change Management in Software Project Management**

Procurement Management and Change Management are two crucial aspects of software project management. **Procurement Management** ensures that all external resources (hardware, software, services) are acquired efficiently, while **Change Management** ensures that project changes are handled systematically to minimize risks and disruptions.

### **1. Procurement Management in Software Projects**

#### **Definition:**

Procurement Management is the process of acquiring external resources, such as software tools, hardware, cloud services, third-party development, or consulting services, required for project execution.

#### **Key Components of Procurement Management:**

1. **Procurement Planning:**

   - Identifying what needs to be procured externally.
   - Deciding whether to **buy or build** a software component.
   - Creating a procurement schedule.

2. **Vendor Selection & Contracting:**

   - Evaluating vendors based on **cost, quality, reputation, and timelines**.
   - Negotiating terms and signing **contracts or Service-Level Agreements (SLAs)**.

3. **Procurement Execution:**

   - Issuing purchase orders and tracking deliveries.
   - Ensuring compliance with contractual agreements.

4. **Monitoring and Control:**

   - Tracking vendor performance and resolving issues.
   - Managing risks related to procurement delays or failures.

5. **Procurement Closure:**
   - Verifying that all deliverables meet requirements.
   - Closing contracts and making final payments.

#### **Example:**

A software company outsourcing **UI/UX design** to a third-party vendor must:

- Define the **scope of work** and timelines.
- Select a vendor with relevant experience.
- Establish an SLA for deliverables and quality standards.
- Monitor progress and ensure adherence to deadlines.

### **2. Change Management in Software Projects**

#### **Definition:**

Change Management is the structured approach to managing changes in project scope, schedule, or requirements while minimizing disruptions and risks.

#### **Key Components of Change Management:**

1. **Identifying Change:**

   - A change request can come from **clients, stakeholders, or development teams** due to evolving business needs or new technology.

2. **Impact Analysis:**

   - Assessing how the change affects **cost, timeline, scope, and risks**.
   - Analyzing dependencies on existing tasks and resources.

3. **Approval or Rejection:**

   - The **Change Control Board (CCB)** or project manager evaluates and approves/rejects the change.

4. **Change Implementation:**

   - Updating project plans, timelines, and budgets.
   - Communicating changes to the team and stakeholders.

5. **Monitoring & Evaluation:**
   - Ensuring successful integration of the change.
   - Reviewing project progress after the change is implemented.

#### **Example:**

A client requests an **additional feature in a mobile app** after development has started.

- The team evaluates the impact on **cost and delivery date**.
- The **Change Control Board** decides whether to accept the change.
- If approved, the **development schedule is adjusted**, and resources are reallocated.

### **Conclusion**

- **Procurement Management ensures timely acquisition of external resources**, preventing project delays.
- **Change Management helps projects adapt to new requirements** while controlling risks and maintaining quality.

---

## **Software Risk Management in IT Projects**

Software Risk Management is essential in **IT projects** to identify potential risks, analyze their impact, develop strategies to mitigate them, and monitor their effects throughout the project lifecycle. Below is a structured approach to managing risks in software projects.

### **1. Identifying IT Project Risks**

Risk identification involves recognizing potential problems that could **delay, increase cost, or cause project failure**.

#### **Types of Risks in IT Projects:**

1. **Technical Risks:**

   - Unstable technologies or new frameworks.
   - Integration issues with existing systems.
   - Performance or scalability problems.

2. **Project Management Risks:**

   - Poor scheduling or unrealistic deadlines.
   - Inaccurate effort estimation.
   - Resource allocation issues.

3. **Operational Risks:**

   - Lack of skilled personnel.
   - Inefficient communication among teams.
   - Infrastructure failures (server downtime, power outages).

4. **External Risks:**

   - Vendor or third-party service failures.
   - Regulatory compliance changes.
   - Economic or market fluctuations.

5. **Security Risks:**
   - Cyber threats (hacking, data breaches).
   - Unauthorized access or software vulnerabilities.
   - Compliance issues (GDPR, HIPAA).

### **2. Risk Analysis and Assessment**

Once risks are identified, they must be **analyzed** and **assessed** based on their likelihood and impact.

#### **Risk Assessment Matrix:**

| **Risk**         | **Probability (Low, Medium, High)** | **Impact (Low, Medium, High)** | **Priority (High, Medium, Low)** |
| ---------------- | ----------------------------------- | ------------------------------ | -------------------------------- |
| Scope Creep      | High                                | High                           | High                             |
| Server Downtime  | Medium                              | High                           | High                             |
| Skill Shortage   | High                                | Medium                         | Medium                           |
| Security Threats | Low                                 | High                           | Medium                           |

#### **Qualitative vs. Quantitative Analysis**

- **Qualitative Risk Analysis:** Categorizing risks based on probability and impact (low, medium, high).
- **Quantitative Risk Analysis:** Using statistical models to determine numerical risk values (e.g., Monte Carlo simulation).

### **3. Risk Strategies (Risk Mitigation Plans)**

After assessment, a **risk response plan** must be created.

#### **Common Risk Handling Strategies:**

1. **Risk Avoidance:**

   - Changing project scope or technology to eliminate risks.
   - Example: Avoiding outdated software libraries.

2. **Risk Mitigation:**

   - Reducing the probability or impact of risks.
   - Example: Using **prototyping** to reduce uncertainties in software requirements.

3. **Risk Transfer:**

   - Shifting risks to third parties (e.g., outsourcing security management).
   - Example: Purchasing **cybersecurity insurance**.

4. **Risk Acceptance:**
   - Accepting risks when mitigation is too costly or impractical.
   - Example: Accepting minor UI bugs that do not impact functionality.

### **4. Risk Monitoring and Control**

Risk Monitoring ensures that identified risks are tracked throughout the project lifecycle.

#### **Steps in Risk Monitoring:**

- Conduct **regular risk assessments** and updates.
- Use **KPIs (Key Performance Indicators)** to track risk levels.
- Maintain a **Risk Register** (a document tracking risk status).
- Use **Risk Heat Maps** to visualize critical risks.

#### **Tools for Risk Monitoring:**

- **JIRA / Trello** – Track project risks and issues.
- **Microsoft Project / Smartsheet** – Monitor schedule risks.
- **SIEM (Security Information and Event Management)** – Detect security threats.

### **5. Risk Response and Evaluation**

After risks are handled, they must be **evaluated for effectiveness**.

#### **Post-Risk Evaluation Strategies:**

1. **Conduct Lessons Learned Meetings:**

   - Identify what worked and what failed in risk handling.

2. **Adjust Future Risk Management Plans:**

   - Improve risk response based on past experiences.

3. **Update Documentation:**

   - Maintain records for future projects.

4. **Implement Preventive Actions:**
   - Introduce new security policies, better communication strategies, or enhanced testing procedures.

### **Conclusion**

Effective **risk management in software projects** ensures smooth execution by proactively identifying, analyzing, mitigating, and monitoring risks. A **structured approach** improves project success rates and minimizes financial or operational losses.

---

## **`Gagan Saini`**
