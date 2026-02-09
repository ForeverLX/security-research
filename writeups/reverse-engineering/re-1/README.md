# StackSmash — re-1 (Byte-wise Validation)

## Metadata
- **Challenge:** re-1
- **Platform:** StackSmash
- **Category:** Re
- **Difficulty:** Beginner
- **Date:** 2026-01-18
- **Time Spent:** ~20–30 minutes
- **Tools:** file, strings, gdb, python3, echo

## TL;DR
- Quick recon (`file`, `strings`) reveals a success message (`correct!`) and a source reference (`simple.c`), pointing to straightforward local validation.
- Disassembly shows a byte-by-byte comparison loop against hardcoded values.
- Converting the extracted bytes (hex → ASCII) yields the required input (redacted), which prints `correct!`.

## Objective
Reverse engineer the `re-1` binary to determine the exact input that triggers the `correct!` success message.

## Scope / Constraints
- **Binary type:** ELF 32-bit (x86), PIE, not stripped
- **Validation style:** character-by-character compare against embedded bytes
- **Assumptions:** local execution, no remote component
- **Redaction:** the final derived input is intentionally omitted from this writeup

## Recon
Initial reconnaissance steps:
```bash
    file re-1
    strings re-1 | grep -E "(correct|flag|simple)"
```
Key observations:
- The binary contains a clear success string: `correct!`
- A source reference like `simple.c` appears in the strings output, suggesting a simple validation routine rather than heavy obfuscation.

## Analysis
Disassembly of `main` showed a deterministic validation loop:

- Read user input
- Iterate over each position `i`
- Compare `input[i]` to a hardcoded expected byte sequence
- If any mismatch occurs → fail path
- If all bytes match → print `correct!`

Commands used:
```bash
    gdb -q ./re-1
    (gdb) disassemble main
```
GDB’s `disassemble` command is a fast way to inspect compiled validation logic. ([sourceware.org](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Machine-Code.html?utm_source=chatgpt.com))

The expected bytes were recovered from the comparison logic as hexadecimal constants. Converting those hex values to ASCII reconstructs the required input.

## Solution
Minimal local conversion (expected bytes and output redacted):
```python
    python3 - << 'PY'
    # Redacted: byte sequence recovered from disassembly.
    hex_values = [
        # 0x??, 0x??, ...
    ]

    derived = ''.join(chr(b) for b in hex_values)
    print(derived)  # <REDACTED_INPUT>
    PY
```
## Outcome / Validation
Provide the derived input to the program (redacted) and confirm the success message:
```bash
    echo -n "<REDACTED_INPUT>" | ./re-1
```

Observed result:
- Program prints: `correct!`

## Key takeaways
- “Not stripped” binaries can leak high-signal artifacts that speed up analysis (strings, symbols, clearer disassembly).
- Byte-wise compare loops are a common beginner RE pattern: extract constants → decode → validate.
- Always validate recovered input by executing the binary, not just static reasoning.

## Defensive notes
Client-side secret checks are inherently recoverable through disassembly. Common hardening steps include:
- **Strip symbols** in release builds (e.g., `strip --strip-all`) to reduce leaked metadata and make analysis slower. ([sourceware.org](https://www.sourceware.org/binutils/docs/binutils/))
- Avoid shipping secrets in a client binary; prefer server-side verification when applicable.

## References
- GDB machine-code inspection / `disassemble`. ([sourceware.org](https://sourceware.org/gdb/current/onlinedocs/gdb.html/))
- GNU `strip` documentation. ([sourceware.org](https://www.sourceware.org/binutils/docs/binutils/))
