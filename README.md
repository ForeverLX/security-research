# Darrius Grate | Offensive Security Portfolio

**Location:** Las Vegas, NV
**Target Role:** Red Team Operator / Vulnerability Researcher / Offensive Security Engineer
**Portfolio:** <https://github.com/ForeverLX/security-portfolio>

---

## QUICK NAVIGATION - Start Here

### For Hiring Managers (2-Minute Review)

1. **AD-RTS Certification** → [📜 View Certificate](https://labs.cyberwarfare.live/credential/achievement/692075a2524427687600cad2)

2. **Binary Exploitation Writeups** → [Challenge writeups](#binary-exploitation-challenge-writeups)

3. **Professional Methodology** → [📋 Enterprise AD Attack Chain](#enterprise-ad-attack-chain)

### For Technical Interviewers (5-Minute Review)

1. **Binary Exploitation Showcase** → [`projects/binary-exploitation/stacksmash-showcase.md`](projects/binary-exploitation/stacksmash-showcase.md)
2. **Web Security Mastery** → [25+ OWASP-style writeups](#web-application-security)
3. **Tool Development** → [🛠️ ACLGuard - AD Permission Auditor](https://github.com/ForeverLX/ACLGuard-Active-Directory-Permission-Auditor)

### For Recruiters (30-Second Review)

- ** Contact:** <Darrius.G@proton.me>

- ** Location:** Las Vegas, NV (Open to Remote)

- ** Availability:** Immediate

- ** Target:** Red Team / Vulnerability Research Roles

---

## PORTFOLIO HIGHLIGHTS

### Binary Exploitation (Challenge Writeups)

- **Technical Depth:** Memory corruption, ROP chains, exploit development with GDB/pwntools

- **Evidence:** [`projects/binary-exploitation/stacksmash-showcase.md`](projects/binary-exploitation/stacksmash-showcase.md)

### Enterprise AD Attack Chain

- **Certification:** Active Directory Red Team Specialist (AD-RTS) - November 2025

- **Scope:** Full domain compromise from initial access to persistence

- **Methodology:** Reconnaissance → Lateral Movement → Privilege Escalation → Domain Admin

- **Verification:** [📜 Official Certificate](https://labs.cyberwarfare.live/credential/achievement/692075a2524427687600cad2)

### Web Application Security

- **Scope:** 25+ OWASP-style writeups completed (December 2025 - February 2026)

- **Coverage:** SQLi, XSS, SSRF, SSTI, XXE, CSRF, IDOR, Race Conditions, File Upload

- **Documentation:** Detailed write-ups with exploitation steps and mitigation strategies

- **Evidence:** [`writeups/web-security/`](writeups/web-security/)

### Security Tool Development

- **ACLGuard:** Custom C-based Active Directory permission auditor

- **Purpose:** Identify risky ACLs and privilege escalation paths in AD environments

- **Technology:** C programming, LDAP queries, CSV/JSON output formats

- **Repository:** [github.com/ForeverLX/ACLGuard](https://github.com/ForeverLX/ACLGuard-Active-Directory-Permission-Auditor)

### Professional Methodology

- **Controlled Environment:** All testing in authorized lab environments

- **Documentation:** Step-by-step methodology with commands and outputs

- **Reporting:** Business impact analysis and mitigation recommendations

- **Ethics:** Strong emphasis on responsible disclosure and authorized testing

---

## PORTFOLIO STRUCTURE

```text

security-portfolio/
├── HIRING.md # One-page summary for recruiters
├── projects/ # Deep-dive technical projects
│   ├── binary-exploitation/ # StackSmash + pwn.college showcase
│   ├── ad-exploitation/ # Enterprise AD attack chain (in development)
│   └── tool-development/ # ACLGuard integration (in progress)
├── writeups/ # 35+ hands-on writeups
│   ├── web-security/ # OWASP Top 10 vulnerability types
│   ├── penetration-testing/ # Real-world scenarios
│   └── reverse-engineering/ # Binary analysis challenges
└── assets/certificates/ # Professional certifications

```

---

## SKILLS MATRIX

| Category                     | Skill                                           | Evidence                                         |
| ---------------------------- | ----------------------------------------------- | ------------------------------------------------ |
| **Binary Exploitation**      | x86_64 assembly, memory corruption, ROP chains  | StackSmash ranking, pwn.college completion       |
| **Web Application Security** | OWASP Top 10, advanced filter bypass            | 25+ OWASP-style writeups with exploitation steps |
| **Active Directory**         | Kerberos attacks, lateral movement, persistence | AD-RTS certification, attack chain methodology   |
| **Reverse Engineering**      | GDB analysis, binary analysis, debugging        | StackSmash challenges, Hackviser labs            |
| **Tool Development**         | C programming, security tool architecture       | ACLGuard repository with source code             |
| **Professional Skills**      | Client reporting, methodology, ethics           | Controlled environment testing approach          |

---

## CAREER NARRATIVE

**Transition:** Physical Security → Technical Offensive Security
**Approach:** Systematic, evidence-based skill development
**Proof:** Verifiable certifications + competitive rankings + tool development
**Leadership:** OWASP Las Vegas Chapter Founder & Leader

My background in physical security provides a holistic understanding of organizational risk. I apply the same systematic approach to offensive security: identify vulnerabilities, demonstrate impact, and provide actionable remediation.

---

## Field Report: Engineering a Security-Focused Linux Platform

### Motivation & Design Goals

Offensive workflows demand:

- Low attack surface

- High reliability and responsiveness

- Explicit control over service stacks

- Keyboard-centric operator workflows

- Repeatable, auditable configurations

**Core Stack:**

- Arch Linux (minimal base)

- Sway (Wayland)

- Terminals: Ghostty (primary), Warp (evaluated)

- Browser: Thorium with Wayland flags

- Compatibility via XWayland

---

## Key Engineering Decisions & Tradeoffs

### Wayland over X11

_Rationale:_ Reduced legacy risk and attack surface.

### Minimal Services and No Display Manager

_Rationale:_ Explicit session control, reduce background processes.

### Terminal Selection

- Ghostty (stable, minimal)

- Warp evaluated; usable but not primary due to integration complexity

### Audio Omission as Intentional Design Choice

Audio stacks add complexity with minimal operational benefit in offensive workflows — deliberately excluded to simplify system and reduce surface area.

---

## Troubleshooting & Lessons Learned

- CPU power management tuning before stability caused boot issues — _stability first_.

- Custom PipeWire configs regressed audio state — _baseline resets matter_.

- Applications expecting X11 require XWayland — _compatibility layer provisioned explicitly_.

---

## Current Status

- Stable Sway workstation environment

- Minimal services and attack surface

- Explicit session management via TTY

- Audio functioning on clean baseline (reboot enforced)

- Tooling integrated for offensive workflows

---

## VERIFICATION LINKS

| Achievement                              | Link                                                                                                  |
| ---------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| **Active Directory Red Team Specialist** | [📜 View Certificate](https://labs.cyberwarfare.live/credential/achievement/692075a2524427687600cad2) |
| **StackSmash Profile**                   | [🥇 3rd of 204](https://members.stacksmash.io/u/0119f178)                                             |
| **ACLGuard Tool**                        | [🛠️ Repository](https://github.com/ForeverLX/ACLGuard-Active-Directory-Permission-Auditor)            |
| **OWASP Las Vegas**                      | [🌐 Chapter Page](https://owasp.org/www-chapter-las-vegas/)                                           |

---

## CONTACT & NEXT STEPS

**Ready for Technical Interviews:**

- Available for technical challenges and live assessments

- Prepared for deep-dive discussions on any portfolio item

- Can provide additional materials upon request

**Connect With Me:**

- **Email:** [Darrius.G@proton.me](mailto:Darrius.G@proton.me)

- **LinkedIn:** [Darrius Grate](https://www.linkedin.com/in/darrius-grate/)

- **GitHub:** [github.com/ForeverLX](https://github.com/ForeverLX)

**Portfolio Last Updated:** February 2026

---

_All security testing conducted in controlled, authorized environments for educational purposes. This README is engineered to convey not just activity but disciplined technical judgment._
