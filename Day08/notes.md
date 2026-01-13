# Day 08 – Containers & Docker Fundamentals

## Topics Covered
- Virtual Machines vs Containers
- Why containers were introduced
- Container architecture
- How containers are lightweight
- Container lifecycle
- What is Docker
- Docker architecture
- CMD vs ENTRYPOINT
- Port forwarding in containers

---

## Virtual Machines vs Containers

If virtual machines are an advancement over physical servers, then **containers are an advancement over virtual machines**.

### Virtual Machines (Quick Revision)

- Physical machines run a hypervisor
- Hypervisor creates multiple logical machines (VMs)
- Each VM has:
  - Its own operating system
  - Independent resources
  - Strong isolation and security

Even though VMs solved the resource utilization problem, **they still waste resources** because:
- Each VM carries a full operating system
- OS overhead is heavy

---

## Why Containers Were Introduced

Even with VMs, some resources remain unused.

Problems with VMs:
- Heavy OS
- Slower startup time
- Difficult to ship and replicate
- Resource overhead

To solve this, **containers were introduced**.

Containers are not perfect:
- Less secure than VMs
- Share the host OS kernel
- Containers can communicate with each other

But they solve efficiency and portability problems very well.

---

## Container Deployment Models

### Model 1
- Physical machine
- Hypervisor
- Virtual Machines
- Docker installed on VMs
- Containers run on VMs

### Model 2 (Most Common)
- Physical machine
- Virtual machine
- Docker installed on VM
- Containers created using Docker

---

## What Is a Container?

A container is a package of:
- Application
- Libraries
- System dependencies

Containers do NOT carry a full operating system.
They share most of the OS and kernel from the host machine.

This is why containers are lightweight and fast.

---

## Why Containers Are Lightweight

- Containers do not have a full OS
- They only include minimal system dependencies
- Majority of resources are shared with the host kernel

Example:
- Ubuntu VM size: ~2.4–2.5 GB
- Ubuntu base container image: ~30 MB

This massive size difference makes containers easy to ship and deploy.

---

## Why Containers Still Need System Dependencies

Containers do not share everything from the host.

If everything were shared:
- One container could access another container
- Security would be compromised

To maintain isolation, containers keep certain directories separate.

### Directories NOT shared between containers
- /bin
- /sbin
- /etc
- /lib
- /root
- /var
- /usr

---

## What Containers Share with the Host

- Host kernel
- Networking stack
- System calls
- Namespaces
- Control groups (cgroups)

This shared model makes containers lightweight but less isolated than VMs.

---

## Container Lifecycle

1. Write a Dockerfile
2. Build an image using Docker
3. Run the image to create a container

Docker engine:
- Reads Dockerfile
- Builds an image
- Runs containers from images

---

## What Is Docker?

Containerization is a concept.  
**Docker is a tool that implements containerization.**

Docker provides:
- Image building
- Container runtime
- Registry integration

---

## Docker Architecture

- Docker Client:
  - Used to run Docker commands

- Docker Daemon:
  - Heart of Docker
  - Receives commands from client
  - Builds images
  - Runs containers
  - Manages networking and storage

- Docker Registry:
  - Stores images
  - Allows push and pull of images

---

## Practical Work Done

- Wrote a Dockerfile
- Containerized a Django application
- Built Docker image
- Ran container

---

## CMD vs ENTRYPOINT

Both CMD and ENTRYPOINT are used when running containers.

### ENTRYPOINT
- Cannot be overridden easily
- Fixed command
- Used when container must always run a specific process

### CMD
- Can be overridden at runtime
- Used to provide default arguments

ENTRYPOINT is rigid, CMD is flexible.

---

## Port Forwarding in Containers

Containers run in isolated environments.

If an application runs on port 8080 inside the container:
- It will NOT be accessible by default

We must forward the port:
- Container port → VM/Host port

Without port forwarding, the application cannot be accessed externally.

---

## Key Takeaways

- Containers are lighter than virtual machines
- They share the host OS kernel
- Containers package app + dependencies
- Docker is the most popular container tool
- Containers are fast, portable, and efficient
- CMD and ENTRYPOINT behave differently
- Port mapping is required for external access

---

✅ Day 08 Completed – Containers & Docker Fundamentals
