A critical deliverable in the [[Penetration Testing Process]], finalized during the [[Post-Engagement Phase]].

## Purpose

- Communicate findings, impact, and remediation advice clearly to the client.
- Provide evidence for discovered vulnerabilities.
- Enable the client to understand their security posture and prioritize fixes.
- Serve as a formal record of the engagement.

## Preparation

- Ensure all necessary evidence (command output, screenshots, affected hosts lists) is collected *before* disconnecting from the client network after testing.
- Avoid including sensitive client data ([[PII]], etc.) in the report itself; reference findings without exposing raw data where possible.
- Compile findings during the test, not just at the end.

## Key Sections (Typical Structure)

- **Executive Summary:**
    - High-level overview for non-technical audience (management, executives).
    - Summarizes key findings, overall risk posture, and strategic recommendations.
    - Should be clear, concise, and impactful.
- **Methodology:**
    - Brief description of the approach and phases followed (linking to [[Penetration Testing Process]] phases).
- **Attack Chain / Narrative (If applicable):**
    - Detailed walkthrough of steps taken during a significant compromise (e.g., external-to-internal, domain compromise).
    - Shows how multiple vulnerabilities were combined.
    - Helps illustrate overall impact.
- **Detailed Findings:**
    - One section per vulnerability or finding.
    - **Title:** Clear and concise name.
    - **Risk Rating:** (e.g., Critical, High, Medium, Low, Info) based on impact and likelihood (see [[CVSS]] or custom methodology).
    - **Description:** What the vulnerability is.
    - **Impact:** What an attacker could achieve by exploiting it (specific to client environment).
    - **Affected Hosts/URLs/Parameters:** Clear scope of where the vulnerability exists.
    - **Evidence:** Screenshots, code snippets, command output proving the finding.
    - **Steps to Reproduce:** Clear, numbered steps allowing the client to validate the finding.
    - **Remediation Recommendations:** Actionable advice on how to fix the vulnerability.
    - **References:** Links to [[CVE]] details, [[OWASP]], vendor advisories, best practice guides.
- **Recommendations (Strategic):**
    - Broader advice based on observed patterns.
    - Prioritized near, medium, and long-term actions.
    - Example: Implementing better [[Password Policy]], network segmentation, vulnerability management program.
- **Appendices:**
    - **Scope:** Target list (IPs, URLs).
    - **[[OSINT]] Data:** (If relevant and permitted).
    - **Password Cracking Analysis:** (If relevant).
    - **Discovered Ports/Services:** List of open ports found.
    - **Compromised Hosts/Accounts:** List of systems/accounts successfully accessed.
    - **Tester Artifacts:** Files transferred, accounts created, modifications made (important for [[Cleanup]] correlation).
    - **[[Active Directory]] Security Analysis:** (If performed).
    - **Relevant Scan Data:** Supporting output from tools.
    - **Other Supplementary Info:** Anything needed to clarify findings.

## Process

1.  **Drafting:** Compile findings and evidence into a draft report.
2.  **Internal Review:** Peer review by other testers/seniors.
3.  **Deliver Draft:** Send draft to client for review.
4.  **[[Report Review Meeting]]:** Discuss findings with client, answer questions, clarify issues.
5.  **Finalization:** Incorporate client feedback (factual corrections).
6.  **[[Deliverable Acceptance]]:** Client formally accepts the final report.

See also: [[Report Review Meeting]], [[Deliverable Acceptance]], [[Role of Pentester in Remediation]] 