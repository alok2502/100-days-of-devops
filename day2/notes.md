# Day 02 – Virtual Machines & Hypervisors

## Topics Covered
- Why Virtual Machines are needed
- Resource utilization problem with physical servers
- Hypervisors and virtualization
- How Virtual Machines work in cloud (AWS example)
- VM creation and automation methods

---

## Why Virtual Machines Are Needed

DevOps is all about **improving efficiency, scalability, and automation**.

Consider this scenario:

- You have **5 physical servers**
- Each server has:
  - 100 GB RAM
  - 100 CPU cores

Now imagine:
- Team 1 needs only **4 GB RAM and 4 CPUs** to deploy their application

If we deploy that application directly on a physical server:
- One full server is consumed
- Remaining resources are wasted

This approach is **highly inefficient**.

---

## Solution: Virtualization

To solve this problem, we use **virtualization**.

With the help of a **hypervisor**, we can:
- Split a physical server into multiple logical servers
- Allocate only required resources (CPU, RAM, storage) to each team
- Run multiple applications on the same physical machine safely

These **logically separated servers** are called **Virtual Machines (VMs)**.

They are logical, not physical — but they behave like real servers.

---

## What Is a Hypervisor?

A **hypervisor** is software that:
- Runs on physical hardware
- Creates and manages Virtual Machines
- Allocates CPU, memory, and storage to each VM
- Ensures isolation between VMs

### Popular Hypervisors
- VMware
- Xen
- KVM
- Hyper-V

---

## How Virtual Machines Work in the Cloud (AWS Example)

When you request a VM (EC2) in AWS:

1. AWS has multiple **data centers** (for example, Mumbai region)
2. These data centers contain **physical machines**
3. Hypervisors are installed on those machines
4. Based on your request:
   - AWS creates a VM with required CPU, RAM, and storage
   - Assigns IP address and networking
5. You receive access details to use the VM

From the user perspective, it feels like you got a dedicated server —  
but internally, it is a **virtual machine running on shared physical hardware**.

---

## Creating Virtual Machines in Cloud

Virtual Machines can be created using multiple methods:

### Manual (UI)
- AWS Console
- Azure Portal

### Automation / Infrastructure as Code
- Terraform
- CloudFormation (CFT)
- AWS CDK
- AWS CLI / Azure CLI

---

## Automation Insight (Important)

If you create VMs using UI:
- It is manual
- Not repeatable
- Not scalable

In DevOps, we prefer:
- **APIs**
- **Infrastructure as Code**
- **Automation tools**

Instead of clicking buttons in UI, automation tools use **cloud APIs** to create and manage virtual machines consistently.

---

## Key Takeaways

- Physical servers lead to resource wastage
- Virtual Machines improve hardware utilization
- Hypervisors enable virtualization
- VMs are logical, not physical machines
- Cloud providers use hypervisors behind the scenes
- DevOps favors automated VM creation over manual UI actions

---

✅ **Day 02 Completed – Virtual Machines & Virtualization**
