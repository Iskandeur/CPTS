A consideration during the [[Post-Engagement Phase]] regarding the handling of client data collected during the [[Penetration Test]].

## The Challenge

Pentesters often collect significant amounts of client data (scan results, configuration details, potentially sensitive information found during [[Pillaging]]). Securely managing and eventually disposing of this data is crucial.

## Best Practices & Recommendations

- **Retain Evidence (Temporarily):** Keep evidence supporting findings for a reasonable period after the engagement.
    - **Purpose:** To answer client questions, assist with [[Post-Remediation Testing]], or address disputes.
    - **Duration:** Varies based on firm policy, contractual agreements, and legal/regulatory requirements (e.g., [[PCI DSS]] doesn't mandate specific retention periods for testers but recommends retaining evidence).
- **Secure Storage:** Any retained data **must** be stored securely:
    - In a location owned and controlled by the testing firm.
    - **Encrypted at rest.**
- **Wipe Tester Systems:** All client data should be wiped from individual tester workstations/VMs at the conclusion of the assessment.
- **Client-Specific VMs:** Use dedicated VMs per client. Destroy or securely wipe these VMs after the engagement and necessary retention period.
- **New VMs for Retesting:** Create a *new*, clean VM for any [[Post-Remediation Testing]] or follow-up investigation, rather than reusing the original assessment VM.
- **Check RoE:** The [[Rules of Engagement (RoE)]] or [[Contract]] may specify data handling and retention requirements.
- **Local/Regional Laws:** Be aware of any applicable data privacy laws.

## Availability

Retained evidence should be available upon request from the client or other authorized entities (as defined in the [[Rules of Engagement (RoE)]]). 