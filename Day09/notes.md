# Day 09 – Multi-Stage Docker Builds, Distroless Images & Container Internals

## Topics Covered
- Multi-stage Docker builds
- Why multi-stage builds are needed
- Distroless images
- Bind mounts vs volumes
- Docker volumes lifecycle
- Container networking fundamentals
- Bridge, host, and custom bridge networks
- Practical container isolation

---

## Why Multi-Stage Docker Builds Are Needed

Consider a 3-tier application:
- Frontend: React
- Backend: Spring Boot
- Database: MySQL

If we build everything in a single Docker image:
- Ubuntu base image: ~400 MB
- Java runtime: ~300 MB
- React dependencies: ~200 MB
- MySQL: ~100 MB

Total image size becomes **more than 1 GB**.

Containers were introduced to be lightweight, so this defeats the purpose.

---

## What Is a Multi-Stage Docker Build?

Multi-stage builds allow us to:
- Build the application in multiple stages
- Use heavy images only during build time
- Keep only runtime dependencies in the final image

Example idea:
- Stage 1: Build the application
- Stage 2: Copy only the final binary/artifacts
- Final image contains only runtime + binary

Result:
- Final image size reduced to ~150–200 MB
- Faster image pulls
- Less storage usage
- Smaller attack surface

---

## Distroless Images

Distroless images are **minimal images that contain only runtime dependencies**.

Key characteristics:
- No package manager
- No shell
- No debugging tools like ls, find, bash

### Advantages of Distroless Images
- Extremely small image size
- Improved security
- Reduced attack surface

Since there is no shell, attackers cannot easily interact with the container even if they gain access.

---

## Biggest Challenge with Containers (Ephemeral Nature)

Containers are **ephemeral**, meaning:
- They can stop or restart anytime
- Data inside containers is lost if not persisted

### Problem Scenarios
- Logs written inside container are lost on restart
- Backend data lost affects frontend
- Cron jobs writing files lose data
- Applications cannot directly read host files

---

## Docker Solutions for Data Persistence

Docker provides two solutions:
1. Bind mounts
2. Volumes

---

## Bind Mounts

Bind mounts map a **specific directory of the container to a directory on the host**.

Example:
- Container path: /app
- Host path: /app/container1

Even if the container goes down:
- Data remains on the host
- New container can reuse the same data

### Limitations of Bind Mounts
- Tightly coupled to a specific host
- Not portable
- Less flexible lifecycle management

---

## Docker Volumes

Volumes provide a **better abstraction for persistent data**.

Key features:
- Managed by Docker
- Independent lifecycle
- Can be attached/detached from containers
- Can be backed by external storage (EC2, NFS, S3, etc.)

Volumes are preferred over bind mounts in production.

---

## Docker Volume Commands Practiced

- Create volume
- List volumes
- Inspect volume
- Remove volume

Important note:
- A volume cannot be deleted if it is attached to a running container
- Container must be stopped before removing the volume

---

## Bind Mount vs Volume (Summary)

- Bind Mount:
  - Host dependent
  - Limited lifecycle control

- Volume:
  - Docker-managed
  - Better lifecycle
  - Portable
  - Supports external storage

Recommended approach: **Use volumes over bind mounts**.

---

## Docker Networking Basics

Docker networking enables:
- Communication between containers
- Communication with host system
- Isolation where required

---

## Default Docker Network (Bridge Network)

- Default network created by Docker
- Uses docker0 bridge
- Each container gets a virtual ethernet interface
- Allows containers to communicate with host and each other

Without this network, containers cannot communicate.

---

## Host Network

- Container shares host’s network directly
- No isolation
- IP address is not assigned to container

This is **highly insecure** and not recommended for most use cases.

---

## Overlay Network

- Used in container orchestration
- Enables communication across multiple hosts
- Common in Kubernetes and Docker Swarm

(This will be covered later.)

---

## Container Isolation Using Custom Bridge Networks

Problem:
- Some containers should communicate (login, logout)
- Some containers should be isolated (payment)

Solution:
- Use custom bridge networks

---

## Practical Networking Scenario

- Created a custom bridge network
- Ran login and logout containers on default bridge
- Verified they were in the same subnet
- Successfully pinged each other

Then:
- Ran payment container using custom bridge network
- Payment container was in a different subnet
- login/logout could not ping payment container

This ensured proper isolation.

---

## Host Network Observation

When a container is run using host networking:
- No container IP is assigned
- Container directly uses host network interface
- This breaks isolation

---

## Key Takeaways

- Multi-stage builds drastically reduce image size
- Distroless images improve security
- Containers are ephemeral by nature
- Volumes are best for persistent data
- Docker networking controls communication
- Custom bridge networks enable isolation
- Host networking is insecure and risky

---

✅ Day 09 Completed – Advanced Docker Concepts
