A key objective within the [[Post-Exploitation]] phase.

Involves establishing a method to maintain access to a compromised system or network across reboots, credential changes, or other disruptions.

## Goal

- Ensure continued access for the duration of the [[Penetration Test]] (or as long as needed to achieve objectives).
- Survive system restarts or user logouts.
- Potentially regain access if initial exploit method is remediated or detected.

## Timing

Often performed *early* in the [[Post-Exploitation]] phase, sometimes even before extensive [[Information Gathering]] or [[Pillaging]], to secure the foothold.

## Techniques (Examples)

*(Specific techniques depend heavily on OS and privileges, sometimes leveraging [[LOLBin]]s)*

- **Windows:**
    - Registry Run Keys (`HKCU\Software\Microsoft\Windows\CurrentVersion\Run`)
    - Scheduled Tasks (`schtasks`)
    - Startup Folders
    - Service Creation (`sc create`)
    - [[WMI]] Event Subscriptions
    - DLL Hijacking
    - Modifying Shortcuts (.lnk files)
- **Linux:**
    - Cron Jobs (`crontab`)
    - `~/.bashrc`, `~/.profile` modifications
    - Systemd Services
    - `rc.local`
    - Private Keys (`id_rsa`, `id_ed25519`, etc.)
    - Public Keys (`id_rsa.pub`, etc.)
    - Known Hosts (`known_hosts`)
    - [[SSH]] Authorized Keys (`authorized_keys`)
    - SSH Config (`config`)
    - Modifying system binaries (less common/stealthy)
- **Web Applications:**
    - Web Shells
    - Backdoored plugins/themes
    - Database triggers

## Considerations

- **Stealth:** Persistence mechanisms are often targets for detection by [[Antivirus (AV)]] and [[Endpoint Detection and Response (EDR)]. Choose methods appropriate for the [[Evasive Testing]] requirements.
- **Privileges:** Many persistence techniques require elevated privileges.
- **Cleanup:** Remember to remove persistence mechanisms at the end of the engagement as per the [[Rules of Engagement (RoE)]], unless instructed otherwise for demonstration purposes.
- **Flexibility:** Be prepared to adapt techniques based on the environment and defenses encountered. 