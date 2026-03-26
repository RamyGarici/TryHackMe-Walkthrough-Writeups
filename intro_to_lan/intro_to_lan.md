# Intro to LAN — TryHackMe

**Platform:** TryHackMe  
**Type:** Room  
**Difficulty:** Easy  
**Name:** Intro to LAN

---

## Questions & Answers (TryHackMe)

### Introducing LAN Topologies

Q: What does LAN stand for?  
A: Local Area Network

Q: What is the verb given to the job that routers perform?  
A: Routing

Q: What device is used to centrally connect multiple devices on the local network and transmit data to the correct location?  
A: Switch

Q: What topology is cost-efficient to set up?  
A: Bus topology

Q: What topology is expensive to set up and maintain?  
A: Star topology

Q: Complete the interactive lab attached to this task. What is the flag given at the end?  
A: THM{TOPOLOGY_FLAWS}

---

### A Primer on Subnetting

Q: What is the technical term for dividing a network into smaller pieces?  
A: Subnetting

Q: How many bits are in a subnet mask?  
A: 32

Q: What is the range of a section (octet) of a subnet mask?  
A: 0–255

Q: What address is used to identify the start of a network?  
A: Network address

Q: What address is used to identify devices within a network?  
A: Host address

Q: What is the name used to identify the device responsible for sending data to another network?  
A: Default gateway

---

### ARP

Q: What does ARP stand for?  
A: Address Resolution Protocol

Q: What category of ARP packet asks a device whether or not it has a specific IP address?  
A: Request

Q: What address is used as a physical identifier for a device on a network?  
A: MAC address

Q: What address is used as a logical identifier for a device on a network?  
A: IP address

---

### DHCP 
Q: What type of DHCP packet is used by a device to retrieve an IP address?
A: DHCP Discover

Q: What type of DHCP packet does a device send once it has been offered an IP address by the DHCP server?
A: DHCP Request

Q: Finally, what is the last DHCP packet that is sent to a device from a DHCP server?
A: DHCP ACK

## Notes

### LAN Topologies

Topology = the design or layout of a network.

Star topology:
- Most commonly used today.
- Devices are individually connected via a central device (switch or hub).
- More expensive due to cabling and hardware.
- Very scalable (easy to add devices).
- As the network grows, maintenance becomes more complex.
- If the central device fails, communication stops.

Bus topology:
- Uses a single backbone cable.
- All data travels along the same cable.
- Can become slow if multiple devices send data at the same time.
- Difficult to troubleshoot.
- Easy and cost-efficient to set up.
- A single failure in the cable can break the entire network.

Ring topology:
- Devices are connected in a loop.
- Requires less cabling and less hardware.
- Data travels through devices until reaching its destination.
- A device sends its own data before forwarding others.
- Data flows in one direction.
- Easier to troubleshoot but less efficient.
- Less prone to congestion than bus topology.
- A single failure breaks the entire network.

---

### Switch

- Connects multiple devices (computers, printers, etc.).
- More efficient than hubs.
- Keeps track of which device is connected to each port.
- Sends data only to the correct device instead of broadcasting.
- Can be connected to routers or other switches to increase redundancy.
- Improves reliability but may slightly reduce performance due to longer paths.

---

### Router

- Connects different networks together.
- Uses routing to send data between networks.
- Routing creates paths for data to travel.
- Useful when multiple paths exist between devices.

---

### Subnetting

- Splitting a network into smaller networks.
- Subnet mask = 4 bytes (0–255 each).

IP address usage:
- Network address → identifies the network.
- Host address → identifies a device.
- Default gateway → sends data to other networks.

Benefits:
- Efficiency
- Security
- Better control

---

### ARP

- Uses both MAC and IP addresses.
- Associates a MAC address with an IP address.
- Each device keeps a cache of known devices.

How it works:
- A device sends a broadcast (ARP request).
- Devices respond if they own the IP (ARP reply).
- The mapping is stored for future use.

---

### DHCP

- Assigns IP addresses automatically.

Process:
- DHCP Discover
- DHCP Offer
- DHCP Request
- DHCP ACK
