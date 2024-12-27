---
title: Behind Every URL ?
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


When you type a URL (Uniform Resource Locator) into the browser, several steps are taken to interpret and process it:

# Components of a URL
A URL typically consists of:
```
protocol://hostname:port/path?query#fragment
```
- **Protocol:** Defines the communication method (e.g., `http`, `https`, `ftp`).
- **Hostname:** The domain name (e.g., `www.example.com`) that needs to be resolved into an IP address.
- **Port (optional):** Specifies the port to connect to (default: `80` for HTTP and `443` for HTTPS).
- **Path, Query, Fragment (optional):** Specifies the resource or parameters.

For example:
`https://www.example.com:443/page?search=test#section`

---

# Parsing the URL
- The browser parses the URL to identify its components.
- If the protocol is missing, the browser assumes the default (`http://` or `https://`).
- If the port is omitted, the default port for the protocol is used (`80` for HTTP, `443` for HTTPS).

---

# IP Address Resolution
The browser needs to convert the **hostname** (e.g., `www.example.com`) into an **IP address** (e.g., `192.168.1.1`) to locate the server. This process is called **DNS Resolution**.

## Steps in IP Address Resolution
1. **Browser Cache:**
   - The browser checks its cache for a stored IP address associated with the domain name.
   - If found, it skips further steps.

2. **Operating System Cache:**
   - If the browser cache doesn’t have the IP, the request is forwarded to the OS, which checks its local DNS cache.

3. **Hosts File:**
   - The OS checks the **hosts file**, a local configuration file mapping domain names to IP addresses.
   - If the hostname is found here, its corresponding IP address is used.

4. **Recursive DNS Resolver:**
   - If the IP is not resolved locally, the OS forwards the request to a **recursive DNS resolver** (provided by the ISP or a public DNS service like Google DNS or Cloudflare DNS).
   - The recursive resolver acts as an intermediary that queries other DNS servers.

5. **Root DNS Server:**
   - The resolver queries a **root DNS server**, which responds with the address of the **TLD DNS server** (e.g., for `.com`).

6. **TLD DNS Server:**
   - The resolver queries the **TLD DNS server**, which provides the address of the **authoritative DNS server** for the domain.

7. **Authoritative DNS Server:**
   - The authoritative DNS server for the domain responds with the IP address of the requested hostname.

8. **Caching:**
   - The recursive resolver caches the IP address for a specified **TTL (Time-To-Live)** to speed up future requests.
   - The IP address is returned to the OS, then to the browser.

---

# Final Output
The browser now has the IP address (e.g., `192.168.1.1`) of the server corresponding to the URL. It uses this IP to establish a connection with the server and proceed with the web request.

---

## **Example of IP Resolution**
For `https://www.example.com`:
1. The browser parses the URL and extracts `www.example.com`.
2. It checks the browser cache, OS cache, and hosts file for the IP.
3. The recursive DNS resolver contacts:
   - Root DNS servers → TLD DNS server → Authoritative DNS server.
4. The authoritative server responds with the IP (e.g., `192.168.1.1`).
5. The browser receives the IP address and proceeds to establish a connection.

This entire process typically takes milliseconds, ensuring a seamless browsing experience.

