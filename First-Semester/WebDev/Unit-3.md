# Unit-3

## Open Source

An **open-source framework** is a software framework whose **source code is freely available** for anyone to use, modify, and distribute. These frameworks provide a foundation for developing applications by offering pre-written code, libraries, and tools to simplify development.

### **Key Features of Open-Source Frameworks:**

1. **Free to Use** – No licensing costs.
2. **Community-Driven** – Developed and maintained by a community of developers.
3. **Customizable** – Developers can modify the source code to fit their needs.
4. **Regular Updates** – Continuous improvements and security fixes by contributors.
5. **Collaborative Development** – Contributions from developers worldwide enhance the framework.

### **Examples of Open-Source Frameworks:**

- **Web Development:**
  - **React.js** (JavaScript library for UI)
  - **Angular** (JavaScript framework by Google)
  - **Django** (Python-based web framework)
- **Mobile App Development:**
  - **Flutter** (Dart-based UI toolkit by Google)
  - **React Native** (JavaScript framework for cross-platform apps)
- **Backend Development:**
  - **Spring Boot** (Java framework for web applications)
  - **Express.js** (Minimalist Node.js framework)
  - **Ruby on Rails** (Ruby-based web framework)
- **Machine Learning & Data Science:**
  - **TensorFlow** (Machine learning framework by Google)
  - **PyTorch** (Deep learning framework by Meta)

---

## Open Source Frameworks

### **1. Web Development Frameworks**

#### **1.1 React.js** (JavaScript)

- Developed by **Meta (Facebook)**
- Component-based UI library
- Virtual DOM for fast rendering
- Strong ecosystem (Next.js, Redux)
- Supports **React Native** for mobile

#### **1.2 Angular** (TypeScript)

- Developed by **Google**
- Two-way data binding
- MVC (Model-View-Controller) architecture
- Dependency injection
- Built-in testing tools

#### **1.3 Vue.js** (JavaScript)

- Progressive framework
- Lightweight and flexible
- Two-way data binding
- Component-based architecture
- Simple learning curve

### **2. Backend Development Frameworks**

#### **2.1 Node.js + Express.js** (JavaScript)

- Asynchronous, event-driven model
- Lightweight and fast
- REST API & WebSocket support
- Middleware support
- Huge npm ecosystem

#### **2.2 Django** (Python)

- Follows the **MTV (Model-Template-View)** pattern
- **"Batteries included"** – built-in admin, authentication, ORM
- Highly secure
- Scalable and SEO-friendly

#### **2.3 Spring Boot** (Java)

- Microservices-friendly
- Embedded servers (Tomcat, Jetty)
- Dependency injection
- Powerful security features
- Easy integration with databases

### **3. Mobile App Development Frameworks**

#### **3.1 Flutter** (Dart)

- Developed by **Google**
- **Single codebase** for iOS, Android, Web
- Fast UI with **Skia rendering engine**
- Hot reload for quick development
- Rich UI components

#### **3.2 React Native** (JavaScript)

- Developed by **Meta (Facebook)**
- Uses React.js for mobile
- Native-like performance
- Large community support
- Modular and reusable components

### **4. Machine Learning & AI Frameworks**

#### **4.1 TensorFlow** (Python/C++)

- Developed by **Google**
- High-performance deep learning
- Supports **GPU/TPU acceleration**
- TensorBoard for visualization
- Compatible with mobile and web

#### **4.2 PyTorch** (Python)

- Developed by **Meta (Facebook)**
- Dynamic computation graphs
- Easy debugging
- Strong support for NLP and vision tasks
- Widely used in research

### **5. Cybersecurity & Penetration Testing Frameworks**

#### **5.1 Metasploit**

- Penetration testing tool
- Exploits and payloads for ethical hacking
- Post-exploitation modules
- Large security community

#### **5.2 OSSEC**

- Open-source **intrusion detection system (IDS)**
- Log analysis & monitoring
- File integrity checking
- Active response to threats

---

## **Open-Source Server-Side Web Development Framework – .NET**

**.NET** (previously known as .NET Core) is a **cross-platform, open-source** server-side web development framework developed by **Microsoft**. It is widely used to build **scalable, high-performance web applications**, APIs, microservices, and cloud-based solutions.

### **Key Features of .NET Framework for Server-Side Web Development**

#### **1. Cross-Platform & Open Source**

- .NET is **open-source** and hosted on [GitHub](https://github.com/dotnet).
- It runs on **Windows, Linux, and macOS**, making it highly flexible for deployment.

#### **2. High Performance**

- Optimized for **speed and scalability**, making it one of the fastest web frameworks.
- Uses **Kestrel web server**, which is lightweight and faster than IIS.
- **Ahead-of-Time (AOT) Compilation** improves runtime performance.

#### **3. Supports Multiple Programming Languages**

- Primarily uses **C#**, but also supports **F#** and **VB.NET**.

#### **4. MVC Architecture (ASP.NET Core)**

- **Model-View-Controller (MVC)** pattern helps in organizing code for better maintainability.
- Supports **RESTful APIs, WebSockets, and GraphQL** for modern web applications.

#### **5. Dependency Injection (DI) Built-In**

- Improves **modular design** and testability.
- Automatically manages **service lifetimes**.

#### **6. Microservices & Cloud-Native Development**

- Ideal for **containerized applications** using **Docker** and **Kubernetes**.
- Seamless integration with **Microsoft Azure** and **AWS**.

#### **7. Security Features**

- Built-in support for **authentication and authorization**.
- **Identity Server** for **OAuth 2.0, OpenID Connect, and JWT authentication**.
- Protection against **XSS, CSRF, and SQL Injection**.

#### **8. Integrated with Entity Framework Core (EF Core)**

- **ORM (Object-Relational Mapping)** for database interactions.
- Supports **SQL Server, MySQL, PostgreSQL, and NoSQL databases**.

#### **9. SignalR for Real-Time Applications**

- Enables **real-time communication** (like chat apps, live notifications).
- Uses **WebSockets** and **long polling** for fast data exchange.

#### **10. Razor Pages for Simpler Web Apps**

- A lightweight alternative to MVC for building web pages quickly.

### **Popular Use Cases of .NET Framework**

✔️ **Enterprise Web Applications** (e.g., Banking, Healthcare, CRM)  
✔️ **E-Commerce Websites** (e.g., Shopify, Magento alternatives)  
✔️ **RESTful APIs & Microservices**  
✔️ **Cloud-Based Applications** (Microsoft Azure, AWS)  
✔️ **Real-Time Web Applications** (e.g., Chat, Notifications)  
✔️ **IoT Applications** (works well with Raspberry Pi, Azure IoT)

### **Comparison: .NET vs Other Server-Side Frameworks**

| Feature                   | .NET Core      | Node.js        | Django         | Spring Boot    |
| ------------------------- | -------------- | -------------- | -------------- | -------------- |
| **Performance**           | 🚀 Very High   | 🔥 High        | ⚡ Medium      | 🚀 Very High   |
| **Cross-Platform**        | ✅ Yes         | ✅ Yes         | ✅ Yes         | ✅ Yes         |
| **Microservices Support** | ✅ Strong      | ✅ Yes         | ⚠️ Limited     | ✅ Strong      |
| **Security**              | 🔐 Strong      | 🛑 Moderate    | 🔐 Strong      | 🔐 Strong      |
| **Database Support**      | ✅ SQL & NoSQL | ✅ SQL & NoSQL | ✅ SQL & NoSQL | ✅ SQL & NoSQL |
| **Ease of Learning**      | 🟠 Medium      | 🟢 Easy        | 🟠 Medium      | 🔴 Hard        |

### **Example: Simple ASP.NET Core Web API**

Here’s a basic **ASP.NET Core Web API** example:

```csharp
using Microsoft.AspNetCore.Mvc;

[ApiController]
[Route("api/[controller]")]
public class HelloController : ControllerBase
{
    [HttpGet]
    public string Get()
    {
        return "Hello, World!";
    }
}
```

🔹 **Run on:** `http://localhost:5000/api/hello`  
🔹 **Response:** `"Hello, World!"`

### **Conclusion**

✅ **.NET Core** is one of the best **open-source server-side frameworks** for building **fast, secure, and scalable** web applications.  
✅ It is widely used for **enterprise solutions, cloud applications, microservices, and APIs**.  
✅ With its **high performance, cross-platform support, built-in security, and strong community**, .NET is an excellent choice for modern web development.

---

## **Working Architecture of .NET**

.NET follows a **modular and layered architecture**, allowing developers to build scalable, maintainable, and high-performance applications. It consists of **various components**, such as the **Common Language Runtime (CLR), Base Class Library (BCL), Application Models (ASP.NET, WPF, etc.), and Tools** for development and deployment.

### **1. Key Layers of .NET Architecture**

#### **1.1 Application Layer** (User Interaction)

- This is the topmost layer where users interact with the application.
- It can be **Web-based (ASP.NET Core), Desktop-based (WPF, WinForms), Mobile-based (Xamarin, MAUI), or Console-based applications**.

#### **1.2 Business Logic Layer (BLL)**

- Contains the core logic of the application, such as **validations, calculations, and workflows**.
- Helps in maintaining a **separation of concerns** to make the application modular.
- Can communicate with **APIs, databases, and external services**.

#### **1.3 Data Access Layer (DAL)**

- Handles database interactions using **Entity Framework Core (EF Core), ADO.NET, or Dapper**.
- Supports multiple databases such as **SQL Server, MySQL, PostgreSQL, MongoDB, and more**.

#### **1.4 Database Layer**

- Stores and manages application data.
- Can be relational (SQL) or non-relational (NoSQL).

### **2. Core Components of .NET Architecture**

#### **2.1 Common Language Runtime (CLR)**

- The **heart of .NET**, responsible for executing managed code.
- Provides features like **memory management (Garbage Collection), exception handling, security, and Just-In-Time (JIT) compilation**.

#### **2.2 Base Class Library (BCL)**

- A set of **pre-built libraries** that provide essential functionalities like **file handling, networking, data structures, and cryptography**.

#### **2.3 Language Interoperability**

- .NET allows multiple languages like **C#, F#, and VB.NET** to work together in a single application.

#### **2.4 ASP.NET Core (Web Framework)**

- A high-performance, cross-platform framework used for **web applications, APIs, and microservices**.
- Supports **MVC, Razor Pages, SignalR (real-time communication), and Blazor (interactive UI with C# and WebAssembly)**.

#### **2.5 Entity Framework Core (EF Core)**

- **Object-Relational Mapper (ORM)** that simplifies database interactions.
- Converts **C# objects** into database records and vice versa.

#### **2.6 Dependency Injection (DI)**

- Built-in **DI container** helps in loosely coupling application components, making the code easier to maintain and test.

#### **2.7 .NET Runtime & Hosting Environment**

- The runtime ensures that applications run efficiently on **Windows, Linux, and macOS**.
- Supports **Docker, Kubernetes, and Cloud deployments (Azure, AWS, GCP)**.

### **3. Working of .NET Architecture**

#### **Step-by-Step Execution Flow**

1️⃣ **User Interaction:** A request is initiated from a user via a web browser, mobile app, or API client.  
2️⃣ **Request Handling:** The **ASP.NET Core Web Server (Kestrel)** receives the request.  
3️⃣ **Routing:** The request is processed by the **Routing Engine**, which directs it to the appropriate **Controller**.  
4️⃣ **Business Logic Execution:** The **BLL** processes the request by applying rules, validations, and business workflows.  
5️⃣ **Data Fetching:** If needed, the **DAL retrieves data** from the database using **EF Core or ADO.NET**.  
6️⃣ **Response Generation:** The processed data is sent back as **HTML (for Web UI), JSON (for APIs), or any other format**.  
7️⃣ **Rendering & Display:** The frontend (React, Angular, Blazor, or Razor Pages) renders the response to the user.

### **4. Diagram Representation of .NET Architecture**

```
+----------------------------------------------------+
|                User Interface Layer               |
| (Web App, Mobile App, Desktop App, API Client)    |
+----------------------------------------------------+
                 ↓ Request/Response
+----------------------------------------------------+
|              ASP.NET Core Framework               |
| (MVC, Razor Pages, Blazor, Web API, SignalR)      |
+----------------------------------------------------+
                 ↓ Controller Calls
+----------------------------------------------------+
|        Business Logic Layer (BLL)                 |
| (Validations, Rules, Security, Workflows)         |
+----------------------------------------------------+
                 ↓ Data Processing
+----------------------------------------------------+
|         Data Access Layer (DAL)                   |
| (EF Core, ADO.NET, Dapper)                        |
+----------------------------------------------------+
                 ↓ Database Interaction
+----------------------------------------------------+
|          Database Layer (SQL/NoSQL)               |
| (SQL Server, PostgreSQL, MongoDB, etc.)           |
+----------------------------------------------------+
```

### **5. Advantages of .NET Architecture**

✅ **Cross-Platform:** Runs on **Windows, Linux, macOS**.  
✅ **High Performance:** Optimized for **speed and scalability**.  
✅ **Secure:** Built-in **authentication, authorization, and data encryption**.  
✅ **Modular & Maintainable:** Supports **MVC, DI, and Microservices**.  
✅ **Cloud & Docker Support:** Seamless integration with **Azure, AWS, and Kubernetes**.

### **6. Real-World Applications Using .NET**

🏦 **Banking & Finance:** Secure payment systems (e.g., PayPal uses .NET for APIs).  
🏥 **Healthcare:** EMR & hospital management applications.  
🛒 **E-commerce:** Large-scale platforms like Alibaba & Stack Overflow.  
📡 **IoT & AI Applications:** AI-powered systems & IoT analytics dashboards.

### **Conclusion**

📌 .NET **follows a layered architecture**, allowing developers to build **scalable, secure, and high-performance** applications.  
📌 With support for **MVC, Microservices, APIs, and Cloud**, .NET is ideal for modern **web, mobile, and enterprise applications**.  
📌 It integrates **easily with databases, cloud services, and containerized environments (Docker, Kubernetes)**.

---

## Components of .NET Framework

The **.NET Framework** consists of several key components that enable developers to build, execute, and manage applications efficiently. Below are the core components of the .NET Framework, including **CLI, CLS, CTS, CLR, and FCL**:

### **1. Common Language Infrastructure (CLI)**

**CLI (Common Language Infrastructure)** is the **foundation of the .NET Framework** that defines the runtime environment and the execution model for .NET applications. It enables **multiple programming languages** (C#, VB.NET, F#) to work together by providing a unified execution environment.

#### **Key Features of CLI:**

✔️ Provides a **runtime environment** for .NET applications.  
✔️ Supports **cross-language interoperability** (C#, VB.NET, F# work together).  
✔️ Standardized under **ECMA and ISO**.  
✔️ Contains **CTS, CLS, CLR, and JIT compiler**.

### **2. Common Language Specification (CLS)**

**CLS (Common Language Specification)** is a set of **rules and guidelines** that ensure interoperability between different .NET languages. It ensures that code written in one .NET language can be used in another.

#### **Key Features of CLS:**

✔️ Defines a **subset of features** that all .NET languages must support.  
✔️ Ensures **language interoperability** (e.g., C# can call a VB.NET function).  
✔️ Helps in **cross-language code sharing**.  
✔️ Ensures **type compatibility** across .NET languages.

🔹 **Example of CLS Compliance:**  
✅ **Valid CLS Code (C#):**

```csharp
public class Example
{
    public int Add(int a, int b)  // CLS-compliant
    {
        return a + b;
    }
}
```

❌ **Invalid CLS Code:**

```csharp
public class Example
{
    public uint Add(uint a, uint b) // 'uint' is not CLS-compliant
    {
        return a + b;
    }
}
```

🔹 `uint` is not CLS-compliant because not all .NET languages support unsigned types.

### **3. Common Type System (CTS)**

**CTS (Common Type System)** is a set of rules that defines **how data types should be declared and used** in different .NET languages. It ensures that data types are consistent across all languages.

#### **Key Features of CTS:**

✔️ Defines a **standard set of data types**.  
✔️ Provides **type safety** and avoids conflicts between languages.  
✔️ Categorizes types into **Value Types** and **Reference Types**.

#### **CTS Data Type Categories:**

✅ **1. Value Types** (Stored in Stack)

- `int`, `float`, `double`, `char`, `bool`
- `struct`, `enum`

✅ **2. Reference Types** (Stored in Heap)

- `class`, `interface`, `delegate`, `array`

🔹 **Example of CTS Compliance:**

```csharp
int x = 10;  // CTS value type
string name = "Hello"; // CTS reference type
```

🔹 In **C#**, `int` is mapped to `System.Int32`, while in **VB.NET**, `Integer` is mapped to the same `System.Int32`.  
🔹 This **ensures consistency across .NET languages**.

### **4. Common Language Runtime (CLR)**

**CLR (Common Language Runtime)** is the **execution engine** of the .NET Framework that manages code execution, memory management, security, and more.

#### **Key Features of CLR:**

✔️ **Converts CIL/MSIL to native machine code** via the **JIT (Just-In-Time) Compiler**.  
✔️ **Manages memory automatically** through **Garbage Collection (GC)**.  
✔️ Provides **security features**, including Code Access Security (CAS).  
✔️ Handles **exception management** (try-catch).  
✔️ Supports **multithreading and concurrency**.

#### **CLR Execution Flow:**

1️⃣ **Source Code (C#, VB.NET, F#)**  
2️⃣ **Compiled into CIL (Common Intermediate Language)**  
3️⃣ **JIT (Just-In-Time) Compiler converts CIL into native machine code**  
4️⃣ **CLR executes the compiled code on the OS**

🔹 **Example of CLR Execution:**

```csharp
class Program
{
    static void Main()
    {
        Console.WriteLine("Hello, World!");
    }
}
```

🔹 This C# code is **compiled into CIL (MSIL)** and then converted into machine code by the **JIT Compiler** at runtime.

### **5. Framework Class Library (FCL) / Base Class Library (BCL)**

**FCL (Framework Class Library)**, also known as **BCL (Base Class Library)**, is a **collection of reusable classes and APIs** that developers can use for common tasks like file handling, database access, networking, and more.

#### **Key Features of FCL:**

✔️ Includes **System.IO** (File handling), **System.Net** (Networking), **System.Data** (Database).  
✔️ Provides **rich APIs** for **data structures, cryptography, multithreading, and serialization**.  
✔️ Used by **ASP.NET Core, WinForms, WPF, and Xamarin**.

🔹 **Example of FCL Usage:**

```csharp
using System;
using System.IO;

class Program
{
    static void Main()
    {
        File.WriteAllText("test.txt", "Hello, .NET!"); // Using System.IO
        Console.WriteLine("File Created!");
    }
}
```

🔹 This example **writes a text file** using the **System.IO** namespace.

### **Diagram of .NET Framework Components**

```
+----------------------------------------+
|      .NET Framework Components        |
+----------------------------------------+
|  Application Code (C#, VB.NET, F#)     |
+----------------------------------------+
|  Common Language Specification (CLS)   |
+----------------------------------------+
|  Common Type System (CTS)              |
+----------------------------------------+
|  Framework Class Library (FCL/BCL)     |
+----------------------------------------+
|  Common Language Runtime (CLR)         |
|  - Garbage Collection (GC)             |
|  - JIT Compiler                        |
|  - Exception Handling                   |
+----------------------------------------+
|  Operating System (Windows, Linux)     |
+----------------------------------------+
```

### **Conclusion**

📌 **CLI** provides a **runtime environment** for executing .NET applications.  
📌 **CLS** ensures **language interoperability** among C#, VB.NET, and F#.  
📌 **CTS** defines **consistent data types** across different languages.  
📌 **CLR** is the **execution engine** responsible for memory management, security, and code execution.  
📌 **FCL/BCL** provides **pre-built libraries** to simplify development.

---

## **Framework Class Library (FCL) in .NET**

The **Framework Class Library (FCL)** is a **comprehensive set of reusable classes, interfaces, and APIs** provided by **.NET** to simplify application development. It includes essential functionalities like **file handling, networking, collections, security, multithreading, database access, and more**.

FCL is a core part of **.NET** and is commonly referred to as the **Base Class Library (BCL)** when talking about fundamental system-level classes.

### **Key Features of FCL**

✔️ **Rich Set of APIs**: Provides built-in support for file handling, networking, security, threading, data manipulation, and more.  
✔️ **Cross-Language Compatibility**: Works with **C#, VB.NET, F#, and other .NET languages**.  
✔️ **Object-Oriented Design**: Promotes reusability, encapsulation, and modular programming.  
✔️ **Platform Independence**: Works across **Windows, Linux, macOS** when using **.NET Core/.NET 5+**.  
✔️ **Automatic Memory Management**: Works with **Garbage Collection (GC)** to manage memory efficiently.

### **Major Components of FCL**

The **FCL is divided into different namespaces** based on their functionality. Below are the **most important namespaces**:

#### **1. System Namespace (Core Functionality)**

- **Provides core data types, console operations, and basic functionality.**
- **Common Classes:**
  - `System.Object` → Base class for all .NET types
  - `System.String` → Represents a sequence of characters
  - `System.Console` → Handles console input and output
  - `System.Math` → Provides mathematical functions

🔹 **Example: Using System Namespace**

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Hello, .NET!");
        int number = Math.Max(10, 20);
        Console.WriteLine("Max Number: " + number);
    }
}
```

#### **2. System.IO (File Handling)**

- **Used for working with files, directories, and streams.**
- **Common Classes:**
  - `File` → Create, read, write files
  - `Directory` → Create, move, delete directories
  - `StreamReader` / `StreamWriter` → Read and write text streams

🔹 **Example: Writing to a File**

```csharp
using System;
using System.IO;

class Program
{
    static void Main()
    {
        File.WriteAllText("example.txt", "Hello, .NET FCL!");
        Console.WriteLine("File written successfully!");
    }
}
```

#### **3. System.Collections & System.Collections.Generic (Data Structures)**

- **Provides built-in data structures like lists, dictionaries, and queues.**
- **Common Classes:**
  - `List<T>` → Generic list
  - `Dictionary<TKey, TValue>` → Key-value pair collection
  - `Queue<T>` / `Stack<T>` → FIFO and LIFO collections

🔹 **Example: Using List and Dictionary**

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        List<string> names = new List<string> { "Alice", "Bob", "Charlie" };
        names.Add("David");
        Console.WriteLine("First Name: " + names[0]);

        Dictionary<int, string> students = new Dictionary<int, string>();
        students.Add(1, "John");
        students.Add(2, "Emma");
        Console.WriteLine("Student ID 1: " + students[1]);
    }
}
```

#### **4. System.Net (Networking & Web Requests)**

- **Used for handling HTTP requests, TCP/IP communication, and web APIs.**
- **Common Classes:**
  - `HttpClient` → Makes web requests
  - `WebClient` → Simplifies HTTP communication
  - `TcpClient` / `TcpListener` → Handles low-level network communication

🔹 **Example: Making an HTTP GET Request**

```csharp
using System;
using System.Net.Http;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        HttpClient client = new HttpClient();
        string result = await client.GetStringAsync("https://jsonplaceholder.typicode.com/todos/1");
        Console.WriteLine(result);
    }
}
```

#### **5. System.Threading (Multithreading & Parallel Processing)**

- **Allows developers to create multi-threaded applications.**
- **Common Classes:**
  - `Thread` → Creates a new thread
  - `Task` → Used for asynchronous programming
  - `Parallel` → Enables parallel execution of loops

🔹 **Example: Running Multiple Threads**

```csharp
using System;
using System.Threading;

class Program
{
    static void PrintNumbers()
    {
        for (int i = 1; i <= 5; i++)
        {
            Console.WriteLine(i);
            Thread.Sleep(1000);
        }
    }

    static void Main()
    {
        Thread t = new Thread(PrintNumbers);
        t.Start();
        Console.WriteLine("Main thread is running...");
    }
}
```

#### **6. System.Data & Entity Framework (Database Access)**

- **Used for working with databases, SQL queries, and ORM (Object-Relational Mapping).**
- **Common Classes:**
  - `SqlConnection` → Connects to a database
  - `SqlCommand` → Executes SQL queries
  - `Entity Framework Core` → ORM for database interactions

🔹 **Example: Connecting to SQL Database**

```csharp
using System;
using System.Data.SqlClient;

class Program
{
    static void Main()
    {
        string connectionString = "Server=yourserver;Database=yourdb;User Id=youruser;Password=yourpassword;";
        using (SqlConnection conn = new SqlConnection(connectionString))
        {
            conn.Open();
            Console.WriteLine("Connected to Database!");
        }
    }
}
```

### **Comparison: FCL vs BCL**

| Feature        | **FCL (Framework Class Library)**         | **BCL (Base Class Library)**                                       |
| -------------- | ----------------------------------------- | ------------------------------------------------------------------ |
| **Definition** | Complete library set for .NET             | Core subset of FCL                                                 |
| **Scope**      | Includes BCL, ADO.NET, ASP.NET, WPF, etc. | Includes only core system classes like collections, I/O, threading |
| **Usage**      | Used for all types of .NET development    | Used mainly for fundamental operations                             |

🔹 **BCL is a subset of FCL**, and FCL contains additional libraries like **ASP.NET, WPF, ADO.NET, and more**.

### **Conclusion**

✅ **FCL is a massive library of reusable classes and APIs** that simplify development.  
✅ It provides essential **file handling, networking, data processing, and multithreading** support.  
✅ Supports **cross-platform development** with .NET Core/.NET 5+.  
✅ Works across **Windows, Linux, and macOS** efficiently.

---

## **ASP.NET Using C#** 🚀

### **What is ASP.NET?**

ASP.NET is a **server-side web development framework** built on the **.NET platform**, used to create **dynamic, data-driven web applications and APIs**. It is developed by **Microsoft** and supports multiple programming languages, including **C# and VB.NET**.

### **Key Features of ASP.NET**

✔️ **Fast and Scalable** – Uses Just-In-Time (JIT) compilation and optimized performance.  
✔️ **Cross-Platform** – Works on **Windows, Linux, and macOS** using ASP.NET Core.  
✔️ **MVC Architecture** – Supports **Model-View-Controller** for structured applications.  
✔️ **Built-in Security** – Includes authentication, authorization, and data protection.  
✔️ **Integration with Databases** – Supports **SQL Server, MySQL, MongoDB, and more**.  
✔️ **Supports REST APIs** – Ideal for building **Web APIs** using C#.  
✔️ **Modern UI Frameworks** – Works with **React, Angular, Blazor, and Bootstrap**.

### **ASP.NET Variants**

There are three main **ASP.NET** technologies:  
| Technology | Description | Use Case |
|------------|------------|----------|
| **ASP.NET Web Forms** | Event-driven model, drag-and-drop controls | Legacy web applications |
| **ASP.NET MVC** | Model-View-Controller architecture | Structured web apps |
| **ASP.NET Core** | Cross-platform, open-source | Modern web apps & APIs |

ASP.NET Core is the **most preferred** choice for **modern development**.

### **1️⃣ Setting Up an ASP.NET Core Project**

#### **Step 1: Install .NET SDK**

✅ Download and install the latest **.NET SDK** from [Microsoft .NET](https://dotnet.microsoft.com/download).

#### **Step 2: Create a New ASP.NET Project**

Open a terminal or command prompt and run:

```bash
dotnet new webapp -n MyAspNetApp
cd MyAspNetApp
dotnet run
```

This starts the application at `http://localhost:5000`.

### **2️⃣ Basic ASP.NET MVC Structure**

#### **MVC Pattern in ASP.NET**

ASP.NET follows the **MVC (Model-View-Controller)** architecture:  
1️⃣ **Model** → Handles data and business logic.  
2️⃣ **View** → Displays data (UI layer).  
3️⃣ **Controller** → Handles user input and updates Model & View.

#### **Project Structure**

```
MyAspNetApp/
│-- Controllers/       → Handles requests
│   ├── HomeController.cs
│-- Models/            → Data logic (optional)
│   ├── Product.cs
│-- Views/             → UI pages
│   ├── Home/
│       ├── Index.cshtml
│-- appsettings.json   → Configurations
│-- Program.cs         → Application entry point
│-- Startup.cs         → Middleware & Routing
```

### **3️⃣ Creating a Basic ASP.NET MVC App**

#### **Step 1: Create a Controller**

A **Controller** handles HTTP requests and returns responses.

📌 **File:** `Controllers/HomeController.cs`

```csharp
using Microsoft.AspNetCore.Mvc;

namespace MyAspNetApp.Controllers
{
    public class HomeController : Controller
    {
        public IActionResult Index()
        {
            ViewData["Message"] = "Welcome to ASP.NET Core MVC!";
            return View();
        }
    }
}
```

#### **Step 2: Create a View**

📌 **File:** `Views/Home/Index.cshtml`

```html
@{ ViewData["Title"] = "Home Page"; }

<h1>@ViewData["Message"]</h1>
<p>This is a simple ASP.NET Core MVC page.</p>
```

#### **Step 3: Configure Routing**

📌 **File:** `Program.cs`

```csharp
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.MapControllerRoute(
    name: "default",
    pattern: "{controller=Home}/{action=Index}/{id?}");

app.Run();
```

✅ **Run the project** using:

```bash
dotnet run
```

Now, open `http://localhost:5000/Home/Index` in a browser. 🎉

### **4️⃣ Connecting ASP.NET to a Database (SQL Server)**

#### **Step 1: Install Entity Framework Core**

Run the following command to install **EF Core** for SQL Server:

```bash
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
dotnet add package Microsoft.EntityFrameworkCore.Tools
```

#### **Step 2: Create a Database Model**

📌 **File:** `Models/Product.cs`

```csharp
using System.ComponentModel.DataAnnotations;

namespace MyAspNetApp.Models
{
    public class Product
    {
        [Key]
        public int Id { get; set; }
        public string Name { get; set; }
        public decimal Price { get; set; }
    }
}
```

#### **Step 3: Configure Database Context**

📌 **File:** `Models/AppDbContext.cs`

```csharp
using Microsoft.EntityFrameworkCore;

namespace MyAspNetApp.Models
{
    public class AppDbContext : DbContext
    {
        public AppDbContext(DbContextOptions<AppDbContext> options) : base(options) { }
        public DbSet<Product> Products { get; set; }
    }
}
```

#### **Step 4: Configure Connection String**

📌 **File:** `appsettings.json`

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost;Database=MyAspNetAppDb;Trusted_Connection=True;"
  }
}
```

#### **Step 5: Register Database in Program.cs**

📌 **File:** `Program.cs`

```csharp
var builder = WebApplication.CreateBuilder(args);
builder.Services.AddDbContext<AppDbContext>(options =>
    options.UseSqlServer(builder.Configuration.GetConnectionString("DefaultConnection")));
```

#### **Step 6: Apply Database Migrations**

Run the following commands:

```bash
dotnet ef migrations add InitialCreate
dotnet ef database update
```

✅ This creates a **SQL Server database** with a `Products` table.

### **5️⃣ Creating a Web API in ASP.NET**

ASP.NET can be used to **create RESTful APIs**.

#### **Step 1: Create an API Controller**

📌 **File:** `Controllers/ProductController.cs`

```csharp
using Microsoft.AspNetCore.Mvc;
using MyAspNetApp.Models;
using System.Collections.Generic;
using System.Linq;

namespace MyAspNetApp.Controllers
{
    [Route("api/products")]
    [ApiController]
    public class ProductController : ControllerBase
    {
        private readonly AppDbContext _context;

        public ProductController(AppDbContext context)
        {
            _context = context;
        }

        [HttpGet]
        public ActionResult<IEnumerable<Product>> GetProducts()
        {
            return _context.Products.ToList();
        }

        [HttpPost]
        public IActionResult CreateProduct(Product product)
        {
            _context.Products.Add(product);
            _context.SaveChanges();
            return CreatedAtAction(nameof(GetProducts), new { id = product.Id }, product);
        }
    }
}
```

#### **Step 2: Test API Using Postman or Browser**

Start the server:

```bash
dotnet run
```

Then test API:

- **GET Products:** `http://localhost:5000/api/products`
- **POST Product:** Use **Postman** to send a `POST` request with JSON data:

```json
{
  "name": "Laptop",
  "price": 1200.5
}
```

### **Conclusion**

✅ **ASP.NET with C#** enables **web app & API development**.  
✅ Uses **MVC architecture** for structured applications.  
✅ Supports **SQL Server with Entity Framework Core**.  
✅ Can build **RESTful APIs** for modern applications.  
✅ Works **cross-platform (Windows, Linux, macOS)**.

---

## **ASP.NET Web Forms & Running Web Applications on a Server**

### **1️⃣ What is ASP.NET Web Forms?**

**ASP.NET Web Forms** is a part of the **.NET framework** that allows developers to create **dynamic, data-driven web applications** using a **drag-and-drop** and **event-driven** programming model. It is useful for **rapid development** and works well for applications with a **graphical UI**.

🔹 **Key Features of ASP.NET Web Forms:**  
✔️ **Event-Driven Programming** – Works like Windows Forms applications with events like `Button_Click`.  
✔️ **Drag-and-Drop Controls** – Use UI controls like TextBox, GridView, and Buttons.  
✔️ **ViewState** – Maintains the state of controls between postbacks.  
✔️ **Rapid Development** – No need to write extensive JavaScript or AJAX manually.  
✔️ **Built-in Data Binding** – Easy integration with SQL databases.

### **2️⃣ Setting Up an ASP.NET Web Forms Project**

#### **Step 1: Install Visual Studio**

Download and install **Visual Studio** from [Microsoft](https://visualstudio.microsoft.com/).

#### **Step 2: Create a New ASP.NET Web Forms Project**

1️⃣ Open **Visual Studio**  
2️⃣ Click on **Create a new project**  
3️⃣ Search for **ASP.NET Web Application (.NET Framework)**  
4️⃣ Choose **Web Forms** and click **Create**

### **3️⃣ ASP.NET Web Forms Structure**

When you create a Web Forms project, the structure looks like this:

```
MyWebFormsApp/
│-- App_Code/           → Helper classes
│-- App_Data/           → Database files
│-- Scripts/            → JavaScript files
│-- Styles/             → CSS files
│-- Default.aspx        → Main web page
│-- Default.aspx.cs     → Code-behind file (C# logic)
│-- Web.config         → Application settings
```

#### **Understanding Web Forms Files**

📌 **Web Page (`.aspx`)** → Contains **HTML & Web Controls**  
📌 **Code-Behind (`.aspx.cs`)** → Contains **C# code** for event handling

### **4️⃣ Creating a Simple Web Form**

#### **Step 1: Design the Web Form**

📌 **File:** `Default.aspx`

```html
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="Default.aspx.cs"
Inherits="MyWebFormsApp.Default" %>

<!DOCTYPE html>
<html>
  <head>
    <title>ASP.NET Web Forms</title>
  </head>
  <body>
    <form id="form1" runat="server">
      <h2>Welcome to ASP.NET Web Forms!</h2>

      <asp:Label
        ID="lblMessage"
        runat="server"
        Text="Enter your name:"
      ></asp:Label>
      <asp:TextBox ID="txtName" runat="server"></asp:TextBox>

      <asp:Button
        ID="btnSubmit"
        runat="server"
        Text="Submit"
        OnClick="btnSubmit_Click"
      />

      <br /><br />
      <asp:Label ID="lblOutput" runat="server" ForeColor="Blue"></asp:Label>
    </form>
  </body>
</html>
```

#### **Step 2: Write the Code-Behind**

📌 **File:** `Default.aspx.cs`

```csharp
using System;

namespace MyWebFormsApp
{
    public partial class Default : System.Web.UI.Page
    {
        protected void btnSubmit_Click(object sender, EventArgs e)
        {
            lblOutput.Text = "Hello, " + txtName.Text + "!";
        }
    }
}
```

✅ When the user clicks the **Submit** button, the page displays "Hello, [name]!"

### **5️⃣ Running ASP.NET Web Forms Using a Web Server**

ASP.NET applications **require a web server** to run. You can use:

#### **A) Running in Visual Studio (IIS Express)**

1️⃣ Click **Run (F5)** in Visual Studio  
2️⃣ The application runs on `http://localhost:xxxx`

✅ This is the easiest way to run and test ASP.NET Web Forms apps.

#### **B) Running on IIS (Internet Information Services)**

IIS is a **Microsoft web server** used for hosting ASP.NET applications.

##### **Step 1: Enable IIS on Windows**

1️⃣ Open **Control Panel** → **Turn Windows features on or off**  
2️⃣ Check **Internet Information Services (IIS)**  
3️⃣ Click **OK** and Restart your PC

##### **Step 2: Deploy Web Forms App on IIS**

1️⃣ Open **IIS Manager** (`inetmgr` in Run)  
2️⃣ Add a new **Website** → Set **Physical Path** to your Web Forms folder  
3️⃣ Set **Port** (e.g., `8080`) and Click **Start**  
4️⃣ Access the site in a browser:

```
http://localhost:8080
```

#### **C) Running on an External Server (Deployment)**

1️⃣ **Publish Web Forms App**

- Right-click on your project in Visual Studio
- Click **Publish** → Choose **Folder, FTP, or Azure**

2️⃣ **Host on a Server**

- Upload the **published files** to a web hosting provider
- Use **IIS, Azure, or a cloud platform**

### **6️⃣ Connecting Web Forms to a Database (SQL Server)**

ASP.NET Web Forms can **easily connect** to a SQL Server database.

#### **Step 1: Create a Database Table**

Run this SQL command in **SQL Server**:

```sql
CREATE TABLE Users (
    Id INT PRIMARY KEY IDENTITY,
    Name NVARCHAR(100) NOT NULL
);
```

#### **Step 2: Add a Database Connection**

📌 **File:** `Web.config`

```xml
<connectionStrings>
    <add name="MyDbConnection" connectionString="Server=localhost;Database=MyDatabase;Trusted_Connection=True;" providerName="System.Data.SqlClient"/>
</connectionStrings>
```

#### **Step 3: Fetch Data from the Database**

📌 **File:** `Default.aspx.cs`

```csharp
using System;
using System.Data.SqlClient;
using System.Web.UI.WebControls;

namespace MyWebFormsApp
{
    public partial class Default : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e)
        {
            if (!IsPostBack)
            {
                LoadUsers();
            }
        }

        private void LoadUsers()
        {
            string connString = System.Configuration.ConfigurationManager.ConnectionStrings["MyDbConnection"].ConnectionString;
            using (SqlConnection conn = new SqlConnection(connString))
            {
                conn.Open();
                SqlCommand cmd = new SqlCommand("SELECT Name FROM Users", conn);
                SqlDataReader reader = cmd.ExecuteReader();

                while (reader.Read())
                {
                    lblOutput.Text += reader["Name"].ToString() + "<br />";
                }
            }
        }
    }
}
```

✅ This **retrieves user names** from the database and **displays them on the page**.

### **7️⃣ Advantages of ASP.NET Web Forms**

✔️ **Easy to Learn** – Suitable for beginners with minimal coding.  
✔️ **Drag-and-Drop UI** – Quick UI creation with pre-built controls.  
✔️ **State Management** – ViewState preserves form data after postback.  
✔️ **Event-Driven** – Works like a Windows app with button click events.  
✔️ **Integrated with .NET** – Uses C#, SQL, and ADO.NET for backend processing.

### **Conclusion**

✅ **ASP.NET Web Forms** is ideal for **rapid development** of web apps.  
✅ Can be **hosted on IIS, cloud, or external servers**.  
✅ Supports **database integration** with SQL Server.  
✅ Works well for **enterprise applications** but is being replaced by **ASP.NET Core**.

---

## **ASP.NET Web Forms Controls** 🚀

ASP.NET Web Forms provide a variety of **server controls** that help developers create interactive web applications quickly. These controls are processed on the **server-side** and rendered as **HTML elements** in the browser.

### **1️⃣ Common ASP.NET Web Forms Controls**

| **Control**                                   | **Description**                          |
| --------------------------------------------- | ---------------------------------------- |
| **Button** (`<asp:Button>`)                   | Triggers server-side events when clicked |
| **TextBox** (`<asp:TextBox>`)                 | Accepts user input                       |
| **Label** (`<asp:Label>`)                     | Displays text on the page                |
| **CheckBox** (`<asp:CheckBox>`)               | A single checkbox for selecting options  |
| **CheckBoxList** (`<asp:CheckBoxList>`)       | A group of checkboxes                    |
| **RadioButton** (`<asp:RadioButton>`)         | A single radio button (part of a group)  |
| **RadioButtonList** (`<asp:RadioButtonList>`) | A group of radio buttons                 |
| **ListBox** (`<asp:ListBox>`)                 | A multi-item selectable list             |
| **Calendar** (`<asp:Calendar>`)               | Displays a calendar for date selection   |
| **AdRotator** (`<asp:AdRotator>`)             | Rotates and displays advertisements      |

### **2️⃣ Example: Web Form with Controls**

📌 **File:** `Default.aspx`

```html
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="Default.aspx.cs"
Inherits="MyWebFormsApp.Default" %>

<!DOCTYPE html>
<html>
  <head>
    <title>ASP.NET Web Forms Controls</title>
  </head>
  <body>
    <form id="form1" runat="server">
      <h2>ASP.NET Web Forms Controls Demo</h2>

      <!-- Label & TextBox -->
      <asp:Label
        ID="lblName"
        runat="server"
        Text="Enter your name: "
      ></asp:Label>
      <asp:TextBox ID="txtName" runat="server"></asp:TextBox>

      <br /><br />

      <!-- CheckBox -->
      <asp:CheckBox
        ID="chkSubscribe"
        runat="server"
        Text="Subscribe to newsletter"
      />

      <br /><br />

      <!-- CheckBoxList -->
      <asp:CheckBoxList ID="chkHobbies" runat="server">
        <asp:ListItem Text="Reading" Value="Reading"></asp:ListItem>
        <asp:ListItem Text="Sports" Value="Sports"></asp:ListItem>
        <asp:ListItem Text="Music" Value="Music"></asp:ListItem>
      </asp:CheckBoxList>

      <br />

      <!-- RadioButton -->
      <asp:RadioButton
        ID="rbMale"
        runat="server"
        GroupName="Gender"
        Text="Male"
      />
      <asp:RadioButton
        ID="rbFemale"
        runat="server"
        GroupName="Gender"
        Text="Female"
      />

      <br /><br />

      <!-- RadioButtonList -->
      <asp:RadioButtonList ID="rblAgeGroup" runat="server">
        <asp:ListItem Text="18-25" Value="18-25"></asp:ListItem>
        <asp:ListItem Text="26-35" Value="26-35"></asp:ListItem>
        <asp:ListItem Text="36-50" Value="36-50"></asp:ListItem>
      </asp:RadioButtonList>

      <br />

      <!-- ListBox -->
      <asp:ListBox ID="lstCountry" runat="server" SelectionMode="Single">
        <asp:ListItem Text="USA" Value="USA"></asp:ListItem>
        <asp:ListItem Text="UK" Value="UK"></asp:ListItem>
        <asp:ListItem Text="India" Value="India"></asp:ListItem>
      </asp:ListBox>

      <br /><br />

      <!-- Calendar -->
      <asp:Calendar ID="calDate" runat="server"></asp:Calendar>

      <br /><br />

      <!-- Button -->
      <asp:Button
        ID="btnSubmit"
        runat="server"
        Text="Submit"
        OnClick="btnSubmit_Click"
      />

      <br /><br />

      <!-- Label for Output -->
      <asp:Label ID="lblOutput" runat="server" ForeColor="Blue"></asp:Label>
    </form>
  </body>
</html>
```

### **3️⃣ Code-Behind: Handling Events**

📌 **File:** `Default.aspx.cs`

```csharp
using System;
using System.Web.UI.WebControls;

namespace MyWebFormsApp
{
    public partial class Default : System.Web.UI.Page
    {
        protected void btnSubmit_Click(object sender, EventArgs e)
        {
            string name = txtName.Text;
            string gender = rbMale.Checked ? "Male" : (rbFemale.Checked ? "Female" : "Not selected");
            string ageGroup = rblAgeGroup.SelectedValue;
            string country = lstCountry.SelectedValue;
            bool isSubscribed = chkSubscribe.Checked;

            string hobbies = "";
            foreach (ListItem item in chkHobbies.Items)
            {
                if (item.Selected)
                    hobbies += item.Text + ", ";
            }

            string selectedDate = calDate.SelectedDate.ToShortDateString();
            if (string.IsNullOrWhiteSpace(selectedDate) || selectedDate == "01/01/0001")
                selectedDate = "Not Selected";

            lblOutput.Text = $"Name: {name}<br />" +
                             $"Gender: {gender}<br />" +
                             $"Age Group: {ageGroup}<br />" +
                             $"Country: {country}<br />" +
                             $"Hobbies: {hobbies}<br />" +
                             $"Subscribed: {(isSubscribed ? "Yes" : "No")}<br />" +
                             $"Selected Date: {selectedDate}";
        }
    }
}
```

### **4️⃣ Explanation of Controls and Code**

🔹 **TextBox (`<asp:TextBox>`)** → Accepts user input.  
🔹 **CheckBox (`<asp:CheckBox>`)** → Allows users to select a **single** option.  
🔹 **CheckBoxList (`<asp:CheckBoxList>`)** → Allows users to select **multiple** options.  
🔹 **RadioButton (`<asp:RadioButton>`)** → Allows selection of **one option** in a group.  
🔹 **RadioButtonList (`<asp:RadioButtonList>`)** → Displays a list of radio buttons.  
🔹 **ListBox (`<asp:ListBox>`)** → Provides a dropdown list with multiple selections.  
🔹 **Calendar (`<asp:Calendar>`)** → Allows date selection.  
🔹 **Button (`<asp:Button>`)** → Submits the form and triggers `OnClick` event.  
🔹 **Label (`<asp:Label>`)** → Displays the output message.

When the user clicks the **Submit** button:  
✔️ The data is collected from the controls.  
✔️ The output is displayed in the **Label (`lblOutput`)**.

### **5️⃣ AdRotator Control (Advertisement Display)**

The **AdRotator control** is used to display **random advertisements** from an XML file.

#### **Step 1: Create an XML File for Ads**

📌 **File:** `Ads.xml`

```xml
<Advertisements>
    <Ad>
        <ImageUrl>images/ad1.jpg</ImageUrl>
        <NavigateUrl>https://www.example.com/ad1</NavigateUrl>
        <AlternateText>Buy Now!</AlternateText>
    </Ad>
    <Ad>
        <ImageUrl>images/ad2.jpg</ImageUrl>
        <NavigateUrl>https://www.example.com/ad2</NavigateUrl>
        <AlternateText>Great Discount!</AlternateText>
    </Ad>
</Advertisements>
```

#### **Step 2: Add AdRotator Control**

📌 **File:** `Default.aspx`

```html
<asp:AdRotator ID="adBanner" runat="server" AdvertisementFile="~/Ads.xml" />
```

✅ The AdRotator **randomly selects and displays** an ad from `Ads.xml`.

### **6️⃣ Summary**

✔️ **ASP.NET Web Forms** provides **easy-to-use** server controls.  
✔️ **Button, TextBox, Label, CheckBox, RadioButton, ListBox** are commonly used.  
✔️ **Calendar control** allows date selection.  
✔️ **AdRotator** helps display rotating ads.  
✔️ **Event handling** in C# processes form submissions.

---

## **Form Validation Using Server Validation Controls in ASP.NET Web Forms**

ASP.NET provides **server-side validation controls** to ensure that user input is **correct, complete, and secure** before processing. These validation controls help prevent **invalid data submission**, reducing errors and security risks.

### **1️⃣ Types of Server Validation Controls**

| **Validation Control**         | **Description**                                                  |
| ------------------------------ | ---------------------------------------------------------------- |
| **RequiredFieldValidator**     | Ensures the field is not left blank.                             |
| **CompareValidator**           | Compares values of two controls (e.g., password confirmation).   |
| **RangeValidator**             | Checks if the input falls within a specified range.              |
| **RegularExpressionValidator** | Validates input against a specific pattern (e.g., email format). |
| **CustomValidator**            | Allows custom validation logic.                                  |
| **ValidationSummary**          | Displays a summary of validation errors.                         |

### **2️⃣ Implementing Validation in ASP.NET Web Forms**

#### **📌 Example: Validating a Registration Form**

📌 **File:** `Default.aspx`

```html
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="Default.aspx.cs"
Inherits="MyWebFormsApp.Default" %>

<!DOCTYPE html>
<html>
  <head>
    <title>ASP.NET Validation Controls</title>
  </head>
  <body>
    <form id="form1" runat="server">
      <h2>Registration Form with Validation</h2>

      <!-- Name Field (Required) -->
      <asp:Label ID="lblName" runat="server" Text="Name: "></asp:Label>
      <asp:TextBox ID="txtName" runat="server"></asp:TextBox>
      <asp:RequiredFieldValidator
        ID="rfvName"
        runat="server"
        ControlToValidate="txtName"
        ErrorMessage="Name is required!"
        ForeColor="Red"
        Display="Dynamic"
      />
      <br /><br />

      <!-- Age Field (Range: 18-60) -->
      <asp:Label ID="lblAge" runat="server" Text="Age: "></asp:Label>
      <asp:TextBox ID="txtAge" runat="server"></asp:TextBox>
      <asp:RangeValidator
        ID="rvAge"
        runat="server"
        ControlToValidate="txtAge"
        Type="Integer"
        MinimumValue="18"
        MaximumValue="60"
        ErrorMessage="Age must be between 18 and 60!"
        ForeColor="Red"
        Display="Dynamic"
      />
      <br /><br />

      <!-- Email Field (Pattern Validation) -->
      <asp:Label ID="lblEmail" runat="server" Text="Email: "></asp:Label>
      <asp:TextBox ID="txtEmail" runat="server"></asp:TextBox>
      <asp:RegularExpressionValidator
        ID="revEmail"
        runat="server"
        ControlToValidate="txtEmail"
        ValidationExpression="^[^@]+@[^@]+\.[a-zA-Z]{2,}$"
        ErrorMessage="Enter a valid email address!"
        ForeColor="Red"
        Display="Dynamic"
      />
      <br /><br />

      <!-- Password & Confirm Password (Comparison Validation) -->
      <asp:Label ID="lblPassword" runat="server" Text="Password: "></asp:Label>
      <asp:TextBox
        ID="txtPassword"
        runat="server"
        TextMode="Password"
      ></asp:TextBox>
      <asp:RequiredFieldValidator
        ID="rfvPassword"
        runat="server"
        ControlToValidate="txtPassword"
        ErrorMessage="Password is required!"
        ForeColor="Red"
        Display="Dynamic"
      />
      <br />

      <asp:Label
        ID="lblConfirmPassword"
        runat="server"
        Text="Confirm Password: "
      ></asp:Label>
      <asp:TextBox
        ID="txtConfirmPassword"
        runat="server"
        TextMode="Password"
      ></asp:TextBox>
      <asp:CompareValidator
        ID="cvPassword"
        runat="server"
        ControlToValidate="txtConfirmPassword"
        ControlToCompare="txtPassword"
        ErrorMessage="Passwords do not match!"
        ForeColor="Red"
        Display="Dynamic"
      />
      <br /><br />

      <!-- Custom Validator (Custom Logic) -->
      <asp:Label ID="lblPhone" runat="server" Text="Phone: "></asp:Label>
      <asp:TextBox ID="txtPhone" runat="server"></asp:TextBox>
      <asp:CustomValidator
        ID="cvPhone"
        runat="server"
        ControlToValidate="txtPhone"
        OnServerValidate="ValidatePhone"
        ErrorMessage="Phone number must be 10 digits!"
        ForeColor="Red"
        Display="Dynamic"
      />
      <br /><br />

      <!-- Validation Summary -->
      <asp:ValidationSummary ID="vsSummary" runat="server" ForeColor="Red" />

      <!-- Submit Button -->
      <asp:Button
        ID="btnSubmit"
        runat="server"
        Text="Register"
        OnClick="btnSubmit_Click"
      />

      <br /><br />
      <asp:Label ID="lblMessage" runat="server" ForeColor="Green"></asp:Label>
    </form>
  </body>
</html>
```

### **3️⃣ Code-Behind: Handling Custom Validation & Form Submission**

📌 **File:** `Default.aspx.cs`

```csharp
using System;
using System.Web.UI.WebControls;

namespace MyWebFormsApp
{
    public partial class Default : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e) { }

        // Custom Validator for Phone Number
        protected void ValidatePhone(object source, ServerValidateEventArgs args)
        {
            if (args.Value.Length == 10 && long.TryParse(args.Value, out _))
                args.IsValid = true;
            else
                args.IsValid = false;
        }

        // Submit Button Click Event
        protected void btnSubmit_Click(object sender, EventArgs e)
        {
            if (Page.IsValid)
            {
                lblMessage.Text = "Registration successful!";
            }
            else
            {
                lblMessage.Text = "";
            }
        }
    }
}
```

### **4️⃣ Explanation of Validation Controls**

✅ **RequiredFieldValidator** → Ensures fields are not left blank.  
✅ **RangeValidator** → Ensures numeric values are within a defined range.  
✅ **RegularExpressionValidator** → Validates input formats (email, phone, etc.).  
✅ **CompareValidator** → Ensures two fields have matching values.  
✅ **CustomValidator** → Defines custom validation logic (e.g., checking phone number length).  
✅ **ValidationSummary** → Displays all validation errors in one place.

### **5️⃣ Advantages of Server Validation in ASP.NET**

✔️ **Ensures Data Integrity** – Prevents incorrect or incomplete data submission.  
✔️ **Reduces Client-Side Manipulation** – More secure than JavaScript validation.  
✔️ **Works with ASP.NET Postbacks** – Ensures validation happens before processing.  
✔️ **Easy Implementation** – No need for complex JavaScript code.

### **6️⃣ Summary**

🔹 **ASP.NET Web Forms provides built-in validation controls** to validate user input.  
🔹 Validation controls include **RequiredFieldValidator, RangeValidator, RegularExpressionValidator, and more**.  
🔹 **Custom validation** allows developers to implement **custom rules**.  
🔹 **ValidationSummary** displays all error messages in one place.  
🔹 The **Page.IsValid** property ensures validation before processing data.

---

## **`Gagan Saini`**
