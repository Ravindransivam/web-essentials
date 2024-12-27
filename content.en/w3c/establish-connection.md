---
title: Establish Connection
weight: 3
---


**Establishing a Connection**
- The browser establishes a **TCP (Transmission Control Protocol)** connection with the server using the resolved IP address.
- If the site uses HTTPS, a **TLS/SSL handshake** occurs to establish a secure, encrypted connection.

---The **TCP handshake** is a crucial part of establishing a reliable connection between a client (browser) and a server during a web request. It ensures that both the client and the server are ready to exchange data securely and reliably. Here's how it works step by step:

---

# Purpose of the TCP Handshake
The TCP handshake is a **three-way handshake** used to:
1. Establish a connection between the client and the server.
2. Synchronize the sequence numbers used for data transmission.
3. Ensure both parties are ready to send and receive data.

---

# Steps of the Three-Way Handshake
## **Step 1: SYN (Client → Server)**
- The client initiates the connection by sending a **SYN (synchronize)** packet to the server.
- This packet includes:
  - The client’s **initial sequence number (ISN)**.
  - Flags indicating a connection request.

## **Step 2: SYN-ACK (Server → Client)**
- The server responds with a **SYN-ACK** packet.
- This packet includes:
  - The server’s own ISN.
  - An acknowledgment number (the client’s ISN + 1) to confirm receipt of the client’s SYN.
  - A SYN flag indicating the server’s willingness to establish a connection.

## **Step 3: ACK (Client → Server)**
- The client sends an **ACK (acknowledgment)** packet back to the server.
- This packet includes:
  - The acknowledgment number (server’s ISN + 1) to confirm receipt of the server’s SYN.
  - Flags indicating the connection is ready.

Once this step is complete, the connection is established.

---

# Visual Representation
```
Client                   Server
  | ---- SYN ------>      |
  | <--- SYN-ACK ----     |
  | ---- ACK ------>      |
Connection Established
```

---

# After the Handshake
- With the connection established, the client can begin sending HTTP requests (e.g., `GET`, `POST`).
- The server processes these requests and sends HTTP responses back to the client.

---

# Secure Connections (TLS Handshake)
If the connection is over **HTTPS**, the TCP handshake is followed by a **TLS handshake** to:
- Negotiate encryption protocols.
- Exchange cryptographic keys.
- Establish a secure, encrypted channel.

---

# Key Features of TCP in the Handshake
- **Reliability:** Sequence numbers ensure that all data is received and reassembled in the correct order.
- **Error Checking:** Acknowledgments and checksums verify data integrity.
- **Congestion Control:** TCP adapts to network conditions to avoid overwhelming the network.

This process underpins the reliability and security of web communications.

