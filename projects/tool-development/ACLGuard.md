# 🛠️ ACLGuard: Active Directory Permission Auditor

**Language:** C | **Domain:** Windows Security / Active Directory | **Status:** Active Development

## 🎯 The Problem

Analyzing Active Directory Access Control Lists (ACLs) for dangerous permissions is manual and time-consuming. Security tools often show _what_ permissions exist but not the _exploitable paths_ they create. Blue teams need a fast, precise way to identify configurations that allow privilege escalation.

## 💡 The Solution

ACLGuard is a purpose-built tool written in C that queries Active Directory to:

1. **Enumerate directory objects** (users, groups, OUs, computers).
2. **Analyze permissions** for known dangerous rights.
3. **Identify attack paths** by linking permissions between objects.

## 🏗️ Architecture & Design Choices

Choosing C over PowerShell or Python offers key advantages for an AD auditing tool:

- **Performance:** Native binaries handle large directory scans efficiently.
- **Portability:** CLI runs with standard LDAP libraries and minimal dependencies.
- **Learning Depth:** Implementing LDAP queries and permission analysis in C builds deep AD and Windows security knowledge.

### Core Components

1. **LDAP Connection Handler:** Authenticates to the directory and executes queries.
2. **Permission Analyzer:** Interprets group membership and high-risk permission flags.
3. **Risk Engine:** Scores users/groups based on detected privileges.
4. **Export + CLI:** JSON/CSV export and deterministic mock mode for demos/tests.

## 📟 Example Usage & Output

```bash
# Mock demo flow
./aclguard --mock status
./aclguard --mock alerts --recent
./aclguard --mock correlate --attack kerberoasting

# Live LDAP scan (env vars configured)
./aclguard status
./aclguard alerts --recent
```

Sample Finding Output:
```text
[!] HIGH: User 'jdoe' flagged with privileged group membership
    ↳ Impact: Privileged access detected without documented change control.
```

### 🔬 Key Implementation Focus

The core logic prioritizes deterministic, explainable findings over black-box scoring.

## 📈 Future Development Roadmap

- Graph Visualization: Generate .dot files for Graphviz to visualize attack paths.
- BloodHound Integration: Output in Cypher format for direct import into BloodHound.
- Risk Scoring Algorithm: Assign quantitative risk scores to discovered paths based on permission type and target value.

## 🧠 Why This Tool Demonstrates Professional Skills

- **Security Research:** Identifies a real gap in existing tooling (path analysis).
- **Technical Execution:** Implements a non-trivial Windows security feature in C.
- **Practical Utility:** Provides immediate value for both red teams and blue teams.
- **Strategic Thinking:** Roadmap shows planning for integration with industry-standard tools.

## 🔗 Repository & Contribution

The complete source code, build instructions, and issue tracker are available on GitHub:
[github.com/ForeverLX/ACLGuard-Active-Directory-Permission-Auditor](https://github.com/ForeverLX/ACLGuard-Active-Directory-Permission-Auditor)

Feedback and contributions are welcome. This is an active research project.
