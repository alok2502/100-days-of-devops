# Day 06 – Configuration Management & Ansible Fundamentals

## Topics Covered
- What is Configuration Management
- Why Configuration Management is needed
- Problems with manual server management
- Configuration management tools
- Why Ansible is popular
- Ansible architecture and working
- Ansible vs Puppet
- Ansible prerequisites
- Ansible ad-hoc commands
- Ansible playbooks
- Ansible roles (high-level understanding)

---

## What Is Configuration Management?

Configuration Management is a way DevOps teams **manage and maintain configurations of servers and infrastructure** in a consistent and automated manner.

It ensures that:
- Servers are configured correctly
- Software versions are consistent
- Security patches are applied
- Systems remain in a desired state

---

## Why Configuration Management Is Needed?

Consider this scenario:

- A system administrator manages 100 on-premise servers:
  - 50 Windows
  - 25 CentOS
  - 25 Ubuntu

Daily responsibilities include:
- OS upgrades
- Installing packages
- Applying security patches
- Managing configurations

Doing this manually means:
- SSH into each server
- Perform tasks one by one
- High chance of human error
- Not scalable for a single person

If servers increase to 1000 or more, this approach becomes impossible.

With the rise of cloud computing, infrastructure size increased drastically, which created the need for **Configuration Management tools**.

---

## Configuration Management Tools

Some popular configuration management tools are:
- Puppet
- Chef
- Salt
- Ansible

Among these, **Ansible is the most widely adopted**.

---

## Why Ansible Is Popular?

### Push vs Pull Model
- Ansible uses a **push-based model**
- Configuration is pushed from the control machine
- Puppet uses a pull-based (master-slave) model

---

### Agentless Architecture
- Ansible is **agentless**
- No software required on target machines
- Puppet requires agents on all nodes

---

### Simple & Easy to Learn
- Ansible uses YAML
- Puppet requires learning Puppet DSL
- Ansible syntax is simple and readable

---

### Multi-OS Support
- Strong Linux support
- Good Windows support compared to other tools

---

### Extensibility
- Ansible is written in Python
- Custom modules can be written
- Modules can be shared using Ansible Galaxy

---

## Limitations of Ansible

- Debugging can be difficult
- Performance issues with very large scale (10k+ servers)
- Windows support is not as strong as Linux

---

## How Ansible Works (Linux & Windows)

- Linux machines: Uses SSH
- Windows machines: Uses WinRM

Cloud provider does not matter as long as:
- SSH is enabled
- Public IP is available

---

## Practical Setup Performed

- Created two EC2 instances on AWS:
  - One Ansible control machine
  - One target machine
- Installed Ansible on control machine
- Verified Ansible installation

---

## Passwordless Authentication Setup

Ansible requires passwordless authentication.

Steps followed:
- Generated SSH key pair using ssh-keygen on Ansible machine
- Copied public key to target machine’s authorized_keys
- Verified SSH access without password

This completed the Ansible prerequisites.

---

## Ansible Ad-Hoc Commands

It is not mandatory to write a playbook for every task.

For small tasks, **Ansible ad-hoc commands** can be used.

Example task:
- Create a file on the target machine

Steps:
- Created an inventory file with target IP address
- Used Ansible CLI with:
  - -i for inventory
  - -m for module
  - -a for arguments
- Verified file creation on target machine

Grouping can also be done in inventory files using square brackets [].

---

## Ansible Playbooks

For multiple or complex tasks, playbooks are used.

Playbooks are written in YAML.

Playbook concepts learned:
- --- indicates start of YAML file
- Play starts with -
- name describes the task
- hosts specifies target machines
- become enables root privileges
- tasks contain actual configuration steps

---

## Playbook Executed

A playbook was written to:
- Install nginx
- Start nginx service

Execution was done using ansible-playbook command.

Verification confirmed nginx was installed and running on the target machine.

---

## Verbosity in Ansible

To increase logging and debugging output:
- -v
- -vv
- -vvv

Higher verbosity gives more detailed execution logs.

---

## Why Ansible Roles Are Needed?

For large-scale setups (example: Kubernetes cluster):
- 3 EC2 machines (1 master, 2 nodes)
- Infrastructure created using Terraform
- Configuration handled using Ansible

Such setups require:
- 50–60 tasks
- Multiple configurations
- Reusability

Writing everything in a single playbook is not efficient.

---

## Ansible Roles

Ansible roles provide:
- Better structure
- Reusability
- Maintainability
- Separation of concerns

Roles are the preferred way to manage complex configurations.

---

## Key Takeaways

- Configuration Management solves scalability and consistency problems
- Manual server management does not scale
- Ansible is agentless and easy to use
- SSH-based communication simplifies setup
- Ad-hoc commands are useful for small tasks
- Playbooks handle complex workflows
- Roles are essential for large configurations

---

✅ Day 06 Completed – Configuration Management & Ansible