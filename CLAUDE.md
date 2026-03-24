# security-research — Repo-Level Claude Code Context

## Purpose
Flagship research repository. Container boundary weaknesses is the active research track.
Every research effort produces multiple outputs: GitHub writeup, conference talk, YouTube, research brief.

## Key Paths
- Container boundary research: `security-research/research/container-boundaries/`
- Certificates: `security-research/assets/certificates/`

## Active Research
- **Flagship:** Container boundary weaknesses
  - Real infrastructure (Veil mesh, Podman rootless Quadlets on Cerberus)
  - Connects RE to infra — differentiating angle
  - Status: research question not yet locked

## Rules
- Use vuln-analyst agent for analysis tasks — read-only
- Use research-writer agent for writeup and content tasks
- Use router-escalation for architectural research reasoning
- Write-first rule applies to any code written as part of research
- No speculative findings — everything must be reproducible on real infrastructure
- Prior work must be cited before any novel claims

## Output Standard
Each research finding should produce:
1. GitHub writeup in this repo
2. Conference talk abstract (target: HackSpaceCon May 2026)
3. YouTube / research brief
4. azraelsec.dev /research page entry
