# Day 19 – AWS VPC Deep Dive
## #100DaysOfDevOps

## What is Cloud?
Cloud computing means using compute, storage, and networking resources that exist somewhere else, without knowing or managing their physical location.

There are two main types of cloud:
- Private Cloud: Infrastructure maintained by a single organization.
- Public Cloud: Infrastructure provided by vendors like AWS, Azure, and GCP, accessible to anyone with proper authentication and authorization.

Public cloud became popular mainly because startups and mid-sized organizations cannot afford the cost and maintenance of their own data centers.

AWS is the market leader due to its first-mover advantage and early maturity in cloud services.

---

## Understanding VPC (Virtual Private Cloud)

VPC can be understood using a gated society analogy.

- The gated society represents the VPC
- Boundary walls represent network isolation
- Address range of the society represents CIDR
- Houses or projects represent subnets
- Entry gate represents the Internet Gateway
- Roads inside the society represent route tables
- Watchman at each house represents Security Groups

A VPC provides a logically isolated network inside the AWS public cloud.

---

## CIDR and Subnetting

CIDR defines the IP address range of a VPC, for example 10.0.0.0/16.

Subnetting divides a VPC into smaller IP ranges for different projects or tiers such as frontend, backend, and database.

Examples:
- /24 provides 256 IP addresses
- /30 provides 4 IP addresses

---

## Public and Private Subnets

Public Subnet:
- Has a route to an Internet Gateway
- Used for load balancers and bastion hosts

Private Subnet:
- Does not have direct internet access
- Used for application servers and databases

Private resources are accessed through public-facing components like load balancers.

---

## Internet Gateway and Route Tables

Internet Gateway enables communication between the VPC and the internet.

Route Tables define how traffic flows between subnets, gateways, and other network components.

Each subnet must be associated with a route table to control traffic routing.

---

## Security Groups (SG)

Security Groups operate at the instance level and are stateful.

Default behavior:
- Inbound traffic is denied
- Outbound traffic is allowed

Security Groups explicitly allow traffic on required ports such as 22, 80, and 8000 and act as the last line of defense before traffic reaches the application.

---

## Network ACLs (NACL)

Network ACLs operate at the subnet level and are stateless.

Key points:
- Support both allow and deny rules
- Rules are evaluated in ascending order
- First matching rule is applied
- Default rule is deny

NACLs provide an additional layer of security at the subnet level.

---

## NAT Gateway

Problem:
Instances in private subnets need outbound internet access, but assigning public IPs is insecure.

Solution:
- NAT Gateway provides outbound internet access for private subnets
- Performs Source NAT (SNAT)
- Masks private IP addresses using a public IP

---

## Practical Observation

A Python application was running on port 8000.

- NACL allowed traffic, but Security Group blocked it, so the application was not accessible
- After allowing port 8000 in the Security Group, the application became accessible
- Denying port 8000 in the NACL blocked the application again

Traffic must be allowed at both Security Group and NACL levels.

---

## Route 53 (AWS DNS Service)

Route 53 is the DNS service provided by AWS.

- Resolves domain names to IP addresses
- Supports AWS-purchased and external domains
- Routes traffic to load balancers or other AWS resources

DNS resolution happens before traffic reaches application resources.

---

## Key Takeaways

- VPC is the foundation of AWS networking
- CIDR defines IP address boundaries
- Subnets enable isolation and scalability
- Security Groups and NACLs provide layered security
- NAT Gateway enables secure outbound access
- Route 53 manages DNS and traffic routing

---

## Status

- AWS VPC fundamentals completed
- Networking and security concepts understood with hands-on practice

---

End of Day 19
