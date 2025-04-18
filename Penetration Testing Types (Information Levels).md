Defines the amount of information provided to the penetration testing team before the engagement begins. This is decided during the [[Pre-Engagement Phase]] and documented in the [[Scope of Work (SoW)]] / [[Rules of Engagement (RoE)]].

## Types

- **[[Black Box Testing]]**
    - **Information Provided:** Minimal. Often just the target organization's name, main domain, or IP ranges.
    - **Simulation:** An external attacker with no prior knowledge.
    - **Focus:** Relies heavily on [[Open-Source Intelligence (OSINT)]] and external scanning ([[Infrastructure Enumeration]], [[Service Enumeration]]) to discover the attack surface.
    - **Pros:** Most realistic simulation of an opportunistic external attacker.
    - **Cons:** Can be time-consuming; might miss internal vulnerabilities if the perimeter is strong; may spend significant time enumerating scope already known internally.

- **[[Grey Box Testing]]**
    - **Information Provided:** Partial/Extended. Testers receive some information beyond what's publicly available, such as specific target URLs, subnets, application user credentials (standard user), potentially limited architecture diagrams.
    - **Simulation:** An attacker with some insider knowledge or a user account (e.g., a standard employee, a customer with application access).
    - **Focus:** Blends external discovery with more targeted internal/authenticated testing.
    - **Pros:** More efficient than black box; allows deeper testing of specific applications or internal segments within the timeframe; simulates insider threats or post-phishing scenarios.
    - **Cons:** Less realistic simulation of a purely external attacker.

- **[[White Box Testing]]**
    - **Information Provided:** Maximum/Full. Testers receive extensive information, potentially including administrator credentials, source code, full network diagrams, configuration details.
    - **Simulation:** An attacker with significant insider knowledge (e.g., developer, administrator) or used for in-depth audits.
    - **Focus:** Comprehensive review of specific systems or applications with full knowledge. Often used for source code reviews, in-depth configuration audits, or testing specific security controls.
    - **Pros:** Most thorough and efficient for finding flaws in specific components; allows deep analysis.
    - **Cons:** Least realistic simulation of an external attacker; requires significant information sharing from the client.

## Relationship with Other Test Types

- These information levels can be applied to different assessment types like [[External Penetration Test]], [[Internal Penetration Test]], Web Application Tests, etc.
- [[Red Teaming]] often starts black box but may incorporate grey/white box elements depending on the scenario.
- [[Purple Teaming]] usually involves white box levels of information sharing to facilitate collaboration between attackers (Red Team) and defenders (Blue Team). 