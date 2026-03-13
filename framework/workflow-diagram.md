flowchart TD

A[Start Privilege Escalation Workflow] --> B[Environment Validation]

B -->|Linux Confirmed| C[Phase 1: System Context]
B -->|Not Linux| Z[Stop - Out of Scope]

C --> D[Phase 2: Privilege Audit]

D -->|Full Sudo Access| R[Immediate Escalation]
D -->|Limited Access| E[Phase 3: SUID Check]

E --> F[Phase 4: Cron Review]
F --> G[Phase 5: Writable Files]
G --> H[Phase 6: Capabilities]
H --> I[Phase 7: Kernel Mapping]

I -->|Exploit Found| R
I -->|No Exploit| X[Generate Escalation Summary]

R --> S[Generate Escalation Summary]
S --> END[Stop Workflow]
