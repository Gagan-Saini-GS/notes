# Unit-1

## Basic Internet

### **Overview of the Internet**

The **Internet** is a global network of interconnected computers that communicate using standardized protocols. It enables data exchange, communication, and access to information. The internet supports various services such as email, web browsing, social media, cloud computing, and online transactions.

### **Evolution of the Internet**

The internet has evolved through several stages:

1. **ARPANET (1960s-1980s)**
   - Developed by the U.S. Department of Defense's ARPA (Advanced Research Projects Agency).
   - Introduced packet switching and TCP/IP protocol.
2. **Expansion to Universities (1980s)**

   - Used by academic institutions for research and data sharing.
   - Birth of the **Domain Name System (DNS)** in 1983.

3. **Commercialization & WWW (1990s)**

   - The **World Wide Web (WWW)** was invented by **Tim Berners-Lee** in 1989.
   - First web browser (**Mosaic**) was developed.
   - Internet Service Providers (ISPs) made internet access available to the public.

4. **Broadband & Mobile Internet (2000s-2010s)**

   - Introduction of high-speed broadband and wireless networks.
   - Rise of social media, cloud computing, and e-commerce.

5. **IoT, 5G & AI-driven Internet (2020s-Present)**
   - **5G** networks enhance speed and connectivity.
   - The **Internet of Things (IoT)** connects smart devices.
   - **Artificial Intelligence (AI)** enhances automation and cybersecurity.

### **Concepts of the Internet & WWW**

1. **Internet vs. WWW**

   - The **Internet** is the infrastructure (network of networks).
   - The **WWW (World Wide Web)** is an application that runs on the internet, consisting of websites and web pages accessed via web browsers.

2. **Key Concepts:**
   - **IP Address:** A unique identifier for devices on the internet.
   - **DNS (Domain Name System):** Converts domain names (e.g., google.com) into IP addresses.
   - **Web Browsers:** Software for accessing the WWW (e.g., Chrome, Firefox).
   - **Search Engines:** Help users find information (e.g., Google, Bing).
   - **Web Hosting:** Services that store website files.

### **Introduction to TCP/IP**

**TCP/IP (Transmission Control Protocol/Internet Protocol)** is the foundation of internet communication. It defines how data is sent, transmitted, and received over networks.

#### **Key Components of TCP/IP:**

1. **Internet Protocol (IP)**

   - Responsible for addressing and routing packets between devices.
   - Uses IPv4 (32-bit) and IPv6 (128-bit) addresses.

2. **Transmission Control Protocol (TCP)**

   - Ensures reliable data transmission by establishing a connection, managing data flow, and handling errors.

3. **Other Supporting Protocols:**
   - **HTTP/HTTPS:** Used for web communication.
   - **FTP:** Used for file transfer.
   - **SMTP/POP3/IMAP:** Used for email communication.

### **Conclusion**

The internet has transformed communication, business, and technology. Understanding its evolution, key concepts, and the role of TCP/IP helps in comprehending how it operates and continues to grow.

---

## HTML

### **HTML Elements**

HTML (**HyperText Markup Language**) elements are the building blocks of web pages. An HTML element consists of a **start tag**, **content**, and an **end tag**.

#### **Types of HTML Elements:**

1. **Structural Elements:**

   - `<html>`: Defines the root of an HTML document.
   - `<head>`: Contains metadata and links to styles/scripts.
   - `<body>`: Contains the visible page content.

2. **Text Formatting Elements:**

   - `<h1>` to `<h6>`: Headings.
   - `<p>`: Paragraph.
   - `<b>`, `<strong>`: Bold text.
   - `<i>`, `<em>`: Italicized text.
   - `<u>`: Underlined text.

3. **List Elements:**

   - `<ul>`: Unordered list.
   - `<ol>`: Ordered list.
   - `<li>`: List item.

4. **Table Elements:**

   - `<table>`: Creates a table.
   - `<tr>`: Table row.
   - `<td>`: Table data/cell.
   - `<th>`: Table header.

5. **Link and Media Elements:**
   - `<a>`: Creates hyperlinks.
   - `<img>`: Displays images.
   - `<video>`, `<audio>`: Embeds media.

### **Semantic Elements**

Semantic elements in HTML **provide meaning** to the structure of a webpage. They improve readability, accessibility, and SEO.

#### **Common Semantic Elements:**

1. **Structural Elements:**

   - `<header>`: Defines the page or section header.
   - `<nav>`: Contains navigation links.
   - `<section>`: Defines a section of the document.
   - `<article>`: Represents self-contained content (e.g., blog post).
   - `<aside>`: Contains side content like ads or widgets.
   - `<footer>`: Defines the footer of a page or section.

2. **Text-related Elements:**
   - `<mark>`: Highlights text.
   - `<time>`: Represents a date/time value.
   - `<figure>`: Groups media elements like images.
   - `<figcaption>`: Provides a caption for `<figure>`.

#### **Benefits of Semantic Elements:**

✅ **Better SEO** – Search engines understand the structure.  
✅ **Accessibility** – Screen readers can interpret content better.  
✅ **Maintainability** – Easier to read and edit code.

### **HTML Forms**

HTML forms allow users to input data, which can be sent to a server for processing.

#### **Basic Structure of a Form:**

```html
<form action="submit.php" method="POST">
  <label for="name">Name:</label>
  <input type="text" id="name" name="name" required />

  <label for="email">Email:</label>
  <input type="email" id="email" name="email" required />

  <input type="submit" value="Submit" />
</form>
```

#### **Common Form Elements:**

- `<input>`: Accepts user input (text, email, password, checkbox, radio, etc.).
- `<textarea>`: Multi-line text input.
- `<select>`: Drop-down menu.
- `<option>`: Options within `<select>`.
- `<button>`: Clickable button.
- `<label>`: Describes form controls for accessibility.

#### **Form Attributes:**

- `action` – Specifies where the form data should be sent.
- `method` – Defines the HTTP method (`GET` or `POST`).
- `required` – Ensures a field must be filled before submission.

---

## CSS

### **Introduction to CSS**

CSS (**Cascading Style Sheets**) is used to style and layout web pages. It allows control over colors, fonts, spacing, animations, and responsive designs.

#### **Ways to Apply CSS:**

1. **Inline CSS:** Applied directly in the HTML element.
   ```html
   <p style="color: blue;">This is blue text.</p>
   ```
2. **Internal CSS:** Defined within the `<style>` tag inside the `<head>`.
   ```html
   <style>
     p {
       color: blue;
     }
   </style>
   ```
3. **External CSS:** Written in a separate `.css` file and linked using `<link>`.
   ```html
   <link rel="stylesheet" href="styles.css" />
   ```

### **CSS Selectors**

Selectors are used to target HTML elements.

1. **Basic Selectors:**

   - `*` → Universal selector (targets all elements).
   - `p` → Element selector (targets all `<p>` elements).
   - `.class` → Class selector (targets elements with the class).
   - `#id` → ID selector (targets a specific element by ID).

2. **Combinators:**

   - `div p` → Descendant selector (targets `<p>` inside `<div>`).
   - `div > p` → Child selector (direct children only).
   - `div + p` → Adjacent sibling (immediately follows `<div>`).
   - `div ~ p` → General sibling (follows `<div>` but not necessarily immediate).

3. **Attribute Selectors:**
   - `[type="text"]` → Targets `<input type="text">`.
   - `[href^="https"]` → Targets links starting with "https".

### **Styling Elements**

- `color` → Text color.
- `background-color` → Background color.
- `width`, `height` → Set element size.
- `margin`, `padding` → Control spacing.
- `display` → Defines element display (`block`, `inline`, `flex`).

### **Borders in CSS**

Borders define the outline of an element.

```css
div {
  border: 2px solid black;
  border-radius: 10px;
}
```

- `solid`, `dashed`, `dotted`, `double` → Border styles.
- `border-radius` → Rounds corners.

### **Backgrounds in CSS**

Used to set images, colors, or gradients as the background.

```css
body {
  background-color: lightblue;
  background-image: url("image.jpg");
  background-size: cover;
  background-repeat: no-repeat;
}
```

- `background-image` → Sets an image.
- `background-size: cover;` → Ensures full coverage.
- `background-attachment: fixed;` → Makes the background fixed while scrolling.

### **Text Effects in CSS**

Used to add styles to text.

```css
h1 {
  text-shadow: 2px 2px 5px gray;
  letter-spacing: 2px;
}
```

- `text-shadow` → Adds shadow to text.
- `letter-spacing` → Adjusts space between letters.
- `word-spacing` → Adjusts space between words.

### **Text Styling in CSS**

```css
p {
  text-align: center;
  text-transform: uppercase;
  line-height: 1.5;
}
```

- `text-align` → Aligns text (`left`, `right`, `center`, `justify`).
- `text-transform` → Changes text case (`uppercase`, `lowercase`).
- `line-height` → Adjusts line spacing.

### **Fonts in CSS**

Used to customize text appearance.

```css
p {
  font-family: "Arial", sans-serif;
  font-size: 16px;
  font-weight: bold;
}
```

- `font-family` → Defines the font.
- `font-size` → Controls the text size.
- `font-weight` → Adjusts boldness (`normal`, `bold`, `lighter`).

### **CSS Transitions**

Allows smooth property changes over time.

```css
button {
  background-color: blue;
  transition: background-color 0.5s ease-in-out;
}

button:hover {
  background-color: red;
}
```

- `transition-property` → Specifies the property to animate.
- `transition-duration` → Time taken for the transition.
- `transition-timing-function` → Controls speed (`ease`, `linear`).

### **CSS Transforms**

Used to rotate, scale, skew, or translate elements.

```css
div {
  transform: rotate(45deg);
  transform: scale(1.5);
  transform: translate(50px, 20px);
}
```

- `rotate(deg)` → Rotates an element.
- `scale(x, y)` → Resizes an element.
- `translate(x, y)` → Moves an element.

### **CSS Animations**

Allows elements to animate without JavaScript.

```css
@keyframes slide {
  from {
    left: 0px;
  }
  to {
    left: 100px;
  }
}

div {
  position: relative;
  animation: slide 2s infinite alternate;
}
```

- `@keyframes` → Defines the animation steps.
- `animation-name`, `animation-duration` → Apply the animation.

### **Multiple Columns in CSS**

Used to create multi-column layouts.

```css
div {
  column-count: 3;
  column-gap: 20px;
}
```

- `column-count` → Number of columns.
- `column-gap` → Space between columns.

### **CSS User Interface (UI) Styling**

Enhances the look of UI elements.

```css
button {
  cursor: pointer;
  outline: none;
  user-select: none;
}
```

- `cursor` → Changes mouse pointer (`pointer`, `crosshair`).
- `outline` → Removes focus outline.
- `user-select` → Prevents text selection.

### **CSS Filters**

Used to apply effects like blur, brightness, contrast, etc.

```css
img {
  filter: grayscale(100%);
}
```

- `blur(px)` → Blurs an image.
- `grayscale(%)` → Converts to grayscale.
- `brightness(%)` → Adjusts brightness.

---

## **Web Servers**

A **web server** is software and hardware that serves web pages to users over the internet or an intranet. It processes requests via **HTTP (Hypertext Transfer Protocol)** and delivers web content such as HTML pages, images, and other media files.

### **Popular Web Servers:**

1. **Apache HTTP Server** – Open-source and widely used.
2. **NGINX** – Known for speed and load balancing.
3. **Microsoft IIS (Internet Information Services)** – Windows-based web server.
4. **LiteSpeed** – High-performance alternative to Apache.

### **System Architecture of Web Servers**

Web servers operate on a **client-server model**, where the client (browser) sends requests, and the server processes and responds with the requested resources.

### **Components of Web Server Architecture:**

1. **Client (User Browser)** – Requests web pages (e.g., Chrome, Firefox).
2. **Web Server** – Processes HTTP requests and delivers responses.
3. **Application Server (Optional)** – Executes backend logic (e.g., PHP, Java, Node.js).
4. **Database Server** – Stores and manages data (e.g., MySQL, PostgreSQL).

### **Types of Web Server Architectures:**

- **Single-tier Architecture:** Web server and database on the same machine.
- **Two-tier Architecture:** Web server and database are separate.
- **Three-tier Architecture:** Includes a separate application layer for business logic.
- **Distributed Architecture:** Load balancers distribute traffic among multiple servers.

### **Configuring and Accessing IIS Web Server**

**IIS (Internet Information Services)** is a web server by Microsoft for hosting websites on **Windows Server** or **Windows 10/11 Pro**.

#### **Steps to Install and Configure IIS:**

##### **1. Install IIS on Windows**

1. Open **Control Panel** → **Programs and Features** → **Turn Windows features on or off**.
2. Check **Internet Information Services (IIS)** and click **OK**.
3. Wait for the installation to complete.

##### **2. Access IIS Manager**

1. Press `Win + R`, type `inetmgr`, and press **Enter**.
2. IIS Manager will open, allowing you to configure websites.

##### **3. Configure a Website on IIS**

1. Open **IIS Manager**.
2. Expand **Sites** → Right-click **Default Web Site** → Select **Manage Website > Advanced Settings**.
3. To create a new site:
   - Right-click **Sites** → **Add Website**.
   - Enter **Site Name**, **Physical Path** (folder containing web files), and **Port (80/443)**.
   - Click **OK** to create the site.

##### **4. Accessing IIS Web Server**

- Open a browser and enter:
  ```
  http://localhost
  ```
  or
  ```
  http://<your-server-ip>
  ```
- If configured correctly, the IIS default page or your website should load.

##### **5. Enabling HTTPS (SSL Certificate)**

1. Install an SSL certificate from a Certificate Authority (CA) or generate a self-signed certificate.
2. In IIS Manager, select the site → Click **Bindings** → Add **HTTPS**.
3. Choose the installed certificate and save.

##### **6. Managing IIS Services**

Use **Command Prompt (as Administrator):**

- Start IIS:
  ```sh
  iisreset /start
  ```
- Stop IIS:
  ```sh
  iisreset /stop
  ```
- Restart IIS:
  ```sh
  iisreset
  ```

### **Conclusion**

IIS is a powerful web server for hosting ASP.NET, PHP, and static websites on Windows. It provides an easy-to-use interface for managing websites, security configurations, and performance settings. 🚀

---

## **HTTP and HTTPS Protocols**

### **What is HTTP?**

**HTTP (Hypertext Transfer Protocol)** is the foundation of communication on the web. It is a **stateless**, **application-layer** protocol that enables data exchange between web clients (browsers) and web servers.

- **Default Port:** **80**
- **Uses:** Web browsing, APIs, file transfer
- **Drawback:** Data is transmitted in plain text, making it insecure

### **What is HTTPS?**

**HTTPS (Hypertext Transfer Protocol Secure)** is a secure version of HTTP that encrypts data using **SSL/TLS (Secure Sockets Layer/Transport Layer Security)** to prevent interception and attacks.

- **Default Port:** **443**
- **Uses:** Secure transactions (e.g., banking, e-commerce, login pages)
- **Benefit:** Protects data from hackers by encrypting communication

### **Key Differences Between HTTP and HTTPS**

| Feature     | HTTP                             | HTTPS                    |
| ----------- | -------------------------------- | ------------------------ |
| Security    | Not encrypted (vulnerable)       | Encrypted using SSL/TLS  |
| Port        | 80                               | 443                      |
| URL Prefix  | `http://`                        | `https://`               |
| Data Safety | Prone to interception            | Secure from hackers      |
| SEO Impact  | Less preferred by search engines | Boosts ranking in Google |

### **HTTP Request and Response**

When a client (browser) communicates with a server, it follows the **request-response cycle**.

#### **1. HTTP Request**

A **request** is sent from the client to the server to fetch a resource (e.g., webpage, image).

##### **Request Structure:**

1. **Request Line:** Specifies the HTTP method, URL, and version
   ```
   GET /index.html HTTP/1.1
   ```
2. **Headers:** Contains metadata (e.g., user-agent, host, content-type)
   ```
   Host: www.example.com
   User-Agent: Mozilla/5.0
   ```
3. **Body (Optional):** Contains data in POST/PUT requests

##### **Common HTTP Methods:**

| Method     | Description                                      |
| ---------- | ------------------------------------------------ |
| **GET**    | Requests data from a server (read-only)          |
| **POST**   | Sends data to the server (e.g., form submission) |
| **PUT**    | Updates an existing resource                     |
| **DELETE** | Removes a resource from the server               |
| **HEAD**   | Retrieves headers without the response body      |

#### **2. HTTP Response**

The **response** is sent from the server to the client after processing the request.

##### **Response Structure:**

1. **Status Line:** Contains the HTTP version, status code, and message
   ```
   HTTP/1.1 200 OK
   ```
2. **Headers:** Metadata about the response
   ```
   Content-Type: text/html
   Content-Length: 1024
   ```
3. **Body:** The actual content (HTML, JSON, etc.)

##### **Common HTTP Status Codes:**

| Code    | Meaning               | Description                    |
| ------- | --------------------- | ------------------------------ |
| **200** | OK                    | Request succeeded              |
| **301** | Moved Permanently     | Redirects to a new URL         |
| **400** | Bad Request           | Client error (invalid request) |
| **401** | Unauthorized          | Authentication required        |
| **403** | Forbidden             | Access denied                  |
| **404** | Not Found             | Resource not found             |
| **500** | Internal Server Error | Server-side issue              |

### **Conclusion**

- **HTTP** is used for normal web communication, while **HTTPS** ensures security through encryption.
- The **request-response model** is essential for web interactions, where clients request resources, and servers respond with data. 🚀

---

## **`Gagan Saini`**
