# Day 18 – AWS Basics: Cloud Computing, IAM & EC2

## Focus of the Day
- What is Cloud Computing
- Private Cloud vs Public Cloud
- Why Public Cloud is Popular
- Why AWS is the Market Leader
- AWS IAM (Authentication & Authorization)
- IAM Core Components
- EC2 Overview
- Practical: Deploying Jenkins on EC2

---

## What Is Cloud Computing?

In simple terms, cloud means:
- Using computing resources (servers, storage, networking)
- Without knowing where they physically exist
- Accessed over the internet

Example:
- We use virtual machines (servers) without knowing their physical location.

---

## Private Cloud

Private cloud means:
- Infrastructure is owned and maintained by an organization
- Datacenters are managed internally
- Full responsibility of maintenance lies with the organization

Challenges:
- High cost
- Infrastructure maintenance
- Hardware management
- Skilled manpower required

---

## Public Cloud

Public cloud is provided by third-party vendors like:
- AWS
- Azure
- GCP

Key idea:
- Anyone with proper authentication and authorization can create resources
- No need to manage physical datacenters

Advantages:
- Pay-as-you-go
- No infrastructure maintenance
- Fast provisioning
- High scalability

---

## Private Cloud vs Public Cloud

| Private Cloud | Public Cloud |
|--------------|-------------|
| Organization manages infrastructure | Cloud provider manages infrastructure |
| High upfront cost | No upfront cost |
| Maintenance overhead | No maintenance burden |
| Limited scalability | Highly scalable |

---

## Why Is Public Cloud So Popular?

Many believe cost is the main reason — which is partially true.

The real reasons:
- No datacenter maintenance
- No hardware procurement
- Easy scalability
- Ideal for startups and mid-scale organizations
- Faster time to market

Maintenance and operational overhead is the biggest reason companies move to public cloud.

---

## Why Is AWS So Popular?

AWS dominates the cloud market mainly because:
- First-mover advantage
- Pioneer in cloud computing
- Rich set of services
- Mature and stable platform
- Large global infrastructure

This gives AWS a larger market share compared to Azure and GCP.

---

## AWS IAM (Identity and Access Management)

IAM solves two core security problems:
- Authentication
- Authorization

---

## Authentication vs Authorization (Bank Example)

### Authentication
- Verifies **who you are**
- Example:
  - Only account holders can enter the bank

### Authorization
- Verifies **what you are allowed to do**
- Example:
  - Customers → service area
  - Managers → finance & locker areas
  - Peons → document area (limited actions)

---

## IAM in AWS

In AWS:
- Having an account means authentication
- Permissions decide what actions can be performed

Giving everyone root access is dangerous:
- Anyone can create or delete critical resources
- High risk of accidental damage

IAM ensures least-privilege access.

---

## Core Components of AWS IAM

### IAM Users
- Created for individual people
- Used for authentication

---

### IAM Policies
- Define permissions
- Specify:
  - Which services can be accessed
  - What actions can be performed

---

### IAM Groups
- Collection of users
- Used for easier permission management

Example:
- All QA engineers in one group
- Grant read-only access to the group instead of individual users

---

### IAM Roles
- Used for temporary access
- Not tied to a specific user

Use cases:
- One AWS service accessing another service
- Cross-account access
- Applications running on EC2 accessing AWS resources

Roles are preferred over hardcoded credentials.

---

## EC2 – Elastic Compute Cloud

EC2 provides:
- Virtual servers in the cloud
- On-demand compute capacity

Problems EC2 solves:
- No need to buy physical servers
- Scalable infrastructure
- Full control over OS and applications

---

## Practical: Deploying Jenkins on EC2

Steps performed:
1. Created an EC2 instance
2. Installed Jenkins on the server
3. Updated inbound security group rules
4. Allowed port 8080 for external access
5. Accessed Jenkins UI from laptop browser

This demonstrated:
- Compute provisioning
- Security group configuration
- Real-world application deployment

---

## Key Takeaways

- Cloud abstracts physical infrastructure
- Public cloud removes maintenance overhead
- AWS leads due to first-mover advantage
- IAM controls authentication and authorization
- Users, groups, policies, and roles are core IAM components
- EC2 provides scalable compute resources
- Security groups control inbound access

---

## What’s Next (Day 19 Plan)

- Deeper dive into EC2
- Security Groups vs NACLs
- Storage basics (EBS, S3)
- IAM best practices

---

✅ Day 18 Completed – AWS Cloud & IAM Basics
