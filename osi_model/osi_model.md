# OSI Model — TryHackMe

**Platform:** TryHackMe  
**Type:** Room  
**Difficulty:** Easy  
**Name:** OSI Model  

---

## Questions & Answers (TryHackMe)

### Basics

Q: What does the "OSI" in "OSI Model" stand for?  
A: Open Systems Interconnection  

Q: How many layers (in digits) does the OSI model have?  
A: 7  

Q: What is the key term for when pieces of information get added to data?  
A: Encapsulation  

---

### Layer 1 — Physical

Q: What is the name of this layer?  
A: Physical  

Q: What is the name of the numbering system that is both 0's and 1's?  
A: Binary  

Q: What is the name of the cables that are used to connect devices?  
A: Ethernet cables  

---

### Layer 2 — Data Link

Q: What is the name of this layer?  
A: Data Link  

Q: What is the name of the piece of hardware that all networked devices come with?  
A: Network Interface Card  

---

### Layer 3 — Network

Q: What is the name of this layer?  
A: Network  

Q: Will packets take the most optimal route across a network? (Y/N)  
A: Y  

Q: What does the acronym "OSPF" stand for?  
A: Open Shortest Path First  

Q: What does the acronym "RIP" stand for?  
A: Routing Information Protocol  

Q: What type of addresses are dealt with at this layer?  
A: IP addresses  

---

### Layer 4 — Transport

Q: What is the name of this layer?  
A: Transport  

Q: What does TCP stand for?  
A: Transmission Control Protocol  

Q: What does UDP stand for?  
A: User Datagram Protocol  

Q: What protocol guarantees the accuracy of data?  
A: TCP  

Q: What protocol doesn't care if data is received or not?  
A: UDP  

Q: What protocol would an email client use?  
A: TCP  

Q: What protocol would a file download use?  
A: TCP  

Q: What protocol would video streaming use?  
A: UDP  

---

### Layer 5 — Session

Q: What is the name of this layer?  
A: Session  

Q: What is the technical term for when a connection is successfully established?  
A: Session  

---

### Layer 6 — Presentation

Q: What is the name of this layer?  
A: Presentation  

Q: What is the main purpose that this layer acts as?  
A: Translator  

---

### Layer 7 — Application

Q: What is the name of this layer?  
A: Application  

Q: What is the technical term for the software users interact with?  
A: Graphical User Interface  

---

## Notes

### OSI Model Overview

- OSI model = framework used in networking.  
- Defines how data is sent, received, and interpreted.  
- Allows different devices to communicate even if they are different.  
- Contains 7 layers.  
- Data passes through each layer.  
- At each layer, data is modified → encapsulation.  

Layers order:  
Application → Presentation → Session → Transport → Network → Data Link → Physical  

---

### Layer 1 — Physical

- Lowest layer.  
- Deals with hardware.  
- Uses electrical signals.  
- Data is transmitted as binary (0 and 1).  
- Uses Ethernet cables.  

---

### Layer 2 — Data Link

- Handles physical addressing (MAC).  
- Receives packets from Network layer.  
- Adds MAC address.  
- Uses NIC (Network Interface Card).  
- MAC address is unique and set by manufacturer.  
- Can be spoofed.  

Process:  
- Device receives data  
- Checks MAC address  
- If correct → passes to Network layer  

---

### Layer 3 — Network

- Handles routing.  
- Determines best path for data.  
- Uses IP addresses.  
- Devices: routers (Layer 3 devices).  

Routing factors:  
- Shortest path  
- Most reliable  
- Fastest connection  

Protocols:  
- OSPF  
- RIP  

---

### Layer 4 — Transport

- Responsible for data transmission.  
- Uses TCP and UDP.  

TCP:
- Reliable  
- Guarantees delivery  
- Error checking  
- Maintains connection  

Advantages:
- Accurate data  
- Synchronization  

Disadvantages:
- Slower  
- Requires stable connection  

Used for:
- Email  
- File transfer  
- Web browsing  

UDP:
- Faster  
- No guarantee of delivery  
- No synchronization  

Advantages:
- Speed  
- No persistent connection  

Used for:
- Streaming  
- Small data transfers  
- ARP / DHCP  

---

### Layer 5 — Session

- Creates and maintains connection.  
- Session = active connection between devices.  
- Closes inactive sessions.  
- Uses checkpoints to resume transmission.  
- Sessions are unique.  

---

### Layer 6 — Presentation

- Handles formatting and translation.  
- Ensures data is understandable.  
- Deals with encryption (HTTPS).  
- Acts as translator between systems.  

---

### Layer 7 — Application

- Closest layer to the user.  
- Defines how applications interact with network.  

Examples:
- Browsers  
- Email clients  
- File transfer tools  

Protocols:
- DNS (translates domain names to IP)  

---

### OSI Summary

7. Application → user interaction  
6. Presentation → encoding / encryption  
5. Session → connection management  
4. Transport → communication (TCP/UDP)  
3. Network → routing (IP)  
2. Data Link → MAC addressing  
1. Physical → bits and hardware  
