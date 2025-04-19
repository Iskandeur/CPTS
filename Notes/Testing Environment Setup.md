Setting up a reliable and secure environment is crucial for penetration testing.

## Attack Machine Setup

Penetration testers need dedicated attack machines, typically running Linux, separate from their primary OS.

### Methods

- **Virtualization (Recommended):** Using a [[Hypervisor]] (e.g., VMware Workstation/Fusion, VirtualBox, KVM, Parallels) to run a pentest distribution as a Virtual Machine (VM).
    - **Pros:** Isolation, snapshots for reverting changes, easy to create fresh VMs per engagement, portability.
    - **Cons:** Requires host machine resources (RAM, CPU, Disk).
- **Dual Booting:** Installing a pentest distro alongside the main OS.
    - **Pros:** Full hardware access (no virtualization overhead).
    - **Cons:** Time-consuming to switch OS, potential partitioning risks, harder isolation.
- **Bare Metal Install:** Using the pentest distro as the primary OS.
    - **Pros:** Full hardware access.
    - **Cons:** Not recommended due to lack of isolation and potential security risks from running testing tools on the main machine.

### [[Hypervisor]]

Software that creates and runs VMs (e.g., VMware, VirtualBox). Comfort with using hypervisors is essential for technical infosec roles.

### [[Pentest Distro]]

Linux distributions pre-loaded with security tools (e.g., [[Kali Linux]], [[Parrot OS]]). No single distro has *all* tools; customization is common.
- **[[Parrot OS]]:** Used for [[Pwnbox]] in HTB Academy.
- **Fresh VM per Engagement:** **CRITICAL BEST PRACTICE.** Always start a new assessment with a freshly installed VM to prevent accidental data leakage between clients and ensure a clean slate.
    - Requires efficient setup processes (automation, scripts, documented procedures).

### Installation Media

- **[[ISO]] Image:** A bootable image file (like a virtual CD-ROM) used to install the OS manually within the hypervisor. Allows for customization during setup (keyboard, locale, partitioning).
- **[[OVA]] (Open Virtualization Appliance):** A pre-built VM package containing the virtual disk ([[VMDK]]) and configuration ([[OVF]]). Faster deployment but less customization during initial setup.

### [[Pwnbox]]

- HTB Academy's in-browser instance of [[Parrot OS]].
- Useful for completing module exercises without local virtualization setup.
- Access to Docker targets doesn't require VPN; access to specific hosts (e.g., AD labs) may require [[VPN (Virtual Private Network)|VPN]] if not using Pwnbox. 