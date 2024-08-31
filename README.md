




<h2 dir="rtl" align="center">
بسم الله الرحمن الرحيم
</h2>

# IIS Revision

This revision is designed to provide a concise overview of **IIS**, including both basic and some advanced concepts. It is intended especially for web developers and anyone interested in **IIS**. Let's start.

Before learning **What is IIS**, we need to understand **What is a Web Server**.

## What is the Web Server?
A web server is a specialized software that handles HTTP requests from clients (usually web browsers) and serves them web pages or resources.   
It interprets the requests and fetches the appropriate content, delivering it back to the client.

### Examples:
- Microsoft’s IIS
- Nginx
- Apache


## What is Internet Information Services (IIS)?

**IIS** is a **web server software** developed by Microsoft to host and serve websites and applications on the Windows operating system. It supports multiple protocols such as HTTP, HTTPS, FTP, and more. **IIS** is well-suited for hosting ASP.NET and .NET Core applications, and it also supports other web technologies through additional configurations.

Here's some important concepts in IIS Context:

### **1. Sites:**
In IIS, a "site" is a top-level entity that can contain one or more web applications and virtual directories.   
Each site is distinguished by **one or more Unique bindings**. 

#### **Binding**
**Binding** involves two key attributes that are crucial for server-client communication:

1. **Binding Protocol**: Defines the protocol used for communication between the server and the client (e.g., HTTP or HTTPS).

2. **Binding Information**: Specifies the details required to access the site, it includes:
     - **IP Address:** The specific IP address the site listens on (e.g., `192.168.1.1`).
     - **Port Number:** The network port the site uses (e.g., port `80` for HTTP or `443` for HTTPS).
     - **Host Header (Domain Name) :** The domain name associated with the site (e.g., `www.example.com`), While the Host Header is technically `optional`, it is often necessary when multiple sites are hosted on the same IP address and port, a scenario known as `host-header-based` or `name-based` virtual hosting.

 #### **Default Ports**
   - Port 80 is the default port for **HTTP**. So connecting  to **http://domain** would send you to **http://domain:80** (by default).
   - Port 443 is the default port for **HTTPS**. Similarly, connecting  to  **https://domain**, would send you to **https://domain:443** (by default).
   - For any non-default ports, you need to explicitly specify the port like **url:port** to connect to. also you would need to make sure that the new port is open, forwarded and can receive connections.
  

 #### **Consideration on Selecting Site Ports**
   1. **Avoid Well-Known Ports**:
      - Ports `0-1023` are well-known and often reserved for system or well-established services (e.g., SSH on port 22, FTP on port 21). Unless your site is specifically providing one of these services, avoid these ports.
  
   2. **Avoid Commonly Used Ports**:
      - Ports `1024-49151` are registered ports, and many are commonly used by applications (e.g., MySQL uses port 3306). To avoid conflicts, choose a port that is less likely to be used by other applications.
  
   3. **Use Dynamic/Private Ports**:
      - Ports `49152-65535` are dynamic or private ports. These are less likely to conflict with other services, making them a good choice for internal or custom web applications.
  
   4. **Firewall and Security Considerations**:
      - Ensure that the chosen port is open in your firewall and not blocked by security policies.
  
One thing to note is that while these guidelines are generally good practice, the actual implementation can vary depending on the specific environment, operating system, and network configuration. For example, some systems might use slightly different port ranges for dynamic allocation.
Also, it's worth mentioning that for public-facing web applications, it's common to use standard HTTP (80) or HTTPS (443) ports.
  

