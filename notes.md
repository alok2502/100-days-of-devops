# Day 17 – Networking Fundamentals (IP, VPC, CIDR, OSI Model)

## Focus of the Day
Today’s learning focused on core networking fundamentals required for:
- Linux
- Cloud (AWS, Azure)
- Kubernetes
- DevOps troubleshooting

---

## IP Addresses

An IP address is a unique identifier assigned to a device in a network.

Purpose:
- Identify a machine
- Enable communication between systems

IP addresses are essential for routing traffic across networks and the internet.

---

## VPC (Virtual Private Cloud)

A VPC is a logically isolated virtual network inside a cloud provider.

Advantages of VPC:
- Network isolation
- Security control
- Custom IP ranges
- Better traffic management

All cloud resources like EC2, databases, and load balancers run inside a VPC.

---

## Subnetting in a VPC

A subnet is a logical division of a VPC’s IP address range.

### Why Subnetting Is Needed
- Better IP management
- Improved security
- Logical separation of resources
- High availability across multiple zones

---

### Types of Subnets

- Public Subnet:
  - Has internet access
  - Used for load balancers, bastion hosts

- Private Subnet:
  - No direct internet access
  - Used for application servers and databases

Subnetting improves both security and scalability.

---

## CIDR (Classless Inter-Domain Routing)

CIDR defines IP ranges using notation like:

10.0.0.0/16

Meaning:
- /16 → Network bits
- Remaining bits → Host addresses

CIDR helps:
- Allocate IP ranges efficiently
- Avoid IP wastage
- Support large and small networks flexibly

---

## IP Address Classes

Traditional IP address classes:
- Class A
- Class B
- Class C

CIDR replaced strict class-based networking to provide more flexibility in IP allocation.

---

## Ports

Ports identify specific services running on a machine.

Examples:
- 80 → HTTP
- 443 → HTTPS
- 22 → SSH
- 3306 → MySQL

IP + Port uniquely identifies a service on a system.

---

## DNS Resolution (Revisited)

DNS translates human-readable domain names into IP addresses.

Flow:
- Browser queries DNS
- DNS returns IP address
- Browser connects to the server using that IP

DNS is critical for internet communication.

---

## TCP 3-Way Handshake (Revisited)

TCP establishes a reliable connection using three steps:
1. SYN
2. SYN-ACK
3. ACK

This ensures:
- Reliable communication
- Connection establishment before data transfer

---

## OSI Model Overview

The OSI model explains how data travels from an application to physical hardware.

Layers are numbered from L7 to L1.

---

## OSI Layer Breakdown

### Layer 7 – Application Layer
- Application-specific data
- Headers and protocols like HTTP, HTTPS

---

### Layer 6 – Presentation Layer
- Encryption and decryption
- Data formatting and compression

---

### Layer 5 – Session Layer
- Session management
- Connection setup and teardown

Layers 7, 6, and 5 mostly operate at the application/browser level.

---

### Layer 4 – Transport Layer
- Data segmentation
- Protocol selection (TCP/UDP)
- Port numbers

This layer ensures reliable or fast communication.

---

### Layer 3 – Network Layer
- Routing decisions
- Source and destination IP addresses
- Data units called packets

Routers operate at this layer.

---

### Layer 2 – Data Link Layer
- MAC addresses
- Frames
- Switching within a local network

Switches operate at this layer.

---

### Layer 1 – Physical Layer
- Electrical, optical, or radio signals
- Transmission through cables or fibers

This is where data becomes raw signals.

---

## End-to-End Data Flow Summary

Application Data →  
Segments (L4) →  
Packets with IP (L3) →  
Frames with MAC (L2) →  
Electrical/Optical Signals (L1)

---

## Summary

- Understood IP addressing and subnetting
- Learned VPC and subnet concepts
- Revised CIDR and IP classes
- Revisited DNS and TCP handshake
- Understood OSI model from L7 to L1
- Built strong networking fundamentals

---

✅ Day 17 Completed – Networking Fundamentals
