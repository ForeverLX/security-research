# 🛠️ ACLGuard: Active Directory Permission Auditor

**Language:** C | **Domain:** Windows Security / Active Directory | **Status:** Functional Prototype

## 🎯 The Problem

Analyzing Active Directory Access Control Lists (ACLs) for dangerous permissions is manual and time-consuming. Security tools often show _what_ permissions exist but not the _exploitable paths_ they create. Blue teams need a fast, precise way to identify configurations that allow privilege escalation.

## 💡 The Solution

ACLGuard is a purpose-built tool written in C that directly queries Active Directory to:

1. **Enumerate ACLs** on domain objects (users, groups, OUs, computers).
2. **Analyze permissions** for known dangerous rights (e.g., `GenericAll`, `WriteOwner`, `ForceChangePassword`).
3. **Identify attack paths** by linking permissions between objects, highlighting how a compromised low-privileged account could reach high-value targets.

## 🏗️ Architecture & Design Choices

Choosing C over PowerShell or Python offers key advantages for an AD auditing tool:

- **Performance:** Native Windows API calls (`Active Directory Service Interfaces - ADSI`) allow efficient enumeration of large directories.
- **Stealth & Deployment:** A standalone executable has minimal dependencies and can run in constrained environments where scripting is restricted.
- **Learning Depth:** Implementing LDAP queries and security descriptor parsing in C provides deep understanding of both Windows security and AD internals.

### Core Components

1. **LDAP Connection Handler:** Authenticates to the domain and executes queries.
2. **Security Descriptor Parser:** Decodes raw `ntSecurityDescriptor` attributes.
3. **ACE (Access Control Entry) Analyzer:** Interprets permission bits against a known-dangerous rights list.
4. **Path Mapping Logic:** Builds graph-like relationships between objects based on permissions.

## 📟 Example Usage & Output

```bash

# Basic enumeration of a user object's ACLs
aclguard.exe --domain TELECORE.AD --user standarduser --pass Passw0rd! --target-user "Domain Admin"

# Analyze all ACLs for dangerous rights in an OU
aclguard.exe --domain TELECORE.AD --user standarduser --pass Passw0rd! --ou "OU=Servers,DC=telecore,DC=ad" --audit

Sample Finding Output:
[!] CRITICAL: User 'JSmith' has 'GenericAll' permission on Group 'Helpdesk Admins'
    ↳ Path: JSmith -> (GenericAll) -> Helpdesk Admins -> (MemberOf) -> Server Admins
    ↳ Impact: JSmith can add themselves to the Helpdesk Admins group, inheriting Server Admin privileges.

    🔬 Key Code Snippet: Parsing Security Descriptors
The following demonstrates the tool's core—translating raw binary security descriptors into actionable permissions:
// Simplified parsing logic (from main analysis module)
PACL dacl = NULL;
BOOL daclPresent = FALSE, daclDefaulted = FALSE;

if (GetSecurityDescriptorDacl(securityDescriptor, &daclPresent, &dacl, &daclDefaulted)) {
    if (daclPresent) {
        for (int i = 0; i < dacl->AceCount; i++) {
            if (GetAce(dacl, i, (LPVOID*)&ace)) {
                // Analyze ACE type, flags, mask, and trustee SID
                analyze_ace(ace, targetSid);
            }
        }
    }
}

📈 Future Development Roadmap
Graph Visualization: Generate .dot files for Graphviz to visualize attack paths.

BloodHound Integration: Output in Cypher format for direct import into BloodHound.

Risk Scoring Algorithm: Assign quantitative risk scores to discovered paths based on permission type and target value.

Pass-the-Hash Support: Accept NTLM hashes for authentication.

🧠 Why This Tool Demonstrates Professional Skills
Security Research: Identifies a real gap in existing tooling (path analysis).

Technical Execution: Implements a non-trivial Windows security feature in C.

Practical Utility: Provides immediate value for both red teams (finding escalation paths) and blue teams (auditing configurations).

Strategic Thinking: The roadmap shows planning for integration with industry-standard tools.

🔗 Repository & Contribution
The complete source code, build instructions, and issue tracker are available on GitHub:
github.com/ForeverLX/ACLGuard-Active-Directory-Permission-Auditor

Feedback and contributions are welcome. This is an active research project.
```
