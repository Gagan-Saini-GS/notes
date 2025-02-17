# Unit-4

## Architecture of ADO.NET

ADO.NET (ActiveX Data Objects for .NET) is a data access technology in the .NET framework that allows applications to interact with databases. The architecture of ADO.NET is designed to support a disconnected data access model and is built on XML and the .NET framework.

### **Key Components of ADO.NET Architecture:**

#### **1. Data Providers**

Data providers are the core components of ADO.NET that facilitate communication between the application and the database. Each data provider consists of specific objects:

- **Connection**: Establishes a connection to the database (e.g., `SqlConnection`, `OleDbConnection`).
- **Command**: Executes SQL commands and stored procedures (e.g., `SqlCommand`, `OleDbCommand`).
- **DataReader**: Reads data in a forward-only, read-only manner (e.g., `SqlDataReader`).
- **DataAdapter**: Bridges the gap between a DataSet and the database, allowing data retrieval and updates.

Common ADO.NET Data Providers:

- **SQL Server Provider** (`System.Data.SqlClient`) – Optimized for Microsoft SQL Server.
- **OLE DB Provider** (`System.Data.OleDb`) – Used for various databases supporting OLE DB.
- **ODBC Provider** (`System.Data.Odbc`) – Works with ODBC-compatible databases.
- **Oracle Provider** (`System.Data.OracleClient`) – Optimized for Oracle databases.

> OLE DB stands for Object Linking Embeded DB.

#### **2. DataSet (Disconnected Architecture)**

A **DataSet** is an in-memory representation of data that can hold multiple **DataTables**. It allows applications to work with data without maintaining an active database connection.

- **DataTable**: Represents a single table of in-memory data.
- **DataRow**: Represents a row in a DataTable.
- **DataColumn**: Represents a column in a DataTable.
- **DataRelation**: Represents a relationship between two DataTables.
- **Constraints**: Defines rules like primary keys, foreign keys, and unique constraints.

#### **3. DataView**

A **DataView** provides a customizable view of a DataTable. It allows sorting, filtering, and searching without modifying the actual data.

#### **4. XML Integration**

ADO.NET is tightly integrated with XML, enabling seamless data exchange between applications.

- `DataSet.WriteXml()` – Writes DataSet data to an XML file.
- `DataSet.ReadXml()` – Reads XML data into a DataSet.

### **Architecture Diagram**

```
Application Layer
       |
       v
ADO.NET Data Provider
       |
       |-- Connection
       |-- Command
       |-- DataReader
       |-- DataAdapter
       v
DataSet (Disconnected)
       |
       |-- DataTable
       |-- DataRelation
       |-- Constraints
       v
Database (SQL Server, Oracle, MySQL, etc.)
```

### **Working of ADO.NET**

1. **Connecting to the Database**: Use `SqlConnection` or `OleDbConnection` to establish a connection.
2. **Executing Commands**: Use `SqlCommand` or `OleDbCommand` to execute SQL queries.
3. **Reading Data**:
   - Use `DataReader` for fast, forward-only access.
   - Use `DataAdapter` with a `DataSet` for disconnected data access.
4. **Updating Data**: Modify data in a `DataSet`, then use `DataAdapter.Update()` to push changes to the database.
5. **Closing the Connection**: Always close the database connection after operations.

### **Advantages of ADO.NET Architecture**

- **Scalability**: Supports disconnected architecture for handling large data efficiently.
- **Interoperability**: Uses XML for data storage and exchange.
- **Performance**: Optimized data providers for efficient database operations.
- **Flexibility**: Supports multiple database types and providers.

---

## Classes

### **1. Connection Class (`SqlConnection`, `OleDbConnection`)**

The **Connection class** in ADO.NET is used to establish and manage a connection to a database. It belongs to different namespaces depending on the database provider.

#### **Key Properties:**

- `ConnectionString` – Specifies the database connection details.
- `State` – Indicates the connection status (`Open`, `Closed`, etc.).
- `Database` – Returns the name of the connected database.

#### **Key Methods:**

- `Open()` – Opens the connection to the database.
- `Close()` – Closes the database connection.
- `Dispose()` – Releases the connection resources.

#### **Example using `SqlConnection` (SQL Server)**

```csharp
using System;
using System.Data.SqlClient;

class Program
{
    static void Main()
    {
        string connString = "Server=your_server;Database=your_db;User Id=your_user;Password=your_password;";
        using (SqlConnection conn = new SqlConnection(connString))
        {
            try
            {
                conn.Open();
                Console.WriteLine("Connection Opened Successfully!");
            }
            catch (Exception ex)
            {
                Console.WriteLine("Error: " + ex.Message);
            }
            // No need to call Close() explicitly when using 'using' statement
        }
    }
}
```

### **2. Command Class (`SqlCommand`, `OleDbCommand`)**

The **Command class** is used to execute SQL queries or stored procedures on a database.

#### **Key Properties:**

- `CommandText` – Holds the SQL query or stored procedure name.
- `CommandType` – Specifies whether the command is a `Text` (SQL query) or `StoredProcedure`.
- `Connection` – Represents the `SqlConnection` or `OleDbConnection` used.

#### **Key Methods:**

- `ExecuteReader()` – Returns a `DataReader` for reading data.
- `ExecuteScalar()` – Returns a single value from a query (e.g., COUNT, SUM).
- `ExecuteNonQuery()` – Executes queries like `INSERT`, `UPDATE`, `DELETE` and returns affected rows count.

#### **Example using `SqlCommand`**

```csharp
using System;
using System.Data.SqlClient;

class Program
{
    static void Main()
    {
        string connString = "Server=your_server;Database=your_db;User Id=your_user;Password=your_password;";
        using (SqlConnection conn = new SqlConnection(connString))
        {
            conn.Open();
            string query = "INSERT INTO Employees (Name, Age) VALUES ('John Doe', 30)";

            using (SqlCommand cmd = new SqlCommand(query, conn))
            {
                int rowsAffected = cmd.ExecuteNonQuery();
                Console.WriteLine($"{rowsAffected} row(s) inserted.");
            }
        }
    }
}
```

### **3. DataAdapter Class (`SqlDataAdapter`, `OleDbDataAdapter`)**

The **DataAdapter class** acts as a bridge between a `DataSet` and a database. It allows data retrieval and updating without keeping the connection open.

#### **Key Methods:**

- `Fill(DataSet)` – Fills a `DataSet` with data from the database.
- `Update(DataSet)` – Sends changes from the `DataSet` back to the database.

#### **Example using `SqlDataAdapter`**

```csharp
using System;
using System.Data;
using System.Data.SqlClient;

class Program
{
    static void Main()
    {
        string connString = "Server=your_server;Database=your_db;User Id=your_user;Password=your_password;";
        using (SqlConnection conn = new SqlConnection(connString))
        {
            conn.Open();
            string query = "SELECT * FROM Employees";

            SqlDataAdapter adapter = new SqlDataAdapter(query, conn);
            DataSet ds = new DataSet();

            adapter.Fill(ds, "Employees");

            foreach (DataRow row in ds.Tables["Employees"].Rows)
            {
                Console.WriteLine($"ID: {row["ID"]}, Name: {row["Name"]}, Age: {row["Age"]}");
            }
        }
    }
}
```

### **Summary**

| **Class**                             | **Purpose**                                                                  |
| ------------------------------------- | ---------------------------------------------------------------------------- |
| `SqlConnection` / `OleDbConnection`   | Establishes and manages a database connection.                               |
| `SqlCommand` / `OleDbCommand`         | Executes SQL queries (SELECT, INSERT, UPDATE, DELETE).                       |
| `SqlDataAdapter` / `OleDbDataAdapter` | Retrieves and updates data in a `DataSet` without keeping a connection open. |

---

## **Creating a Connection to a Database in ADO.NET**

To connect to a database using ADO.NET, we use the `SqlConnection` class for SQL Server or `OleDbConnection` for other databases like MS Access or Excel. Below are examples of how to establish a connection.

### **1. Connecting to a SQL Server Database**

#### **Using `SqlConnection`**

```csharp
using System;
using System.Data.SqlClient;

class Program
{
    static void Main()
    {
        // Connection string (Replace with your actual server details)
        string connString = "Server=your_server;Database=your_db;User Id=your_user;Password=your_password;";

        // Create a connection object
        using (SqlConnection conn = new SqlConnection(connString))
        {
            try
            {
                conn.Open(); // Open the connection
                Console.WriteLine("Connection to SQL Server database successful!");
            }
            catch (Exception ex)
            {
                Console.WriteLine("Error: " + ex.Message);
            }
        } // Connection automatically closed when using 'using' statement
    }
}
```

🔹 **Key Points:**

- `SqlConnection` manages the connection to a SQL Server database.
- Always use `using` to ensure the connection is closed properly.
- The connection string contains **Server name, Database name, User ID, and Password**.

### **2. Connecting to an MS Access Database (`.accdb` or `.mdb`)**

#### **Using `OleDbConnection`**

```csharp
using System;
using System.Data.OleDb;

class Program
{
    static void Main()
    {
        // Connection string for an MS Access database (.accdb for newer versions, .mdb for older versions)
        string connString = "Provider=Microsoft.ACE.OLEDB.12.0;Data Source=C:\\Path\\To\\YourDatabase.accdb;";

        using (OleDbConnection conn = new OleDbConnection(connString))
        {
            try
            {
                conn.Open();
                Console.WriteLine("Connected to MS Access database!");
            }
            catch (Exception ex)
            {
                Console.WriteLine("Error: " + ex.Message);
            }
        }
    }
}
```

🔹 **Key Points:**

- `OleDbConnection` is used for Access databases.
- Replace `"C:\\Path\\To\\YourDatabase.accdb"` with the actual path to your Access database file.

### **3. Connecting to a MySQL Database**

#### **Using `MySqlConnection` (Requires `MySql.Data` NuGet Package)**

```csharp
using System;
using MySql.Data.MySqlClient;

class Program
{
    static void Main()
    {
        // Connection string for MySQL
        string connString = "Server=your_server;Database=your_db;User Id=your_user;Password=your_password;";

        using (MySqlConnection conn = new MySqlConnection(connString))
        {
            try
            {
                conn.Open();
                Console.WriteLine("Connected to MySQL database!");
            }
            catch (Exception ex)
            {
                Console.WriteLine("Error: " + ex.Message);
            }
        }
    }
}
```

🔹 **Key Points:**

- Requires `MySql.Data` package (`Install-Package MySql.Data` via NuGet).
- Use `MySqlConnection` for MySQL databases.

### **4. Connecting to an Oracle Database**

#### **Using `OracleConnection` (Requires `Oracle.ManagedDataAccess` NuGet Package)**

```csharp
using System;
using Oracle.ManagedDataAccess.Client;

class Program
{
    static void Main()
    {
        // Connection string for Oracle
        string connString = "User Id=your_user;Password=your_password;Data Source=your_oracle_db";

        using (OracleConnection conn = new OracleConnection(connString))
        {
            try
            {
                conn.Open();
                Console.WriteLine("Connected to Oracle database!");
            }
            catch (Exception ex)
            {
                Console.WriteLine("Error: " + ex.Message);
            }
        }
    }
}
```

🔹 **Key Points:**

- Requires `Oracle.ManagedDataAccess` package (`Install-Package Oracle.ManagedDataAccess`).
- Uses `OracleConnection` for connecting to Oracle databases.

### **Best Practices for Database Connections**

✅ **Use `using` statements** – Ensures the connection is closed automatically.  
✅ **Handle exceptions properly** – Always wrap in `try-catch` to prevent crashes.  
✅ **Use parameterized queries** – Prevents SQL injection (avoid directly embedding user input in SQL queries).  
✅ **Keep connection strings secure** – Store in `app.config` or environment variables instead of hardcoding.

---

## **Displaying a DataSet in a GridView (C# with ASP.NET & Windows Forms)**

A `DataSet` in ADO.NET is an in-memory representation of data that can be displayed in UI controls like `GridView` in ASP.NET or `DataGridView` in Windows Forms.

### **1. Displaying Data in ASP.NET GridView**

#### **Steps:**

1. Create an ASP.NET Web Application.
2. Use a `GridView` control in the `.aspx` page.
3. Fetch data using `SqlDataAdapter` and bind it to the `GridView`.

#### **ASP.NET Markup (`Default.aspx`)**

```html
<asp:GridView
  ID="GridView1"
  runat="server"
  AutoGenerateColumns="true"
  BorderColor="Black"
  BorderWidth="1px"
/>
```

#### **Code-Behind (`Default.aspx.cs`)**

```csharp
using System;
using System.Data;
using System.Data.SqlClient;
using System.Web.UI.WebControls;

public partial class _Default : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        if (!IsPostBack)
        {
            BindGrid();
        }
    }

    private void BindGrid()
    {
        string connString = "Server=your_server;Database=your_db;User Id=your_user;Password=your_password;";
        using (SqlConnection conn = new SqlConnection(connString))
        {
            SqlDataAdapter da = new SqlDataAdapter("SELECT * FROM Employees", conn);
            DataSet ds = new DataSet();
            da.Fill(ds);

            GridView1.DataSource = ds;
            GridView1.DataBind();
        }
    }
}
```

#### **Explanation:**

- `GridView1.DataSource = ds;` – Binds the dataset to the GridView.
- `GridView1.DataBind();` – Refreshes the GridView to display data.
- The `if (!IsPostBack)` condition ensures data loads only once on the first request.

### **2. Displaying Data in Windows Forms `DataGridView`**

#### **Steps:**

1. Create a **Windows Forms Application**.
2. Add a `DataGridView` control (`dataGridView1`) to the form.
3. Fetch and display data from a `DataSet`.

#### **Code (`Form1.cs`)**

```csharp
using System;
using System.Data;
using System.Data.SqlClient;
using System.Windows.Forms;

public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        LoadData();
    }

    private void LoadData()
    {
        string connString = "Server=your_server;Database=your_db;User Id=your_user;Password=your_password;";
        using (SqlConnection conn = new SqlConnection(connString))
        {
            SqlDataAdapter da = new SqlDataAdapter("SELECT * FROM Employees", conn);
            DataSet ds = new DataSet();
            da.Fill(ds, "Employees");

            dataGridView1.DataSource = ds.Tables["Employees"];
        }
    }
}
```

#### **Explanation:**

- `dataGridView1.DataSource = ds.Tables["Employees"];` – Assigns the data to the `DataGridView`.
- Uses `SqlDataAdapter` to fetch data into a `DataSet`.
- `LoadData()` is called in the constructor to populate data when the form loads.

### **Summary**

| **Platform**  | **Control**    | **Binding Method**                     |
| ------------- | -------------- | -------------------------------------- |
| ASP.NET Web   | `GridView`     | `DataSource = ds; DataBind();`         |
| Windows Forms | `DataGridView` | `DataSource = ds.Tables["TableName"];` |

---

## **Accessing Data with Data Readers in ADO.NET**

A **DataReader** is a fast, forward-only, read-only way of accessing data from a database in ADO.NET. It is ideal for retrieving large amounts of data efficiently because it does not store the data in memory like a `DataSet` does.

### **1. Using `SqlDataReader` for SQL Server**

The `SqlDataReader` class is used to read data row by row from a SQL Server database.

#### **Example: Reading Data Using `SqlDataReader`**

```csharp
using System;
using System.Data.SqlClient;

class Program
{
    static void Main()
    {
        string connString = "Server=your_server;Database=your_db;User Id=your_user;Password=your_password;";
        using (SqlConnection conn = new SqlConnection(connString))
        {
            conn.Open();
            string query = "SELECT ID, Name, Age FROM Employees";

            using (SqlCommand cmd = new SqlCommand(query, conn))
            {
                using (SqlDataReader reader = cmd.ExecuteReader())
                {
                    while (reader.Read()) // Reads data row by row
                    {
                        Console.WriteLine($"ID: {reader["ID"]}, Name: {reader["Name"]}, Age: {reader["Age"]}");
                    }
                }
            }
        }
    }
}
```

#### **Explanation:**

- `ExecuteReader()` – Executes a SQL query and returns a `SqlDataReader`.
- `reader.Read()` – Moves to the next record (returns `false` when no more rows exist).
- `reader["ColumnName"]` – Fetches data by column name.

### **2. Using `OleDbDataReader` for MS Access & Other Databases**

For MS Access and other OLE DB-supported databases, use `OleDbDataReader`.

#### **Example: Reading Data from MS Access**

```csharp
using System;
using System.Data.OleDb;

class Program
{
    static void Main()
    {
        string connString = "Provider=Microsoft.ACE.OLEDB.12.0;Data Source=C:\\Path\\To\\YourDatabase.accdb;";

        using (OleDbConnection conn = new OleDbConnection(connString))
        {
            conn.Open();
            string query = "SELECT ID, Name, Age FROM Employees";

            using (OleDbCommand cmd = new OleDbCommand(query, conn))
            {
                using (OleDbDataReader reader = cmd.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        Console.WriteLine($"ID: {reader["ID"]}, Name: {reader["Name"]}, Age: {reader["Age"]}");
                    }
                }
            }
        }
    }
}
```

#### **Differences from `SqlDataReader`:**

- Uses `OleDbConnection` instead of `SqlConnection`.
- Uses `OleDbCommand` instead of `SqlCommand`.

### **3. Fetching Data with Index-Based Access (Better Performance)**

Instead of accessing columns by name (`reader["ColumnName"]`), you can use an index (`reader[0]`).

#### **Example: Using Column Indexes**

```csharp
while (reader.Read())
{
    int id = reader.GetInt32(0);       // First column (ID)
    string name = reader.GetString(1); // Second column (Name)
    int age = reader.GetInt32(2);      // Third column (Age)

    Console.WriteLine($"ID: {id}, Name: {name}, Age: {age}");
}
```

🔹 **Pros:** Faster performance since no string lookup is required.  
🔹 **Cons:** Less readable, requires knowing column positions.

### **4. Checking for NULL Values**

If a column can contain `NULL`, use `IsDBNull()` to avoid exceptions.

#### **Example: Handling NULL Values**

```csharp
while (reader.Read())
{
    int id = reader.GetInt32(0);
    string name = reader.IsDBNull(1) ? "No Name" : reader.GetString(1);
    int age = reader.IsDBNull(2) ? 0 : reader.GetInt32(2);

    Console.WriteLine($"ID: {id}, Name: {name}, Age: {age}");
}
```

### **5. Using `ExecuteScalar()` for Single Value Queries**

If you need a **single value** (like `COUNT(*)`), use `ExecuteScalar()` instead of `ExecuteReader()`.

#### **Example: Getting Employee Count**

```csharp
string query = "SELECT COUNT(*) FROM Employees";
using (SqlCommand cmd = new SqlCommand(query, conn))
{
    int count = (int)cmd.ExecuteScalar();
    Console.WriteLine($"Total Employees: {count}");
}
```

### **Comparison: `SqlDataReader` vs. `DataSet`**

| Feature        | `SqlDataReader`                 | `DataSet`                            |
| -------------- | ------------------------------- | ------------------------------------ |
| Speed          | Faster (Streaming)              | Slower (Stored in memory)            |
| Memory Usage   | Low (Does not store data)       | High (Holds entire data in memory)   |
| Navigation     | Forward-only                    | Random access (Can go back & forth)  |
| Edit Data      | No (Read-only)                  | Yes (Allows modifications)           |
| Ideal Use Case | Large result sets, fast reading | Disconnected data access, UI binding |

### **Best Practices for Using DataReader**

✅ **Always use `using` blocks** – Ensures proper disposal of connections.  
✅ **Check for `NULL` values** – Use `IsDBNull()` to handle missing data.  
✅ **Use indexes instead of column names** for better performance.  
✅ **Close the reader explicitly** if not using `using` (`reader.Close()`).

---

## **Building a Modern, Responsive Single-Page Application (SPA) with ASP.NET Core**

A **Single-Page Application (SPA)** is a web application that loads a single HTML page and dynamically updates content without requiring full page reloads. ASP.NET Core provides several ways to build SPAs, including **Blazor, Angular, React, and Vue**.

### **1. Choosing a Technology Stack**

To build an SPA with ASP.NET Core, you can use:

- **Blazor WebAssembly** – C#-based, no JavaScript required.
- **Angular** – TypeScript-based, scalable.
- **React** – Fast and component-driven.
- **Vue.js** – Lightweight and simple.

Below is **Blazor WebAssembly (C#-based)** and **React with ASP.NET Core API**.

### **2. Creating an SPA with Blazor WebAssembly**

Blazor WebAssembly (WASM) allows running C# code in the browser, eliminating the need for JavaScript.

#### **Step 1: Create a Blazor WebAssembly App**

```sh
dotnet new blazorwasm -o MyBlazorApp
cd MyBlazorApp
dotnet run
```

This starts a **modern, responsive** Blazor SPA.

#### **Step 2: Create an ASP.NET Core Web API**

```sh
dotnet new webapi -o MyBlazorAPI
cd MyBlazorAPI
dotnet run
```

This API provides backend data for the Blazor frontend.

#### **Step 3: Fetch Data in Blazor**

Modify `Pages/FetchData.razor`:

```razor
@page "/fetchdata"
@inject HttpClient Http

<h3>Weather Forecast</h3>

@if (forecasts == null)
{
    <p>Loading...</p>
}
else
{
    <table>
        <thead>
            <tr><th>Date</th><th>Temperature</th><th>Summary</th></tr>
        </thead>
        <tbody>
            @foreach (var forecast in forecasts)
            {
                <tr>
                    <td>@forecast.Date</td>
                    <td>@forecast.TemperatureC °C</td>
                    <td>@forecast.Summary</td>
                </tr>
            }
        </tbody>
    </table>
}

@code {
    private WeatherForecast[] forecasts;

    protected override async Task OnInitializedAsync()
    {
        forecasts = await Http.GetFromJsonAsync<WeatherForecast[]>("https://localhost:5001/weatherforecast");
    }
}
```

#### **Step 4: Run the App**

- Run `dotnet run` for both **API** and **Blazor**.
- Visit `http://localhost:5000`.

### **3. Creating an SPA with React and ASP.NET Core**

If you prefer JavaScript, you can use React with ASP.NET Core.

#### **Step 1: Create a React + ASP.NET Core App**

```sh
dotnet new react -o MyReactApp
cd MyReactApp
dotnet run
```

This command sets up a **React frontend** and an **ASP.NET Core backend**.

#### **Step 2: Create an API Controller (`WeatherForecastController.cs`)**

```csharp
[Route("api/weather")]
[ApiController]
public class WeatherForecastController : ControllerBase
{
    private static readonly string[] Summaries = new[]
    {
        "Freezing", "Bracing", "Chilly", "Mild", "Warm", "Hot", "Sweltering"
    };

    [HttpGet]
    public IEnumerable<WeatherForecast> Get()
    {
        return Enumerable.Range(1, 5).Select(index => new WeatherForecast
        {
            Date = DateTime.Now.AddDays(index),
            TemperatureC = Random.Shared.Next(-20, 55),
            Summary = Summaries[Random.Shared.Next(Summaries.Length)]
        })
        .ToArray();
    }
}
```

#### **Step 3: Fetch Data in React**

Modify `src/components/Weather.js`:

```javascript
import React, { useEffect, useState } from "react";

function Weather() {
  const [weather, setWeather] = useState([]);

  useEffect(() => {
    fetch("/api/weather")
      .then((response) => response.json())
      .then((data) => setWeather(data));
  }, []);

  return (
    <div>
      <h3>Weather Forecast</h3>
      <table>
        <thead>
          <tr>
            <th>Date</th>
            <th>Temp (°C)</th>
            <th>Summary</th>
          </tr>
        </thead>
        <tbody>
          {weather.map((item, index) => (
            <tr key={index}>
              <td>{item.date}</td>
              <td>{item.temperatureC}</td>
              <td>{item.summary}</td>
            </tr>
          ))}
        </tbody>
      </table>
    </div>
  );
}

export default Weather;
```

#### **Step 4: Run the React SPA**

```sh
cd ClientApp
npm start
```

Visit `http://localhost:3000` to see the React SPA.

### **4. Deploying the SPA**

For production, build the frontend and serve it from ASP.NET Core.

#### **Step 1: Build React**

```sh
npm run build
```

Copy the `build/` folder to `wwwroot/`.

#### **Step 2: Serve from ASP.NET Core**

Modify `Startup.cs`:

```csharp
app.UseStaticFiles();
app.UseSpa(spa =>
{
    spa.Options.SourcePath = "ClientApp";
});
```

#### **Step 3: Publish**

```sh
dotnet publish -c Release
```

### **5. Conclusion**

| **Feature**    | **Blazor WebAssembly**            | **React + ASP.NET Core** |
| -------------- | --------------------------------- | ------------------------ |
| Language       | C# (No JavaScript)                | JavaScript / TypeScript  |
| Performance    | Slower Initial Load (WebAssembly) | Faster Initial Load      |
| Learning Curve | Easier for .NET Devs              | Easier for JS Devs       |
| Ecosystem      | .NET Libraries                    | NPM Packages             |
| Mobile Support | Limited (PWA possible)            | Excellent (React Native) |

### **When to Use What?**

- Use **Blazor WebAssembly** if you prefer **C# over JavaScript**.
- Use **React/Angular** if you want **better mobile support** and an **active JavaScript ecosystem**.

---

## **Understanding MVC and MVVM Design Patterns**

Both **Model-View-Controller (MVC)** and **Model-View-ViewModel (MVVM)** are architectural patterns used to **separate concerns** in application development. They help in **maintaining clean code, reusability, and better scalability**.

### **1. Model-View-Controller (MVC)**

#### **What is MVC?**

MVC is a **design pattern** used mainly for web applications. It divides the application into three interconnected components:

1. **Model** – Represents data and business logic.
2. **View** – Displays UI elements and data to the user.
3. **Controller** – Handles user inputs, processes data, and updates the view.

#### **Diagram of MVC Architecture**

```
User → Controller → Model → View → User
```

#### **Example: MVC in ASP.NET Core**

##### **Step 1: Create an ASP.NET Core MVC Project**

```sh
dotnet new mvc -o MyMVCApp
cd MyMVCApp
dotnet run
```

##### **Step 2: Define a Model (`Models/Employee.cs`)**

```csharp
public class Employee
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Department { get; set; }
}
```

##### **Step 3: Create a Controller (`Controllers/EmployeeController.cs`)**

```csharp
using Microsoft.AspNetCore.Mvc;
using System.Collections.Generic;

public class EmployeeController : Controller
{
    public IActionResult Index()
    {
        var employees = new List<Employee>
        {
            new Employee { Id = 1, Name = "Alice", Department = "IT" },
            new Employee { Id = 2, Name = "Bob", Department = "HR" }
        };

        return View(employees);
    }
}
```

##### **Step 4: Create a View (`Views/Employee/Index.cshtml`)**

```html
@model List<Employee>
  <h2>Employee List</h2>
  <table>
    <tr>
      <th>ID</th>
      <th>Name</th>
      <th>Department</th>
    </tr>
    @foreach (var emp in Model) {
    <tr>
      <td>@emp.Id</td>
      <td>@emp.Name</td>
      <td>@emp.Department</td>
    </tr>
    }
  </table></Employee
>
```

#### **How MVC Works in ASP.NET Core**

1. **User Requests Data** → `Controller` (`EmployeeController`)
2. **Controller Fetches Data** → `Model` (`Employee`)
3. **Data is Passed to View** → `Index.cshtml` displays employee data.

✅ **Best For**: Web applications, APIs  
✅ **Pros**: Separation of concerns, testability  
✅ **Cons**: Complex for small projects

### **2. Model-View-ViewModel (MVVM)**

#### **What is MVVM?**

MVVM is mainly used for **desktop, mobile, and frontend-heavy applications** (e.g., WPF, Xamarin, Blazor). It provides **better data binding and state management**.

#### **MVVM Components**

1. **Model** – Represents business logic and data.
2. **View** – Represents the UI.
3. **ViewModel** – Acts as a bridge between Model and View (handles UI logic).

#### **Diagram of MVVM Architecture**

```
User → View → ViewModel ↔ Model
```

#### **Example: MVVM in WPF (C#)**

##### **Step 1: Create a Model (`Models/Employee.cs`)**

```csharp
public class Employee
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Department { get; set; }
}
```

##### **Step 2: Create a ViewModel (`ViewModels/EmployeeViewModel.cs`)**

```csharp
using System.Collections.ObjectModel;

public class EmployeeViewModel
{
    public ObservableCollection<Employee> Employees { get; set; }

    public EmployeeViewModel()
    {
        Employees = new ObservableCollection<Employee>
        {
            new Employee { Id = 1, Name = "Alice", Department = "IT" },
            new Employee { Id = 2, Name = "Bob", Department = "HR" }
        };
    }
}
```

##### **Step 3: Bind Data in the View (`Views/MainWindow.xaml`)**

```xml
<Window x:Class="MVVMApp.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="Employee List">

    <Window.DataContext>
        <local:EmployeeViewModel />
    </Window.DataContext>

    <Grid>
        <ListView ItemsSource="{Binding Employees}">
            <ListView.View>
                <GridView>
                    <GridViewColumn Header="ID" DisplayMemberBinding="{Binding Id}" />
                    <GridViewColumn Header="Name" DisplayMemberBinding="{Binding Name}" />
                    <GridViewColumn Header="Department" DisplayMemberBinding="{Binding Department}" />
                </GridView>
            </ListView.View>
        </ListView>
    </Grid>
</Window>
```

#### **How MVVM Works in WPF**

1. **User Interacts with UI (`View`)**
2. **`ViewModel` Fetches and Updates Data (`ObservableCollection<Employee>`)**
3. **View Updates Automatically via Data Binding**

✅ **Best For**: WPF, Xamarin, Blazor  
✅ **Pros**: Better separation, two-way data binding, reusability  
✅ **Cons**: Can be complex for simple UI

### **3. MVC vs MVVM: Which One to Use?**

| Feature              | MVC (Model-View-Controller)              | MVVM (Model-View-ViewModel)                  |
| -------------------- | ---------------------------------------- | -------------------------------------------- |
| **Usage**            | Web Applications (ASP.NET, Java, Django) | Desktop & Mobile Apps (WPF, Xamarin, Blazor) |
| **Data Binding**     | Manual (Controller passes data)          | Automatic (Two-way data binding)             |
| **State Management** | Controller manages state                 | ViewModel manages state                      |
| **UI Complexity**    | Easier for web apps                      | Better for complex UIs                       |
| **Performance**      | Faster for web apps                      | More responsive UI                           |

### **4. When to Choose MVC or MVVM?**

- **Use MVC** when developing **web applications** with **ASP.NET Core, Django, Spring Boot**.
- **Use MVVM** when developing **desktop applications (WPF, Xamarin, Blazor)** with **complex UI interactions**.

---

## **`Gagan Saini`**
