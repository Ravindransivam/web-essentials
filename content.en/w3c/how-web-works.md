---
title: How does it works ?
weight: 1
---

When you type a URL into a browser, several processes occur behind the scenes to display the desired webpage. 

Here’s a step-by-step explanation of the web request flow.

---

# User Action
The web request flow begins when a user performs an action in their browser, such as:
- Typing a URL (e.g., `www.example.com`) in the address bar.
- Clicking on a hyperlink.
- Submitting a form.

---

### **3. Establishing a Connection**
- The browser establishes a **TCP (Transmission Control Protocol)** connection with the server using the resolved IP address.
- If the site uses HTTPS, a **TLS/SSL handshake** occurs to establish a secure, encrypted connection.

---The **TCP handshake** is a crucial part of establishing a reliable connection between a client (browser) and a server during a web request. It ensures that both the client and the server are ready to exchange data securely and reliably. Here's how it works step by step:

---

### **1. Purpose of the TCP Handshake**
The TCP handshake is a **three-way handshake** used to:
1. Establish a connection between the client and the server.
2. Synchronize the sequence numbers used for data transmission.
3. Ensure both parties are ready to send and receive data.

---

### **2. Steps of the Three-Way Handshake**
#### **Step 1: SYN (Client → Server)**
- The client initiates the connection by sending a **SYN (synchronize)** packet to the server.
- This packet includes:
  - The client’s **initial sequence number (ISN)**.
  - Flags indicating a connection request.

#### **Step 2: SYN-ACK (Server → Client)**
- The server responds with a **SYN-ACK** packet.
- This packet includes:
  - The server’s own ISN.
  - An acknowledgment number (the client’s ISN + 1) to confirm receipt of the client’s SYN.
  - A SYN flag indicating the server’s willingness to establish a connection.

#### **Step 3: ACK (Client → Server)**
- The client sends an **ACK (acknowledgment)** packet back to the server.
- This packet includes:
  - The acknowledgment number (server’s ISN + 1) to confirm receipt of the server’s SYN.
  - Flags indicating the connection is ready.

Once this step is complete, the connection is established.

---

### **3. Visual Representation**
```
Client                   Server
  | ---- SYN ------>      |
  | <--- SYN-ACK ----     |
  | ---- ACK ------>      |
Connection Established
```

---

### **4. After the Handshake**
- With the connection established, the client can begin sending HTTP requests (e.g., `GET`, `POST`).
- The server processes these requests and sends HTTP responses back to the client.

---

### **5. Secure Connections (TLS Handshake)**
If the connection is over **HTTPS**, the TCP handshake is followed by a **TLS handshake** to:
- Negotiate encryption protocols.
- Exchange cryptographic keys.
- Establish a secure, encrypted channel.

---

### **Key Features of TCP in the Handshake**
- **Reliability:** Sequence numbers ensure that all data is received and reassembled in the correct order.
- **Error Checking:** Acknowledgments and checksums verify data integrity.
- **Congestion Control:** TCP adapts to network conditions to avoid overwhelming the network.

This process underpins the reliability and security of web communications.

### **4. Sending the HTTP Request**
- The browser sends an **HTTP request** to the server. This request includes:
  - **Method** (e.g., `GET`, `POST`).
  - **URL Path** (e.g., `/index.html`).
  - **Headers** (e.g., browser type, cookies, etc.).
  - Optional **body** for methods like `POST`.

---

### **5. Server Processes the Request**
- The web server (e.g., Apache, Nginx) receives the request and determines how to handle it.
- If the website is dynamic, the server may:
  - Run backend code (e.g., PHP, Python, Node.js).
  - Query a **database** for additional data.
- If the website is static, the server retrieves the requested file (e.g., HTML, CSS, JavaScript) from its storage.

---

### **6. Generating the Response**
- The server generates an **HTTP response** containing:
  - **Status code** (e.g., `200 OK`, `404 Not Found`).
  - **Headers** (e.g., content type, cache control).
  - **Response body**, such as HTML, CSS, JSON, or an image.

---

### **7. Sending the Response**
- The server sends the HTTP response back to the browser over the established TCP connection.

---

### **8. Browser Renders the Content**
- The browser receives the response and begins rendering the web page:
  1. **HTML Parsing:** Constructs the DOM (Document Object Model).
  2. **CSS Parsing:** Applies styles.
  3. **JavaScript Execution:** Adds interactivity.
  4. **Resource Requests:** Downloads additional assets (images, scripts, stylesheets).

---

### **9. User Interaction with the Page**
- Once the page is loaded, the user can interact with it. Any further actions (e.g., clicking buttons) may trigger additional HTTP requests, restarting the flow.

---

### Example: Opening a Website
1. The user types `www.example.com` in the browser.
2. DNS resolves it to `192.168.1.1`.
3. A connection is established, and the browser sends a `GET` request for `/index.html`.
4. The server processes the request and responds with the HTML file.
5. The browser renders the page and requests additional resources (CSS, JS, images).
6. The user interacts with the page, possibly triggering more requests.

This cycle repeats throughout a browsing session.
