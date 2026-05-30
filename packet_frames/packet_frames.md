# Packet and Frames --- TryHackMe

**Platform:** TryHackMe\
**Type:** Room\
**Difficulty:** Easy\
**Name:** Packet and Frames

------------------------------------------------------------------------

## Questions & Answers

### Packet and Frames

Q: What is the name for a piece of data when it does have IP addressing information?  
A: Packet

Q: What is the name for a piece of data when it does not have IP addressing information?  
A: Frame

------------------------------------------------------------------------

### TCP/IP The Three-Way Handshake

Q: What is the header in a TCP packet that ensures the integrity of data?  
A: Checksum

Q: Provide the order of a normal Three-way handshake (with each step separated by a comma)  
A: SYN, SYN/ACK, ACK

------------------------------------------------------------------------

### UDP/IP

Q: What does the term "UDP" stand for?  
A: User Datagram Protocol

Q: What type of connection is "UDP"?  
A: Stateless

Q: What protocol would you use to transfer a file?  
A: TCP

Q: What protocol would you use to have a video call?  
A: UDP

---

## Notes

### Packets and Frames

- Packets and frames are small pieces of data that form a larger message to prevent network bottlenecking.
- **Encapsulation:** The process of adding headers to data as it moves down the layers. 
  - *Analogy:* Envelope = Frame (Layer 2), Inside the envelope = Packet (Layer 3).
- **Frame:** Used at Layer 2 (Data Link) of the OSI model; contains MAC addresses.
- **Packet:** Used at Layer 3 (Network) of the OSI model; contains IP headers and payload.

#### IP Packet Structure
- **TTL (Time to Live):** Expiry time for the packet so it doesn't clog the network.
- **Checksum:** Integrity checking for protocols.
- **Source Address:** IP of the sending device.
- **Destination Address:** IP of the receiving device.

------------------------------------------------------------------------

### TCP/IP & The Three-Way Handshake

- **TCP (Transmission Control Protocol):** A connection-based protocol that guarantees data delivery.
- **TCP/IP Model Layers (4 layers):** Application, Transport, Internet, Network Interface.
- **Decapsulation:** The reverse process of encapsulation (removing headers as data moves up layers).

#### TCP Header Fields
- **Source/Destination Port:** Ports used by the sender and the remote service.
- **Source/Destination IP:** IP addresses of sender and receiver.
- **Sequence Number:** A random number assigned to the first piece of data, incremented by 1 for subsequent data to help reconstruct the message.
- **Acknowledgement Number:** The sequence number + 1 of the next expected piece of data.
- **Flags:** Instructions on how the packet should be handled during communication (e.g., SYN, ACK, FIN).

#### The 3-Way Handshake Process
1. **SYN:** Client sends its Initial Sequence Number (ISN) to synchronize.
2. **SYN/ACK:** Server acknowledges the client's ISN and sends its own ISN.
3. **ACK:** Client acknowledges the server's ISN and begins sending data.

#### Full TCP Connection Lifecycle (Open to Close)
- **SYN** $\rightarrow$ **SYN/ACK** $\rightarrow$ **ACK** $\rightarrow$ **DATA** $\rightarrow$ **FIN** $\rightarrow$ **FIN/ACK** $\rightarrow$ **ACK**
- *Note:* Closing connections is a best practice to free up reserved system resources. If a problem occurs, a **RST** (Reset) packet abruptly ends communication.

------------------------------------------------------------------------

### UDP/IP (User Datagram Protocol)

- **UDP:** A stateless protocol that does not require a constant connection before sending data.
- Much simpler than TCP with fewer headers (Faster, but no delivery guarantee).
- **UDP Headers include:** TTL, Source/Destination IP, Source/Destination Port, and Data.

------------------------------------------------------------------------

### Ports 101

- Ports are numerical values between **0 and 65535** used to enforce communication rules and direct traffic to specific applications.
- **Common Ports Reference:**
  
  | Port | Protocol | Description |
  | :--- | :--- | :--- |
  | **21** | FTP | File Transfer Protocol (Client-Server model) |
  | **22** | SSH | Secure Shell (Secure text-based remote login) |
  | **80** | HTTP | Hypertext Transfer Protocol (Unencrypted web traffic) |
  | **443** | HTTPS | HTTP Secure (Encrypted web traffic) |
  | **445** | SMB | Server Message Block (File and device/printer sharing) |
  | **3389**| RDP | Remote Desktop Protocol (Visual GUI remote login) |
