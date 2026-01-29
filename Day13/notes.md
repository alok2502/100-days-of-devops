# Day 13 – ConfigMaps, Secrets & Monitoring Basics in Kubernetes

## Topics Covered
- Why ConfigMaps and Secrets are needed
- ConfigMaps usage
- Secrets usage
- ConfigMaps vs Secrets
- Using ConfigMaps as environment variables
- ConfigMaps with volume mounts
- Difference between kubectl create and kubectl apply
- Secrets encryption basics
- Monitoring basics (Prometheus & Grafana)

---

## Why ConfigMaps and Secrets Are Needed

Applications running in Kubernetes often require configuration values such as:
- Database name
- Port number
- Environment-specific values

Hardcoding these values inside container images is a bad practice.

Kubernetes provides:
- **ConfigMaps** for non-sensitive configuration
- **Secrets** for sensitive information

These values can be consumed by Pods later when required.

---

## ConfigMaps

ConfigMaps are used to store **non-sensitive configuration data**, such as:
- Database port
- Application configuration values
- Feature flags

ConfigMaps can be consumed by Pods in two ways:
- As environment variables
- As volume mounts

---

## Why Secrets Are Needed If ConfigMaps Exist?

A natural question:
If ConfigMaps can store configuration, why do we need Secrets?

Reason:
- Kubernetes stores all cluster data in **etcd**
- If etcd is compromised, all stored data is exposed

To reduce risk:
- ConfigMaps are used for non-sensitive data
- Secrets are used for sensitive data like:
  - Username
  - Password
  - Tokens

Kubernetes encrypts Secrets before storing them in etcd and also supports **custom encryption mechanisms**.

---

## Using ConfigMaps as Environment Variables

Steps performed:
- Created a ConfigMap YAML containing database port
- Referenced ConfigMap in Deployment using `configMapKeyRef`
- Applied both ConfigMap and Deployment

Verification:
- Exec into Pod
- Checked environment variables
- Confirmed DB port value was injected successfully

---

## ConfigMap Update Issue with Environment Variables

Observation:
- After updating ConfigMap value
- Environment variable inside Pod did NOT change automatically

Reason:
- Environment variables are injected at Pod startup
- Pod restart is required for changes to take effect

---

## kubectl create vs kubectl apply

- kubectl create:
  - Used only for creating new resources
  - Fails if resource already exists

- kubectl apply:
  - Can create or update resources
  - Preferred for declarative workflows

This is why `kubectl apply` is commonly used in production.

---

## Using ConfigMaps with Volume Mounts

To solve the dynamic update problem:
- ConfigMaps were mounted as volumes
- Volume was mounted inside container
- Application read configuration from mounted files

Result:
- ConfigMap updates were reflected dynamically
- No Pod restart required

---

## Secrets in Kubernetes

Secrets store sensitive information such as:
- Credentials
- Tokens
- Passwords

Secrets can be consumed:
- As environment variables
- As volume mounts

---

## Secrets Encryption Observation

- Secrets appear Base64 encoded when viewed using describe commands
- Kubernetes encrypts Secrets before storing them in etcd
- Custom encryption can be configured for stronger security

---

## ConfigMaps vs Secrets (Summary)

- ConfigMaps:
  - Non-sensitive data
  - Stored in plain text in etcd

- Secrets:
  - Sensitive data
  - Encrypted before storage
  - Better security controls

---

## Monitoring Basics (Prometheus & Grafana)

Kubernetes monitoring commonly uses:
- **Prometheus**
- **Grafana**

---

## Prometheus

Prometheus:
- Scrapes metrics from Kubernetes components
- Collects data from:
  - Pods
  - Nodes
  - Services
- Uses exporters to expose metrics
- Stores data as time-series
- Supports querying metrics

---

## Grafana

Grafana:
- Connects to Prometheus as a data source
- Visualizes metrics using dashboards
- Displays:
  - CPU usage
  - Memory usage
  - Pod health
  - Cluster performance
- Supports importing custom dashboards

---

## Key Takeaways

- ConfigMaps manage non-sensitive configuration
- Secrets manage sensitive information securely
- Environment variables do not update dynamically
- Volume mounts enable dynamic configuration updates
- kubectl apply is preferred over create
- Prometheus + Grafana is a common monitoring stack
- Monitoring is essential for production Kubernetes

---

✅ Day 13 Completed – ConfigMaps, Secrets & Monitoring Basics
