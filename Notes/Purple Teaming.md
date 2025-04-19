A collaborative approach to security testing, distinct from traditional [[Penetration Test vs Red Team vs VA|Penetration Testing or Red Teaming]].

## Concept

Involves the attacking team (**Red Team**) working closely and openly with the defending team (**Blue Team**) during the assessment.

## Goal

- Improve detection and response capabilities by providing immediate feedback.
- Validate effectiveness of security controls ([[SIEM]] rules, [[Endpoint Detection and Response (EDR)|EDR]] alerts, [[IDS]]/[[IPS]] signatures) against specific attacks.
- Enhance Blue Team skills by observing Red Team techniques ([[TTPs]]).
- Foster collaboration and knowledge sharing between offensive and defensive security functions.
- Tune security tools based on observed gaps.

## Process

- Often follows predefined scenarios or attack paths.
- Red Team executes an attack technique.
- Blue Team attempts to detect and respond.
- Both teams communicate openly about:
    - What the Red Team did.
    - What the Blue Team saw (or didn't see).
    - Why detection failed or succeeded.
    - How detection rules or processes can be improved.
- Iterate through multiple techniques and scenarios.

## Information Level

Typically operates under **[[White Box Testing]]** conditions, with full information sharing between teams.

## Contrast with Red Teaming

- [[Red Teaming]] focuses on stealth and bypassing defenses to achieve an objective, testing the *current* state of detection/response.
- Purple Teaming focuses on *collaboration* to actively *improve* detection/response during the exercise.

## Benefits

- Faster feedback loop for improving defenses.
- Direct validation of security tool configurations.
- Excellent training opportunity for Blue Team members.
- Builds better understanding and communication between offensive and defensive teams. 