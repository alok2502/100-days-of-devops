# Day 10 – Kubernetes (K8s) Fundamentals & Architecture

## Topics Covered
- Why Kubernetes is needed
- Docker vs Kubernetes (real-world view)
- Problems with Docker at scale
- How Kubernetes solves those problems
- Kubernetes cluster concept
- Kubernetes architecture
- Control Plane vs Data Plane
- Core Kubernetes components

---

## Docker vs Kubernetes (Beyond Definitions)

Textbook definitions say:
- Docker is a containerization platform
- Kubernetes is a container orchestration platform

But this alone does not explain **why Kubernetes exists**.

To understand Kubernetes, we must first understand the **problems we faced with Docker**.

---

## Problems with Docker at Scale

### 1️⃣ Single Host Problem
- Containers run on a single host
- If one container consumes too much memory or CPU
- Other containers can crash
- One bad container can affect many containers

---

### 2️⃣ Ephemeral Containers (Auto-Healing Problem)
- Containers can stop anytime
- If a container is killed, it does NOT restart automatically
- Manual intervention is required
- Containers can fail for hundreds of reasons

This is not scalable in production.

---

### 3️⃣ No Auto-Scaling
- If traffic suddenly increases
- New containers must be created manually
- Load balancer must be configured manually

Docker does not provide built-in auto-scaling.

---

### 4️⃣ No Enterprise-Level Support
Enterprise applications require:
- Load balancers
- API gateways
- Firewalls
- Advanced networking
- Security integrations

Docker alone does not provide these capabilities.

---

## How Kubernetes Solves These Problems

Kubernetes is designed to solve all the above issues.

---

## Kubernetes Cluster Concept

Kubernetes works as a **cluster**, meaning:
- A group of nodes working together
- Workload is distributed across nodes
- Failures are handled automatically

---

## Auto-Scaling in Kubernetes

- Kubernetes uses YAML-based configuration
- In Deployment or ReplicaSet, we define number of replicas
- Replicas can be increased manually
- Kubernetes also supports HPA (Horizontal Pod Autoscaler)
- HPA scales pods based on CPU, memory, or custom metrics

---

## Auto-Healing in Kubernetes

- Kubernetes constantly watches the cluster state
- If a pod goes down:
  - Kubernetes creates a new pod automatically
- This is handled by controllers via the API server

No manual intervention required.

---

## Enterprise-Level Support

Kubernetes is not enterprise software by itself, but:
- It is backed by CNCF
- Rapidly evolving
- Supports Custom Resources (CR) and Custom Resource Definitions (CRD)
- Integrates with enterprise tools like:
  - NGINX
  - F5
  - API gateways
  - Cloud-native load balancers

---

## Smallest Unit: Docker vs Kubernetes

- Docker smallest unit: Container
- Kubernetes smallest unit: Pod

A pod can contain:
- One container
- Multiple containers (sidecar pattern)

---

## Kubernetes Architecture Overview

Kubernetes has two main parts:
1. Control Plane
2. Data Plane (Worker Nodes)

---

## Data Plane (Worker Node Components)

### Container Runtime
- Responsible for running containers
- Examples:
  - containerd
  - CRI-O
- Docker shim is deprecated

---

### Kubelet
- Agent running on every worker node
- Ensures containers are running
- Reports pod status to API server
- If a container stops, kubelet informs control plane

---

### Kube-Proxy
- Manages networking on the node
- Handles service networking
- Routes traffic to correct pods

---

## Control Plane Components

### API Server
- Heart and brain of Kubernetes
- Exposes Kubernetes to external world
- All requests go through API server
- Communicates with all components

---

### Scheduler
- Decides where pods should run
- Finds the best suitable node
- Considers resources and constraints

---

### etcd
- Key-value datastore
- Stores entire cluster state
- Single source of truth for Kubernetes

---

### Controller Manager
- Manages controllers like:
  - ReplicaSet
  - Deployment
  - Node controller
- Ensures desired state matches actual state
- Example:
  - If replicas = 5
  - Controller ensures 5 pods are always running

---

### Cloud Controller Manager
- Integrates Kubernetes with cloud providers
- Translates Kubernetes requests to cloud APIs
- Manages cloud resources like:
  - Load balancers
  - Volumes
  - Networking

---

## Key Takeaways

- Docker is great for containers, not orchestration
- Kubernetes solves Docker’s production limitations
- Kubernetes provides:
  - Auto-healing
  - Auto-scaling
  - High availability
- Pod is the smallest unit in Kubernetes
- Control plane manages the cluster
- Worker nodes run the actual workloads

---

✅ Day 10 Completed – Kubernetes Fundamentals & Architecture
