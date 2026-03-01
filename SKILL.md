---

name: linux-privesc-guide

description: Structured Linux privilege escalation enumeration workflow. Use when user says "help with Linux privesc", "enumerate Linux for root", or "privilege escalation steps".

---





\# Linux Privilege Escalation Guide



\## Phase 1: Basic System Enumeration

Run:

\- uname -a

\- id

\- cat /etc/os-release



Goal:

Understand kernel version, current user privileges, OS details.



---



\## Phase 2: SUID \& SGID Check

Run:

\- find / -perm -4000 -type f 2>/dev/null



Goal:

Identify binaries that run as root.



---



\## Phase 3: Sudo Permissions

Run:

\- sudo -l



Goal:

Check if current user can execute commands as root.



---



\## Phase 4: Writable Files \& Directories

Run:

\- find / -writable -type f 2>/dev/null



Goal:

Identify misconfigured files that allow privilege abuse.



---



\## Phase 5: Kernel Exploit Check

Compare:

\- Kernel version from Phase 1

Against:

\- Known Linux exploit databases

