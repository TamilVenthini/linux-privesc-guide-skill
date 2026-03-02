name: linux-privesc-guide
description: Structured Linux privilege escalation methodology with environment validation and controlled execution phases.

# Linux Privilege Escalation – Structured Skill Workflow

---

## 0. Environment Validation (MANDATORY GATE)

Before Phase 1, confirm:

1. Target system is Linux.
   - Verify using: uname or /etc/os-release

2. Local shell access is available.

3. Engagement is authorized (lab or permitted environment).

If any condition fails:
Stop execution.
Notify user workflow is not applicable.

---

## Execution Principles

- Enumeration before exploitation.
- Stop immediately upon confirmed root access.
- Do not perform post-exploitation persistence.
- Stay within privilege escalation scope only.
- Generate structured output.

---

## Phase 1 – System Context

Run:
- uname -a
- id
- cat /etc/os-release

Goal:
Understand kernel version, user privileges, OS details.

---

## Phase 2 – Privilege Audit

Run:
- sudo -l

If output shows:
(ALL : ALL) ALL

Immediate escalation allowed.
Proceed to root verification.
Stop further enumeration.

---

## Phase 3 – SUID / SGID Enumeration

Run:
- find / -perm -4000 -type f 2>/dev/null

Analyze binaries for shell escape potential.

---

## Phase 4 – Cron & Scheduled Tasks

Check:
- /etc/crontab
- systemd timers

Look for writable scripts executed as root.

---

## Phase 5 – Writable File Discovery

Run:
- find / -writable -type f 2>/dev/null

Identify configuration abuse opportunities.

---

## Phase 6 – Capabilities

Run:
- getcap -r / 2>/dev/null

Analyze privilege escalation via Linux capabilities.

---

## Phase 7 – Kernel Exploit Mapping

Compare:
Kernel version against known exploit databases.

---

## Escalation Confirmation

After successful escalation:

Run:
- id

Confirm:
uid=0(root)

Then:
Stop workflow.
Generate structured escalation summary.

---

## Failure Handling

If no escalation vector is found:

Generate structured failure report including:
- Enumeration completed
- Attack surface reviewed
- No exploitable misconfiguration found