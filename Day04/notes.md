# Day 04 – Bash Scripting & Advanced Linux Commands

## Topics Covered
- Bash scripting fundamentals
- Writing readable and debuggable scripts
- Process management
- Pipes and command chaining
- grep, awk, find, curl, wget
- if-else and loops
- Error handling and traps in bash
- Bash scripting from DevOps perspective

---

## Bash Scripting Fundamentals

Bash scripting is used to automate tasks in Linux.  
Today I focused on writing a **practical script** that prints:

- Free disk space
- Free memory
- Number of CPUs

While writing scripts, I learned the importance of:
- Adding **comments** to describe the purpose and metadata of the script
- Writing readable and maintainable scripts

---

## Debugging Bash Scripts

To debug bash scripts, we can use:

- set -x → enables debug mode and shows executed commands
- echo statements → make output user-friendly

If we do not want users to see executed commands:
- We can comment out `set -x`

---

## Process Management

### Viewing Running Processes
The command below shows all running processes:

ps -ef

---

## grep Command

The grep command is used to **search or filter output**.

Example use case:
- Searching for a specific process from a large output

grep is commonly used with pipes.

---

## Pipe ( | ) Operator

A pipe sends the **output of one command as input to another command**.

Example interview question:

date | echo "today is "

Output:
- today is

Explanation:
- `date` sends output to stdout
- `echo` does not read stdin
- So the output of `date` is discarded

---

## awk Command

awk is used to **process and format text output**.

Use case:
- If multiple "amazon" processes are running and we want their process IDs

Example flow:
- ps -ef → list processes
- grep amazon → filter amazon processes
- awk → extract PID column

This prints only the process IDs.

---

## Error Handling in Bash

### set -e
- Exits the script immediately when an error occurs
- Improves script reliability

### Drawback of set -e
- It does NOT fail if an error occurs inside a pipe
- It only checks the last command in the pipeline

### Solution
- Use set -o pipefail
- This ensures the script fails if **any command in the pipeline fails**

---

## curl vs wget

### curl
- Retrieves data from the internet
- Displays output in the terminal

### wget
- Downloads content from the internet
- Saves output to the local system

Both are widely used in DevOps automation.

---

## find Command

The find command is used to **search files across the system**.

Example:
- Searching a file from root directory

find / -name file-name

If permission errors occur:
- Use sudo at the beginning

This command is very powerful for troubleshooting.

---

## Conditional Statements

### if-else
- Used to make decisions in scripts
- Executes commands based on conditions

---

## Loops

### for loop
- Used to repeat tasks
- Helpful when running commands on multiple files, processes, or servers

---

## trap Command

The trap command is used to **capture and handle signals**.

Use cases:
- Cleanup tasks
- Handling script termination
- Managing unexpected exits

trap helps make scripts more robust and production-ready.

---

## Bash Scripting in DevOps

From a DevOps perspective, bash scripts are used for:
- Automation
- Infrastructure management
- Configuration management
- Monitoring and health checks
- CI/CD pipeline support scripts

---

## Key Takeaways

- Bash scripting is a core DevOps skill
- Debugging and readability are critical
- Pipes and text processing tools are extremely powerful
- Proper error handling makes scripts reliable
- Bash scripts help automate repetitive tasks

---

✅ Day 04 Completed – Bash Scripting & Linux Advanced Commands
