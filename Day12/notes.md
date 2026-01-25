# Day 12 – Kubernetes Advanced Concepts (Ingress, RBAC, Custom Resources)

## Topics Covered
- Why Ingress is needed
- Limitations of Service (LoadBalancer)
- Ingress Controller & Ingress Resource
- Role-Based Access Control (RBAC)
- Users vs Service Accounts
- Roles, ClusterRoles & Bindings
- Custom Resources (CR)
- Custom Resource Definitions (CRD)
- Custom Controllers (CRC)

---

## Why Do We Need Ingress?

A common question:
If a Service (LoadBalancer) already exposes applications externally, why do we need Ingress?

To answer this, we must first understand the **limitations of Services**.

---

## Limitations of Kubernetes Services

### 1️⃣ Limited Load Balancing
Kubernetes Services provide only **round-robin load balancing**.

Enterprise load balancers support advanced features like:
- Path-based routing
- Domain-based routing
- Sticky sessions
- IP whitelisting / blacklisting
- Ratio-based traffic splitting
- Header-based routing

These features are not supported by default Services.

---

### 2️⃣ Cost Problem with LoadBalancer Service

If we use Service type LoadBalancer:
- Each Service creates a separate cloud load balancer
- Each load balancer gets a static IP
- Cloud providers charge for each load balancer

Example:
- 100 microservices → 100 load balancers → very expensive

---

## What Is Ingress?

Ingress is a Kubernetes object that:
- Manages external HTTP/HTTPS access
- Provides advanced routing rules
- Works as a **single entry point** for multiple services

Ingress solves both:
- Feature limitations
- Cost problems

---

## Ingress Controller vs Ingress Resource

Ingress works using **two components**:

### Ingress Controller
- Actual implementation of load balancing
- Provided by vendors like:
  - NGINX
  - F5
  - Traefik
- Runs as a controller inside the cluster
- Watches Ingress resources

Without an Ingress Controller, Ingress resources do NOTHING.

---

### Ingress Resource
- YAML definition written by users
- Defines routing rules:
  - Path
  - Domain
  - Backend service

Ingress Resource is useless without an Ingress Controller.

---

## How Ingress Solves the Problem

- One external load balancer
- Multiple applications behind it
- Advanced routing rules
- Reduced cost
- Enterprise-grade traffic management

---

## Role-Based Access Control (RBAC)

RBAC controls **who can do what** inside a Kubernetes cluster.

RBAC is critical in production environments.

---

## Why RBAC Is Needed

Example problem:
- A QA engineer accidentally deletes etcd in kube-system namespace

This can bring down the entire cluster.

RBAC ensures:
- Least privilege access
- Role-based permissions
- Better security and auditability

---

## Types of Identities in RBAC

### 1️⃣ Users
- Humans (developers, QA, DevOps)
- Kubernetes does NOT manage users
- User management is offloaded to identity providers (LDAP, IAM, OIDC)

---

### 2️⃣ Service Accounts
- Used by Pods
- Allows Pods to interact with Kubernetes APIs
- Example:
  - Read ConfigMaps
  - Access Secrets

---

## RBAC Core Components

### Role / ClusterRole
- Defines **what actions are allowed**
- Permissions include:
  - get
  - list
  - create
  - delete
  - update

Role → namespace scoped  
ClusterRole → cluster-wide

---

### RoleBinding / ClusterRoleBinding
- Binds roles to users or service accounts

RoleBinding → namespace scoped  
ClusterRoleBinding → cluster-wide

---

## RBAC Flow Summary

1. Define permissions using Role or ClusterRole
2. Bind permissions using RoleBinding or ClusterRoleBinding
3. Assign access to Users or Service Accounts

---

## Custom Resources (CR)

Kubernetes provides a limited set of native resources:
- Pod
- Deployment
- Service
- ConfigMap
- Secret

But real-world platforms need more.

Examples:
- ArgoCD
- Istio
- Keycloak

These tools require **custom Kubernetes APIs**.

---

## Custom Resource Definition (CRD)

CRD allows us to:
- Extend Kubernetes API
- Define new resource types
- Add validation rules

CRD is a YAML file that defines:
- Structure of the custom resource
- Validation schema

---

## Custom Resource (CR)

- CR is an instance of a CRD
- Similar to how:
  - Deployment is an instance of Deployment schema

When a user creates a CR:
- It is validated against the CRD

---

## Custom Resource Controller (CRC)

Custom Controllers:
- Watch custom resources
- Take action based on desired state
- Similar to built-in Kubernetes controllers

Without a custom controller:
- CRs do nothing

Example:
- Ingress requires Ingress Controller
- CRDs require Custom Controllers

---

## CR / CRD / Controller Relationship

- CRD defines the schema
- CR is the actual object
- Controller enforces behavior

All three are required to extend Kubernetes functionality.

---

## Key Takeaways

- Services alone are not enough for enterprise traffic management
- Ingress provides advanced routing and cost efficiency
- Ingress Controller is mandatory
- RBAC secures cluster access
- Users and service accounts are handled differently
- CRDs extend Kubernetes APIs
- Controllers make custom resources functional

---

✅ Day 12 Completed – Kubernetes Advanced Concepts
