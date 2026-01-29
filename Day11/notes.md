# Day 11 – Kubernetes Pods, Deployments & Services Basics

## Topics Covered
- Why Kubernetes introduced Pods
- Containers vs Pods
- Multi-container Pods (sidecar, init)
- kubectl and Minikube basics
- Creating and managing Pods
- Why Pods are not used directly
- Deployments and ReplicaSets
- Auto-healing with Deployments
- Why Services are needed
- Service discovery and load balancing
- Types of Kubernetes Services

---

## Why Pods Exist (Why Not Just Containers?)

In Docker, we directly run containers, so a natural question is:
Why did Kubernetes introduce a new abstraction called **Pod**?

Containers and Pods are not the same.

A **Pod is a definition of how to run one or more containers**.

Everything that we pass as runtime options in Docker (image, ports, commands, env variables) is defined declaratively inside a **pod YAML manifest** in Kubernetes.

Kubernetes is declarative by design, and Pods provide a standardized way to define container runtime behavior.

---

## Containers vs Pods

- Container:
  - Runtime unit
  - Runs application process

- Pod:
  - Smallest deployable unit in Kubernetes
  - Wrapper around container(s)
  - Defines how containers should run

A Pod can run:
- A single container
- Multiple containers

---

## Multi-Container Pods

Pods can contain more than one container, such as:
- Sidecar containers
- Init containers

Advantages:
- Containers in the same pod share:
  - Network namespace
  - IP address
  - Ports
  - Volumes (storage)
- Containers can communicate using localhost

This is useful for logging agents, proxies, or initialization tasks.

---

## kubectl – Kubernetes CLI

kubectl is the command-line tool used to interact with Kubernetes.

Just like Docker has `docker` CLI, Kubernetes uses `kubectl`.

kubectl communicates with the Kubernetes API Server.

---

## Practical Setup (Minikube)

Steps performed:
- Installed kubectl on Linux machine
- Installed Minikube for learning
- Started Minikube cluster
- Verified cluster using kubectl get nodes

Minikube creates a **single-node Kubernetes cluster** where:
- Control Plane
- Worker Node  
exist on the same VM.

---

## Creating a Pod

- Pod manifest was written using Kubernetes official documentation format
- Verified image name and configuration
- Created pod using kubectl create -f pod.yml

Verification commands:
- kubectl get pods
- kubectl get pods -o wide

---

## Accessing the Pod

- Logged into Minikube VM using minikube ssh
- Accessed the application using curl
- Verified nginx was running

---

## Debugging Pods

Useful commands:
- kubectl logs pod-name  
  Used to view pod logs

- kubectl describe pod pod-name  
  Used to view detailed pod information  
  Helpful for debugging issues

- kubectl delete pod pod-name  
  Used to delete a pod

---

## Why Pods Are Not Used Directly

Pods alone do NOT provide:
- Auto-healing
- Auto-scaling
- High availability

If a pod is deleted:
- It will NOT come back automatically

To use advanced features, Kubernetes provides **Deployments**.

---

## Deployments in Kubernetes

A Deployment is a higher-level abstraction that manages Pods.

Workflow:
- User creates a Deployment
- Deployment creates a ReplicaSet
- ReplicaSet creates Pods

Even though we work with Deployments, **Pods are still created underneath**.

---

## Deployment vs Pod

- Pod:
  - Basic unit
  - No auto-healing
  - No scaling

- Deployment:
  - Manages Pods
  - Provides auto-healing
  - Supports scaling
  - Enables rolling updates

Deployment is a wrapper around ReplicaSet and Pods.

---

## Auto-Healing with Deployment

If replicas = 2:
- Kubernetes ensures 2 Pods are always running
- If a Pod is deleted manually:
  - ReplicaSet creates a new Pod automatically

This achieves auto-healing with zero manual intervention.

---

## Why Services Are Needed

Pods are ephemeral:
- When a Pod is recreated, its IP address changes

Problems without Services:
- Users cannot track changing Pod IPs
- Old IPs become invalid
- Load balancing is not possible

---

## Kubernetes Service

A Service provides:
- Stable network endpoint
- Load balancing
- Service discovery

Instead of accessing Pods directly, users access the **Service**.

Service routes traffic to Pods dynamically.

---

## Service Discovery Using Labels and Selectors

- Pods are labeled
- Services use selectors to match labels
- When a Pod is recreated:
  - It gets a new IP
  - But the same label
- Service automatically routes traffic to the new Pod

This solves the dynamic IP problem.

---

## Exposing Applications with Services

Services also expose applications to users.

We do NOT expect users to:
- SSH into cluster nodes
- Access Pod IPs directly

Services provide controlled access.

---

## Types of Kubernetes Services

### ClusterIP
- Default service type
- Accessible only within the cluster
- Used for internal communication

---

### NodePort
- Exposes application on each node’s IP
- Accessible to anyone who can reach the node
- Uses a fixed port range

---

### LoadBalancer
- Exposes application to the external world
- Creates a cloud load balancer (AWS ELB, Azure LB, etc.)
- Provides a public IP

Commonly used in managed Kubernetes clusters like EKS.

---

## Key Takeaways

- Pod is the smallest unit in Kubernetes
- Pod is a wrapper around containers
- Pods can run multiple containers
- Deployments manage Pods
- ReplicaSets ensure desired replicas
- Pods are ephemeral, Services provide stability
- Services enable load balancing and discovery
- Different service types suit different access needs

---

✅ Day 11 Completed – Pods, Deployments & Services Fundamentals
