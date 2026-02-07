# Web Security Writeups

This section documents hands-on, authorized web exploitation work with a focus on repeatable methodology, clean evidence, and clear remediation notes.

## How I work (methodology)
1) Identify the input surface (params, headers, cookies, body)
2) Prove control with a minimal payload (lowest-noise confirmation)
3) Escalate impact safely (file read → auth bypass → RCE where applicable)
4) Capture evidence (request/response, key output, and a short explanation)
5) Write the fix (what to change, not just what went wrong)

## Navigation
- **Injection Attacks** → `./injection-attacks/`
- **Authentication & Session** → `./authentication-and-session/`
- **IDOR / Access Control** → `./idor/`
- **SSRF** → `./ssrf/`
- **SSTI** → `./ssti/`
- **XSS** → `./xss/`
- **XXE** → `./xxe/`

## Notes
- All targets are lab environments or explicitly authorized scenarios.
- Sensitive values (tokens, creds, real IPs) are sanitized.
