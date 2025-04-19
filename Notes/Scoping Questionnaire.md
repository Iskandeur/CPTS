Part of the [[Pre-Engagement Phase]].

After initial contact, send it to the client to better understand the services they are seeking. Should clearly explain our services.

## Purpose

- Define the scope and objectives of the assessment.
- Understand client requirements and expectations.
- Identify potential constraints or sensitivities.
- Gather information needed for the [[Penetration Testing Proposal]].

## Common Sections/Questions

### Assessment Type Selection

May typically ask them to choose one or more from this list:

- [[Internal Vulnerability Assessment]]
- [[External Vulnerability Assessment]]
- [[Internal Penetration Test]]
- [[External Penetration Test]]
- [[Wireless Security Assessment]]
- [[Application Security Assessment]]
- [[Physical Security Assessment]]
- [[Social Engineering Assessment]]
- [[Red Team Assessment]]
- [[Web Application Security Assessment]]

Each choice needs sub-choices, allowing the client to be more specific.

> Do they need a web application or mobile application assessment? Secure code review? Should the Internal Penetration Test be black box and semi-evasive? Do they want just a phishing assessment as part of the Social Engineering Assessment or also vishing calls?

This is our chance to explain the depth of our services.

### Critical Information

Aside from the assessment type, client name, address, and key personnel contact information, some other critical pieces of information include:

- How many expected live hosts?
- How many IPs/CIDR ranges in scope?
- How many Domains/Subdomains are in scope?
- How many wireless SSIDs in scope?
- How many web/mobile applications? If testing is authenticated, how many roles (standard user, admin, etc.)?
- For a phishing assessment, how many users will be targeted? Will the client provide a list, or we will be required to gather this list via [[OSINT]]?
- If the client is requesting a [[Physical Security Assessment]], how many locations? If multiple sites are in-scope, are they geographically dispersed?
- What is the objective of the [[Red Team Assessment]]? Are any activities (such as phishing or physical security attacks) out of scope?
- Is a separate [[Active Directory Security Assessment]] desired?
- Will network testing be conducted from an anonymous user on the network or a standard domain user?
- Do we need to bypass [[Network Access Control (NAC)]]?

### Other Considerations

- **[[Disclosure Levels]]**: Is the Penetration Test black box (no information provided), grey box (only IP address/CIDR ranges/URLs provided), white box (detailed information provided)?
- **[[Evasiveness Levels]]**: Would they like us to test from a non-evasive, hybrid-evasive (start quiet and gradually become "louder" to assess at what level the client's security personnel detect our activities), or fully evasive.

## Outcome

All this info will help us to make an accurate project timeline proposal.
We sum-up everything into the [[Scoping Document]]. 