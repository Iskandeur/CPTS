Alias: [[Retesting]]

Part of the [[Post-Engagement Phase]], often included in the initial [[Scope of Work (SoW)]].

Process of verifying that vulnerabilities identified during the main [[Penetration Test]] have been successfully fixed by the client.

## Purpose

- Confirm the effectiveness of remediation efforts.
- Provide assurance to the client that reported issues are resolved.
- Update the security posture assessment.

## Process

1.  **Client Provides Evidence:** Client notifies tester which findings they believe are remediated, potentially providing documentation or descriptions of fixes.
2.  **Tester Re-Accesses Environment:** Gain access to the target environment again (may require new credentials or access methods).
3.  **Test Each Claimed Remediation:** Attempt the original exploitation techniques or validation steps documented in the [[Reporting|Report]] for each finding the client claims to have fixed.
4.  **Document Results:** Record whether each tested finding is truly `Remediated` or `Not Remediated`.
5.  **Issue Post-Remediation Report:** Deliver a separate report summarizing the retesting results.

## Post-Remediation Report

- Clearly shows the state *before* and *after* remediation.
- Often includes a table summarizing the status of each finding tested:

    | # | Finding Severity | Finding Title                          | Original Status | Retest Status  |
    | :- | :--------------- | :------------------------------------- | :-------------- | :------------- |
    | 1 | High             | SQL Injection                          | Vulnerable      | Remediated     |
    | 2 | High             | Broken Authentication                  | Vulnerable      | Remediated     |
    | 3 | High             | Unrestricted File Upload               | Vulnerable      | Remediated     |
    | 4 | High             | Inadequate Web and Egress Filtering    | Vulnerable      | Not Remediated |
    | 5 | Medium           | SMB Signing Not Enabled                | Vulnerable      | Not Remediated |
    | 6 | Low              | Directory Listing Enabled              | Vulnerable      | Not Remediated |

- Includes evidence (scan output, failed exploit attempts) confirming remediation where possible.

See also: [[Role of Pentester in Remediation]] 