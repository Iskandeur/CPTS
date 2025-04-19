Understanding the differences between these assessment types is crucial for proper scoping and expectation setting during the [[Pre-Engagement Phase]].

## [[Vulnerability Assessment (VA)]]

- **Goal:** Identify and report vulnerabilities, often using automated scanning tools ([[OpenVAS]], [[Nessus]]). Little to no manual validation or exploitation.
- **Scope:** Typically broad (e.g., a range of IPs).
- **Depth:** Shallow; focuses on finding known vulnerabilities based on scanner databases.
- **Output:** List of vulnerabilities, often with [[CVSS]] scores.
- **Analogy:** A quick health checkup looking for common, known issues.

## [[Penetration Test]]

- **Goal:** Identify *and exploit* vulnerabilities within a defined scope to assess potential impact. Aims to uncover *all* vulnerabilities possible within scope and time constraints.
- **Scope:** Defined range of systems, applications, or networks.
- **Depth:** Deeper than VA; involves manual analysis, exploitation attempts, [[Post-Exploitation]], and potentially [[Lateral Movement]].
- **Output:** Detailed [[Reporting|Report]] including exploited vulnerabilities, impact assessment, evidence ([[Proof-of-Concept (PoC)]]), and remediation advice.
- **Analogy:** A more thorough medical examination, including tests to see if potential issues can actually cause harm.

## [[Red Teaming]]

- **Goal:** Achieve specific, predefined objectives (flags) by simulating a real-world adversary's [[TTPs]], often testing the organization's detection and response (Blue Team) capabilities. Focus is on achieving the objective, not necessarily finding *all* vulnerabilities.
- **Scope:** Can be very broad, potentially including [[Physical Security Assessment|Physical]] and [[Social Engineering]] aspects. Often objective-driven rather than system-list driven.
- **Depth:** Can be very deep but focused on the path to the objective. Emphasizes stealth ([[Evasive Testing]]) and bypassing defenses.
- **Output:** Report detailing success/failure in achieving objectives, adversary path taken, defense evasion techniques used, and assessment of Blue Team performance.
- **Analogy:** Simulating a specific disease progression or targeted attack to test the body's defenses and response mechanisms.

## [[Blue Team]]

- **Role:** The defenders within an organization.
- **Responsibilities:** Strengthening defenses, analyzing risks, implementing security policies, monitoring for threats ([[SIEM]], [[IDS]]/[[IPS]]), responding to incidents (DFIR), configuring and managing security tools.
- **Interaction:** The Blue Team is who the Red Team simulates attacks against, and who the Purple Team collaborates with.

**Key Distinction:** A pentest tries to find *many/all* holes; a red team assessment tries to achieve a *specific goal* through *any* available hole, often stealthily.

*Note: All three require proper authorization.* 