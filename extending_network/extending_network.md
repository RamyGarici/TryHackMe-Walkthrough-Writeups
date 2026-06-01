# Extending Your Network

**Platform:** TryHackMe  
**Type:** Room  
**Difficulty:** Easy  
**Name:** Extending Your Network

------------------------------------------------------------------------

## Questions & Answers

### Intro to Port Forwarding

Q: What is the name of the device that is used to configure port forwarding?  
A: Router

------------------------------------------------------------------------

### Firewalls 101

Q: What layers of the OSI model do firewalls operate at? (Provide numbers in ascending order, separated by an ampersand)  
A: 3 & 4

Q: What category of firewall inspects the entire connection?  
A: Stateful

Q: What category of firewall inspects individual packets?  
A: Stateless

------------------------------------------------------------------------

### VPN Basics

Q: What VPN technology only encrypts & provides the authentication of data?  
A: PPP

Q: What VPN technology uses the IP framework?  
A: IPsec

------------------------------------------------------------------------

### LAN: Networking Devices

Q: What is the verb for the action that a router does?  
A: Routing

Q: What are the two different layers of switches? (Separate by a comma)  
A: Layer 2, Layer 3

---

## Notes

### Port Forwarding

- **Concept:** Essential for connecting private applications and services to the internet. Without it, services are only accessible within the same local network.
- **Security:** Routers block all incoming traffic by default to protect devices on the private local network (LAN).
- **Mechanism:** When an external request arrives at the router on a specific port, the router forwards that traffic to a designated device within the private network.

------------------------------------------------------------------------

### Firewalls 101

- A firewall determines what traffic is allowed to enter and exit a network based on a set of criteria:
  - **Source:** Where the traffic is coming from.
  - **Destination:** Where the traffic is going.
  - **Port:** The specific destination port (e.g., Port 80).
  - **Protocol:** The transport protocol used (TCP, UDP, or both).
- Firewalls perform **packet inspection** to analyze these factors. They range from massive dedicated hardware appliances to residential routers and software (e.g., Snort).



#### Stateful vs. Stateless Firewalls

| Feature | Stateful Firewall | Stateless Firewall |
| :--- | :--- | :--- |
| **Inspection Target** | Evaluates the **entire connection** and behavior dynamically. | Inspects **individual packets** against static rules. |
| **Resource Usage** | **High** (requires memory to track connection states). | **Low** (much faster, processes packets instantly). |
| **Reaction to Threat** | Blocks the **entire device** if bad behavior is detected. | Drops the specific bad packet; doesn't block the whole device. |
| **Best Use Case** | Advanced, contextual network security. | Handling massive traffic volumes, like mitigating **DDoS** attacks. |

------------------------------------------------------------------------

### VPN Basics (Virtual Private Network)

- **Definition:** Allows devices on separate networks to communicate securely by creating an encrypted, private tunnel over the internet.

#### Benefits
- **Geographical Connection:** Links physically separated networks.
- **Privacy:** Encrypts data to prevent sniffing.
- **Anonymity:** Hides traffic details from ISPs and intermediaries.

#### VPN Protocols
- **PPP (Point-to-Point Protocol):** Used to authenticate and encrypt data. Works with a private key and a public certificate that must match to establish a connection.
- **PPTP (Point-to-Point Tunneling Protocol):** Allows PPP data to travel and leave a network. Easy to set up and widely supported, but features weak encryption compared to alternatives.
- **IPsec (Internet Protocol Security):** Encrypts data using the existing IP framework. It is harder to configure than PPTP but boasts very strong encryption.

------------------------------------------------------------------------

### LAN: Networking Devices

#### Routers
- **Role:** Connects distinct networks and passes data between them via **routing** (finding the optimal path across networks).
- Operates at **Layer 3 (Network)** of the OSI model.
- Provides interactive interfaces for administrators to set up firewall rules and port forwarding.

#### Switches
- **Role:** Connects multiple devices together within the *same* local network using ethernet cables (typically from 3 to 63 devices).
- **Layer 2 Switches:** Forward frames to connected devices using **MAC addresses**. They cannot operate at Layer 3.
- **Layer 3 Switches:** Can perform both Layer 2 frame forwarding and Layer 3 packet routing using the **IP protocol**.

#### VLAN (Virtual Local Area Network)
- Allows specific devices within a physical network to be segmented virtually.
- **Advantage:** Devices share resources (like an internet connection) but remain separated, enhancing security by enforcing strict communication rules between specific zones.
