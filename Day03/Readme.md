# Day 03 – Secure Shell (SSH)

## 🔑 What is SSH?
- **SSH (Secure Shell)** is a protocol that creates a **secure, encrypted tunnel** between two machines.  
- It allows you to connect to a **remote machine** and interact with it as if you were sitting right in front of it.  
- When we use SSH:
  - Our **local laptop/PC** becomes the **controller**.  
  - The **remote machine** becomes the **execution target**.  

---

## 🔐 Why Use SSH Keys Instead of Passwords?
- **Passwords**
  - Can be leaked or stolen.  
  - Vulnerable to brute‑force attacks.  
  - Often reused by humans across systems.  
- **SSH Keys**
  - Private key **never leaves your machine**.  
  - Public key is stored on the server.  
  - Stronger security, widely used in companies for remote logins.  

---

## ☁️ My Hands‑On Practice
- Logged into an **AWS EC2 instance** using a `.pem` private key.  
- Practiced basic Linux commands:

```bash
whoami   # Shows the current logged-in user
pwd      # Prints the current working directory
ls       # Lists files and directories
vim      # Opens the Vim text editor
```

## 📌 Key Takeaways
- SSH is the backbone of secure remote administration.
- Keys > Passwords for reliability and safety.
- Real‑world DevOps work (like EC2 login) heavily relies on SSH.