The structured approach followed during a [[Penetration Test]]. It involves a directed sequence of steps and events performed by the tester to find vulnerabilities and achieve defined objectives.

While phases can sometimes overlap or require iteration (especially between [[Information Gathering]] and [[Vulnerability Assessment]]), understanding the general flow is crucial.

## Standard Stages

*(Based on common methodologies like PTES, NIST, OSSTMM, and the CPTS material)*

1.  **[[Pre-Engagement Phase]]**
    *   Defining scope, goals, rules ([[Rules of Engagement (RoE)]]).
    *   Contracts, NDAs ([[Non-Disclosure Agreement (NDA)]]).
    -   Initial meetings ([[Pre-Engagement Meeting]], [[Kick-Off Meeting]]).
2.  **[[Information Gathering]]**
    *   Collecting data about the target (Passive: [[Open-Source Intelligence (OSINT)]]; Active: [[Infrastructure Enumeration]], [[Service Enumeration]], [[Host Enumeration]]).
    *   *Often revisited throughout the test.*
3.  **[[Vulnerability Assessment]]**
    *   Analyzing gathered information to identify potential weaknesses ([[Vulnerability Research]], [[Analysis Types]]).
    *   *Iterates closely with Information Gathering.*
4.  **[[Exploitation]]**
    *   Actively attempting to leverage vulnerabilities to gain access ([[Exploit Development]], [[Exploit Prioritization]]).
5.  **[[Post-Exploitation]]**
    *   Actions taken after gaining initial access: [[Pillaging]], [[Privilege Escalation]], [[Persistence]], internal [[Information Gathering]]/[[Vulnerability Assessment]].
6.  **[[Lateral Movement]]**
    *   Expanding access from compromised systems to other internal systems ([[Pivoting]]).
    *   Often involves repeating steps 2-5 from an internal perspective.
7.  **[[Reporting]] / [[Proof-of-Concept (PoC)]] Documentation**
    *   Documenting findings, impact, evidence, and remediation steps.
    *   Creating clear PoCs for validation.
8.  **[[Post-Engagement Phase]]**
    *   [[Cleanup]], [[Report Review Meeting]], [[Deliverable Acceptance]], [[Post-Remediation Testing]], [[Data Retention]], [[Project Close Out]].

## Process Nature

- **Deterministic elements:** One state often depends on previous states (e.g., exploitation depends on vulnerability assessment).
- **Stochastic elements:** Success is often probabilistic; iteration and adapting the approach are key.

*Refer to the individual linked notes for detailed descriptions of each phase and activity.* 