#new
[What are LOLBins ?][https://www-huntress-com.translate.goog/blog/detecting-malicious-use-of-lolbins?_x_tr_sl=en&_x_tr_tl=fr&_x_tr_hl=fr&_x_tr_pto=rq]

**LOLBin stands for "Living Off the Land Binaries," tools that are pre-installed as part of an operating system. LOLBins are not malicious in themselves but can be used maliciously by cyberattackers.**

>LOLBins are a significant threat to cybersecurity due to their inherent stealth and difficulty detecting malicious use. Since these tools are pre-installed and routinely used for legitimate purposes, security software may not flag their activity as suspicious. 

->A sneaky way hackers remain unnoticed.

## Examples

The biggest challenge with detecting LOLBin attacks is that they mimic regular system operations. Below are some examples of regular operations and how a LOLBin attack may mimic them. 

### 1. User Accounts and net.exe

On Windows endpoints, there are a number of ways to create user accounts. User accounts can be created and managed via [[Powershell]], [[WMI]], or the Local Users and Groups Manager.

Another means for creating user accounts involves the native utility, **net.exe**. Many administrators use this LOLBin to create, manage, and remove user accounts. Threat actors do so as well.

#### How to detect it ?

- Understand whether or not your administrators use the native utility as part of normal operations and workflow
- If not, that’s a clear indicator that a LOLBin is being used maliciously
- If you see **net.exe** being run with arguments such as  **user**, **localgroup**, or **add**, then you can likely assume that the use of the LOLBin is malicious in nature

If your organization does use **net.exe** to create user accounts, ask yourself these questions:

- Do you have specific administrators who use net.exe?
- Which [endpoint](https://www-huntress-com.translate.goog/defenders-handbooks/endpoint-detection-and-response?_x_tr_sl=en&_x_tr_tl=fr&_x_tr_hl=fr&_x_tr_pto=rq) do they usually access from?
- Is a specific account used to create and manage user accounts?
- Does this always happen from a specific system?

If so, any activity outside of those guardrails should be considered suspicious in nature and given a closer look.

### 2. cmd.exe and Explorer.exe

Another aspect regarding the use of native utilities is how those utilities are launched. One common means for doing so is for administrators to log into a system, open a command prompt, and type the command, or run the command from a batch file.

In this case, the process lineage has **cmd.exe** as the process parent and **Explorer.exe** (the Windows Explorer shell) as the process grandparent.

#### How To Detect It

Any observed command line where the process parent or grandparent is one of the following should be considered malicious:

- **wmiprvse.exe** (indicating that the command was run over a type 3 remote network connection)
- **PSExec.exe** (free Microsoft utility for privilege escalation)
- **sqlservr.exe** (MS SQL Server)