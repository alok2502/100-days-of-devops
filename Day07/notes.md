# Day 07 – Infrastructure as Code (IaC) & Terraform Fundamentals

## Topics Covered
- What is Infrastructure as Code (IaC)
- Problems with cloud-specific IaC tools
- Why Terraform was introduced
- Terraform architecture (API as Code)
- Terraform lifecycle
- Terraform core commands
- Terraform file structure
- Terraform state file
- Remote state and state locking
- Terraform modules
- Challenges with Terraform

---

## Understanding the Problem (Why IaC Is Needed)

Let’s assume our project is running on AWS.

- We can use CloudFormation Templates (CFT) to create infrastructure on AWS.
- If later we want to move to Azure, we cannot reuse CFT.
- We must rewrite everything using Azure ARM templates.
- If we move to on-premise, we need Heat templates.
- In a hybrid cloud setup, separate scripts are needed for each cloud.

This leads to:
- Vendor lock-in
- High migration effort
- Multiple scripts for the same infrastructure
- Poor maintainability

These tools (CFT, ARM, Heat) are **cloud-specific Infrastructure as Code tools**, but they do not solve the multi-cloud problem.

---

## What Is Infrastructure as Code (IaC)?

Infrastructure as Code means:
- Defining infrastructure using code
- Creating, modifying, and deleting infrastructure through automation
- Making infrastructure repeatable and version-controlled

---

## Why Terraform?

To solve the cloud-specific IaC problem, **HashiCorp introduced Terraform**.

Terraform:
- Is cloud-agnostic
- Supports multiple cloud providers
- Uses a concept called **API as Code**

Instead of learning different IaC tools for each cloud, we can learn Terraform once and use it everywhere.

---

## Terraform Architecture (API as Code)

Terraform works as an interface between:
- The user
- The cloud provider

Workflow:
- User writes requirements in Terraform configuration files
- Terraform communicates with cloud provider APIs
- Resources are created, updated, or deleted

Terraform does not create resources directly.
It talks to cloud APIs on our behalf.

---

## Terraform Lifecycle

Terraform follows a simple lifecycle:

1. Write
2. Plan
3. Apply

Terraform mainly works using four core commands:
- terraform init
- terraform plan
- terraform apply
- terraform destroy

---

## Terraform Core Commands

### terraform init
- Initializes the Terraform working directory
- Downloads provider plugins
- Prepares backend configuration

### terraform plan
- Shows what Terraform is going to create, update, or delete
- No changes are made

### terraform apply
- Creates or updates infrastructure
- Executes the planned changes

### terraform destroy
- Deletes all resources managed by Terraform

---

## Terraform File Structure

### main.tf
Used to define infrastructure.

Common blocks in Terraform files:
- terraform block
- provider block
- resource block

---

## Practical Work Done

- Installed AWS CLI
- Configured AWS credentials using CLI
- Installed Terraform
- Created a local-state Terraform file (main.tf)
- Created an EC2 instance using Terraform
- Ran:
  - terraform init
  - terraform plan
  - terraform apply
- Verified EC2 creation
- Deleted resources using terraform destroy

---

## Additional Terraform Files

### variables.tf
- Used to define variables
- Helps make code reusable and configurable

### outputs.tf
- Used to display outputs after resource creation
- Example: IP address, instance ID

---

## Terraform State File

After running terraform apply, a **state file** is created.

The state file:
- Tracks the current state of infrastructure
- Acts as the brain and memory of Terraform
- Helps Terraform understand what already exists

---

## Problems with Local State File

1. Contains sensitive information  
   - Cannot be stored in GitHub

2. Not shared  
   - Other team members don’t know the current state
   - Terraform may recreate resources from scratch

---

## Remote State

To solve state-related problems, we use **remote state**.

Examples:
- AWS S3
- Azure Blob Storage

Benefits:
- Centralized state
- Shared across team
- Prevents duplicate resource creation

---

## State Locking

When multiple people run Terraform at the same time:
- State file can get corrupted

Solution:
- State locking

Example:
- AWS DynamoDB is used for locking with S3 backend

Terraform locks the state file so only one change happens at a time.

---

## Environment Segregation

Best practice:
- Separate state files for different environments
  - dev
  - staging
  - production

This reduces blast radius and improves safety.

---

## Terraform Modules

Modules are used to:
- Reuse Terraform code
- Avoid duplication
- Improve maintainability

Modules allow writing code once and using it multiple times.

---

## Challenges with Terraform

1. State file is the single source of truth
2. Manual changes from cloud console are not tracked
3. Terraform is not bidirectional
4. Not fully GitOps-friendly
5. Drift can occur if changes are made outside Terraform

Git should be the single source of truth, but Terraform state creates an additional dependency.

---

## Key Takeaways

- IaC solves scalability and consistency problems
- Cloud-native IaC tools cause vendor lock-in
- Terraform enables multi-cloud infrastructure
- State file is critical but sensitive
- Remote state and locking are mandatory for teams
- Modules help scale Terraform usage
- Terraform requires discipline to avoid drift

---

✅ Day 07 Completed – Infrastructure as Code & Terraform
