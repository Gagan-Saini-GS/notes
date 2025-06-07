# Unit 3: Swing and JDBC – In-Depth Notes with Examples

## 1. Swing Classes and GUI Programming

### What is Swing?

- Swing is a part of Java Foundation Classes (JFC) used to create window-based applications.
- It provides a rich set of GUI components that are lightweight (written entirely in Java).
- Package: `javax.swing`

### Common Swing Components

- **JFrame**: Main window container
- **JLabel**: Displays a text or image
- **JTextField**: Single line input box
- **JTextArea**: Multi-line input box
- **JButton**: Clickable button
- **JCheckBox**: Toggle option
- **JRadioButton**: Select one from multiple options
- **JComboBox**: Drop-down list
- **JList**: List of items
- **JMenuBar, JMenu, JMenuItem**: Menu components
- **JDialog**: Popup dialog box

---

## 2. Working with Frame Window

### Creating a Basic JFrame Window

```java
import javax.swing.JFrame;

public class SimpleFrame {
    public static void main(String[] args) {
        JFrame frame = new JFrame("My First Frame");
        frame.setSize(400, 300);       // width=400, height=300
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setVisible(true);        // Make frame visible
    }
}
```

- `setSize()` defines window dimensions.
- `setDefaultCloseOperation()` controls what happens when you close the window.
- `setVisible(true)` shows the frame.

---

## 3. Graphics and Color in Swing

- You can override `paint(Graphics g)` method of a component to draw shapes and colors.

Example:

```java
import javax.swing.*;
import java.awt.*;

public class DrawShapes extends JFrame {
    public DrawShapes() {
        setTitle("Draw Shapes");
        setSize(400, 400);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setVisible(true);
    }

    public void paint(Graphics g) {
        super.paint(g);
        g.setColor(Color.RED);
        g.drawRect(50, 50, 100, 100);  // Draw rectangle
        g.setColor(Color.BLUE);
        g.fillOval(200, 50, 100, 100); // Draw filled oval
    }

    public static void main(String[] args) {
        new DrawShapes();
    }
}
```

---

## 4. Adding Controls to Frame

### Example: Adding Label, TextField, Button

```java
import javax.swing.*;

public class FormExample {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Form Example");
        frame.setLayout(null);  // Use absolute positioning
        frame.setSize(400, 300);

        JLabel label = new JLabel("Name:");
        label.setBounds(50, 50, 80, 30);
        frame.add(label);

        JTextField textField = new JTextField();
        textField.setBounds(130, 50, 150, 30);
        frame.add(textField);

        JButton button = new JButton("Submit");
        button.setBounds(130, 100, 100, 30);
        frame.add(button);

        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setVisible(true);
    }
}
```

---

## 5. Other Controls

- **Checkbox**

```java
JCheckBox cb = new JCheckBox("I Agree");
cb.setBounds(50, 150, 100, 30);
frame.add(cb);
```

- **RadioButton** (Use ButtonGroup to group them)

```java
JRadioButton r1 = new JRadioButton("Male");
r1.setBounds(50, 180, 80, 30);
JRadioButton r2 = new JRadioButton("Female");
r2.setBounds(130, 180, 80, 30);

ButtonGroup bg = new ButtonGroup();
bg.add(r1);
bg.add(r2);

frame.add(r1);
frame.add(r2);
```

- **List**

```java
String[] colors = {"Red", "Green", "Blue"};
JList<String> list = new JList<>(colors);
list.setBounds(50, 220, 100, 60);
frame.add(list);
```

- **ComboBox**

```java
String[] courses = {"CSE", "IT", "ECE"};
JComboBox<String> comboBox = new JComboBox<>(courses);
comboBox.setBounds(200, 220, 100, 30);
frame.add(comboBox);
```

---

## 6. Dialog Box and Menus

### Dialog Box Example

```java
JOptionPane.showMessageDialog(null, "Hello, welcome to Java Swing!");
```

### Menus Example

```java
JMenuBar menuBar = new JMenuBar();

JMenu fileMenu = new JMenu("File");
JMenuItem exitItem = new JMenuItem("Exit");
fileMenu.add(exitItem);

menuBar.add(fileMenu);
frame.setJMenuBar(menuBar);
```

---

## 7. Event Handling

- Events are actions such as button clicks, mouse movements, key presses.
- Swing uses Listeners to handle events.
- Example: Handling button click

```java
button.addActionListener(e -> {
    System.out.println("Button clicked!");
});
```

Or with anonymous inner class:

```java
button.addActionListener(new ActionListener() {
    public void actionPerformed(ActionEvent e) {
        System.out.println("Button clicked!");
    }
});
```

---

# 8. JDBC (Java Database Connectivity)

---

## 8.1 JDBC Overview

- API to connect Java applications with databases.
- Core interfaces/classes: `DriverManager`, `Connection`, `Statement`, `PreparedStatement`, `ResultSet`.
- Supports SQL commands.

---

## 8.2 JDBC Drivers

- **Type 1:** JDBC-ODBC bridge driver (deprecated)
- **Type 2:** Native-API driver
- **Type 3:** Network Protocol driver
- **Type 4:** Thin driver (pure Java, most popular)

---

## 8.3 JDBC Connectivity Steps

1. Load the JDBC Driver class.
2. Create a Connection object.
3. Create a Statement or PreparedStatement.
4. Execute SQL query.
5. Process the ResultSet.
6. Close connections.

---

## 8.4 Example: Connecting to MySQL Database

```java
import java.sql.*;

public class JDBCExample {
    public static void main(String[] args) {
        String url = "jdbc:mysql://localhost:3306/mydatabase";
        String user = "root";
        String password = "password";

        try {
            // Load and register JDBC driver
            Class.forName("com.mysql.cj.jdbc.Driver");

            // Establish connection
            Connection con = DriverManager.getConnection(url, user, password);

            // Create statement
            Statement stmt = con.createStatement();

            // Execute query
            ResultSet rs = stmt.executeQuery("SELECT * FROM students");

            // Process result
            while (rs.next()) {
                int id = rs.getInt("id");
                String name = rs.getString("name");
                System.out.println("ID: " + id + ", Name: " + name);
            }

            // Close connections
            rs.close();
            stmt.close();
            con.close();

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

## 8.5 Using PreparedStatement (Prevent SQL Injection)

```java
String sql = "SELECT * FROM students WHERE id = ?";
PreparedStatement pstmt = con.prepareStatement(sql);
pstmt.setInt(1, 5);
ResultSet rs = pstmt.executeQuery();
```

---

## 8.6 Inserting Data Example

```java
String insertSql = "INSERT INTO students(name, age) VALUES (?, ?)";
PreparedStatement pstmt = con.prepareStatement(insertSql);
pstmt.setString(1, "John");
pstmt.setInt(2, 21);
int rows = pstmt.executeUpdate();
System.out.println(rows + " row(s) inserted.");
```

---

# Summary

- **Swing** provides GUI components for desktop applications in Java.
- **JFrame** is the main window; components like buttons, labels, text fields are added to frames.
- Events like button clicks are handled via listeners.
- **JDBC** allows Java programs to connect and manipulate databases using SQL.
- Steps include loading driver, connecting, creating statement, executing queries, processing results, and closing connections.
- **PreparedStatement** is preferred for safer database queries.
