Alias: [[PoC]]

A demonstration, often in the form of code or a sequence of steps, that shows a vulnerability ([[CVE]]) is exploitable.

## Purpose

- Proves that a theoretical vulnerability can be practically leveraged.
- Helps understand the mechanism of the vulnerability.
- Provides a starting point for developing a working exploit.

## Usage in Pentesting

- Found during [[Vulnerability Research]] in databases like [[Exploit DB]] or on platforms like GitHub.
- Analyzed using `Diagnostic Analysis` ([[Analysis Types]]) to understand how it works.
- **Adaptation is usually required:** Public PoCs are often tailored to specific environments and rarely work perfectly against a real target without modification.
- Used as a basis for the [[Exploitation]] phase.
- The final successful attack chain serves as a PoC in the [[Reporting]] phase to demonstrate impact to the client.

## Considerations

- Running untrusted PoC code directly against a target or your own system is risky.
- Test PoCs in isolated, controlled environments (e.g., a mirrored lab setup).
- Understand the PoC code before running it. 