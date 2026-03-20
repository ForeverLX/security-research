# security-research

**Azrael Security — Offensive Security Research**

Published by [ForeverLX](https://github.com/ForeverLX) | Azrael Security™

> This repository documents original security research, adversary emulation technique development, and infrastructure-focused vulnerability analysis produced by Azrael Security. Work is conducted on authorized, self-operated infrastructure. All findings are mapped to MITRE ATT&CK where applicable.

---

## Research Areas

### 1. Container Boundary Research
*Status: Active*

Investigating Linux container isolation boundaries as they apply to real offensive infrastructure. Focus areas:

- **Filesystem and mount abuse** — overlayfs behavior, bind mount escapes, volume permission misconfigurations in rootless Podman and Docker contexts
- **Namespace privilege boundaries** — user namespace privilege mapping, PID/mount namespace isolation failures, capability leakage across namespace transitions
- **Process visibility leaks** — `/proc` exposure from within containers, cross-container PID visibility under different namespace configurations
- **Infrastructure applicability** — how these primitives map to real red team infrastructure (C2 isolation, agent staging environments, container-based implant delivery)

Research platform: Cerberus (Podman rootless, Arch Linux) and Tairn (Docker, NixOS 24.11) — live infrastructure, not synthetic lab VMs.

### 2. Linux Kernel & Systems Research
*Status: Early stage — building toward*

Low-level Linux systems research with a long-term focus on kernel exploitation primitives. Current entry point is container boundary analysis (userspace/kernel interface). Planned progression:

- **Syscall boundary analysis** — userspace → kernel transitions, where validation occurs and where it doesn't
- **Privilege escalation primitives** — capability abuse, namespace escape, SUID/SGID misuse
- **Kernel exploitation foundations** — memory corruption in kernel context, ret2usr, kernel ROP (long-term track)
- **CVE analysis** — dissecting published kernel CVEs to understand root cause and exploitation mechanics

Research platform: NightForge (Arch Linux, zen kernel).

### 3. Reverse Engineering
*Status: Active — ongoing challenge series*

Documented RE methodology development through progressive challenge work, building toward application to real binaries and CVE analysis.

- **re-1** — ELF 32-bit, byte-wise comparison loop, static + GDB analysis
- **re-2** — ELF 64-bit stripped, hex decoding pipeline, XOR-based custom comparison logic
- *Ongoing: additional StackSmash RE challenges as completed*

### 4. Active Directory Attack Paths
*Status: Ongoing (course-integrated)*

Technique documentation from CRTA and CRT-ID coursework (CyberWarfare Labs), integrated with hands-on lab work on Tairn. Every technique documented with:
- Mechanical explanation of what is actually happening at the protocol/system level
- MITRE ATT&CK mapping
- Detection considerations
- Tool invocation and output

### 5. Red Team Infrastructure Research
*Status: Ongoing*

Operational security and architecture research applied to the Veil infrastructure project:
- WireGuard mesh architecture for multi-node C2 environments
- Mythic C2 deployment hardening (network isolation, firewall posture)
- Declarative NixOS for reproducible attack nodes
- Rootless container patterns for operational security

---

## Active Research — Container Boundary Analysis

*This section will be populated as the research progresses. Structure is established in advance to hold the work.*

```
research/container-boundaries/
├── README.md               # Research overview and methodology
├── 01-environment-setup/   # Lab setup, tooling, baseline measurements
├── 02-filesystem-mounts/   # Findings: overlayfs, bind mounts, volume abuse
├── 03-namespace-analysis/  # Findings: user/pid/mount namespace boundaries
├── 04-proc-visibility/     # Findings: /proc exposure and PID leaks
├── 05-infrastructure-impact/ # How findings map to offensive infra use cases
└── report/                 # Final research artifact (MITRE-mapped)
```

**Research methodology:**
1. Establish baseline: document expected isolation behavior per container runtime
2. Identify boundary: find the exact syscall, kernel feature, or configuration that enforces the control
3. Test deviation: construct minimal reproduction case that demonstrates the boundary condition
4. Map impact: connect finding to a real offensive or defensive use case
5. Document: write-up suitable for technical audience (not a CTF walkthrough)

---

## Technique Library

Documented techniques from lab work and course progression. Each entry includes mechanical explanation, reproduction steps, and ATT&CK mapping.

*Actively populating as course work progresses on Tairn.*

| Technique | ATT&CK ID | Platform | Status |
|---|---|---|---|
| Kerberoasting | T1558.003 | Windows AD | Documented |
| AS-REP Roasting | T1558.004 | Windows AD | Documented |
| DCSync | T1003.006 | Windows AD | Documented |
| Golden Ticket | T1558.001 | Windows AD | Documented |
| Domain Account Enumeration | T1087.002 | Windows AD | Documented |
| RE: ELF 32-bit byte-wise validation | — | Linux | Complete — `techniques/linux/re/re-1` |
| RE: ELF 64-bit stripped, XOR comparison | — | Linux | Complete — `techniques/linux/re/re-2` |
| *Container escape via mount* | *TBD* | Linux | In progress |
| *Namespace boundary abuse* | *TBD* | Linux | In progress |
| *Kernel privilege escalation primitives* | *TBD* | Linux | Planned |

---

## Repository Structure

```
security-research/
├── README.md
├── research/
│   ├── container-boundaries/   # Active flagship research
│   ├── kernel/                 # Linux kernel & systems research
│   ├── active-directory/       # AD technique documentation
│   └── infrastructure/         # Red team infra research notes
├── techniques/
│   ├── ad/                     # Per-technique writeups (AD)
│   └── linux/
│       ├── re/                 # Reverse engineering writeups
│       │   ├── re-1/
│       │   └── re-2/
│       └── kernel/             # Kernel exploitation technique notes
├── labs/
│   └── tairn/                  # Lab work documented from Tairn
└── assets/
    └── certificates/           # Certifications (AD-RTS, CAPT, COSJ)
```

---

## Infrastructure

Research is conducted on the [Veil](https://github.com/ForeverLX/veil) infrastructure:

- **Cerberus** — Arch Linux edge node, rootless Podman (primary container research platform)
- **Tairn** — NixOS 24.11, Mythic C2 + Docker (AD lab work, agent testing)
- **NightForge** — Arch Linux operator workstation ([nightforge](https://github.com/ForeverLX/nightforge))

---

## Certifications

| Certification | Issuer | Status |
|---|---|---|
| Active Directory Red Team Specialist (AD-RTS) | CyberWarfare Labs | Completed |
| Certified Associate Penetration Tester (CAPT) | HackViser | Completed |
| Certified Offensive Security Junior (COSJ) | RedTeam Ops | Completed |
| Certified Red Team Analyst (CRTA) | CyberWarfare Labs | In Progress |
| Certified Red Team Infrastructure Developer (CRT-ID) | CyberWarfare Labs | In Progress |

---

## Disclaimer

All research is conducted on self-operated infrastructure for authorized security research purposes. Findings and techniques are documented for educational and professional development purposes only.

---

**Author:** Darrius Grate (ForeverLX) | Azrael Security™
