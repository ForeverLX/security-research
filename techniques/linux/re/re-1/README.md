# StackSmash CTF — re-1 Reverse Engineering

## Metadata
- **Challenge:** re-1
- **Platform:** StackSmash
- **Category:** Reverse Engineering
- **Difficulty:** Beginner
- **Architecture:** ELF 32-bit (x86)
- **Protections:** PIE, not stripped
- **Date:** 2026-01-05
- **Time Spent:** ~__ minutes
- **Tools:** file, strings, gdb, (planned) Binary Ninja

---

## Objective
Identify the validation logic in the binary and determine the input that triggers the success condition (prints `correct!` / reveals the flag).

---

## Recon

### File information
```bash
file ./re-1
ls -lh ./re-1
Notable traits:

32-bit PIE ELF

not stripped (symbols present)

interactive behavior (reads stdin)

Runtime behavior
When executed, the program blocks waiting for input. After providing input, it returns to the host prompt without printing an obvious error message. This suggests early-exit validation logic (fail-fast without verbose errors).

Current Status
This writeup currently captures early reconnaissance and investigation notes. Once the full solution/validation steps are documented, the Analysis and Outcome/Validation sections will be expanded.

Analysis (WIP)
Planned analysis path:

Identify main and input-handling functions

Locate the “win condition” branch leading to correct!

Determine what is compared/validated (string compare, byte checks, arithmetic transform, etc.)

Reconstruct the expected input and verify locally

Outcome / Validation (WIP)
To finalize:

Record the exact input used

Show the local success output (correct! and/or flag)

Confirm the same input works against the remote challenge (if applicable)

Key Takeaways (so far)
Silent termination after input can indicate early mismatch exits without error paths.

“Not stripped” binaries reduce friction: symbols and strings often provide quick anchors (main, libc calls, success text).

Appendix — Early Notes (raw log)
These were my initial observations before deeper analysis:

File info: re-1: ELF 32-bit LSB pie executable ... not stripped

Size: ~15 KB

Observed behavior: blocks on input; exits immediately after input is provided

Interesting strings: correct!, main, simple.c, puts, printf

Open questions at the time: what is checked / where is the win condition

Next steps planned: open in Binary Ninja; locate main; analyze logic
