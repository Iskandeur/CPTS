A technique/consideration applicable throughout various [[Penetration Testing]] phases, especially [[Exploitation]], [[Post-Exploitation]], and [[Lateral Movement]].

Defined in the [[Pre-Engagement Phase]] and documented in the [[Rules of Engagement (RoE)]].

## Goal

- Avoid detection by security monitoring systems ([[SIEM]], [[IDS]]/[[IPS]]) and personnel (Blue Team, SOC).
- Bypass security controls ([[Antivirus (AV)]], [[Endpoint Detection and Response (EDR)], [[WAF]]).
- Mimic the stealthy techniques of real-world adversaries.

## When is it Used?

- Explicitly requested by the client (specified in [[Rules of Engagement (RoE)]]).
- Required to achieve specific objectives that would otherwise be blocked by defenses.
- To test the effectiveness of the client's detection and response capabilities.

## Levels/Approaches

*(As defined during scoping)*

- **Fully Evasive:** Maximum effort to remain undetected throughout the engagement.
- **Hybrid-Evasive:** Start quiet, gradually become "louder" to assess detection thresholds. May focus evasion on specific systems or phases.
- **Non-Evasive:** No specific attempt to avoid detection. Focus is on finding vulnerabilities regardless of noise generated. (Security controls might still block actions).

*Note: Even in a non-evasive test, some level of stealth might be necessary initially to gain a foothold.* 

## Techniques

*(Placeholder: Specific techniques can be added, e.g., payload obfuscation, C2 tunneling, living-off-the-land binaries (LOLBins), timing attacks, modifying/disabling logging, memory injection, etc.)*

## Impact of Detection

If detected during evasive testing:
- **For the Pentester:** May lose access (host quarantined, account disabled), potential end of that attack path. Provides learning opportunity on detection mechanisms.
- **For the Client:** Validates effectiveness of certain defenses. Highlights where detection occurred.
- **Reporting:** Even if detected, the full potential attack chain should be documented to show impact and identify gaps where detection *didn't* occur earlier.

## Considerations

- Requires deep understanding of target environment defenses.
- Often involves more complex [[Exploit Development]] and payload crafting.
- Slower and more methodical approach than non-evasive testing.
- Running common recon/exploit commands (e.g., `net user`, `whoami`, Mimikatz) without obfuscation is likely to trigger alerts in mature environments. 