The Nmap Scripting Engine (NSE) is one of `[[Nmap]]`'s most powerful and flexible features. It allows users to write (and share) simple scripts (using the `[[Lua]]` programming language) to automate a wide variety of networking tasks.

These scripts can perform tasks such as:

*   More advanced [[Service Enumeration]] and [[Network Discovery]]
*   [[Vulnerability Scanning]] and detection
*   Backdoor detection
*   Vulnerability exploitation (though less common than dedicated exploit frameworks)

## Usage

NSE scripts are typically run using the `-sC` option (which runs scripts in the `default` category) or the `--script` option.

*   **Run Default Scripts:**
    ```bash
    nmap -sC <target>
    ```
*   **Run Specific Script(s):**
    ```bash
    nmap --script <script-name>.nse <target>
    nmap --script <script1>,<script2> <target> 
    ```
*   **Run Scripts by Category:**
    ```bash
    nmap --script <category> <target>
    # Example: Run vulnerability detection scripts
    nmap --script vuln <target>
    ```
*   **Run Multiple Categories/Scripts:**
    ```bash
    nmap --script "default,safe" <target>
    nmap --script "smb-* and not smb-brute" <target>
    ```

## Script Categories

NSE scripts are grouped into categories for easier selection:

*   `auth`: Scripts dealing with authentication credentials.
*   `broadcast`: Scripts that use broadcast packets for discovery.
*   `brute`: Scripts for brute-force password guessing.
*   `default`: Default scripts run with `-sC`. Considered relatively safe.
*   `discovery`: Scripts involved in discovering network information.
*   `dos`: Scripts that may cause denial-of-service.
*   `exploit`: Scripts that attempt to exploit vulnerabilities.
*   `external`: Scripts that interact with third-party services.
*   `fuzzer`: Scripts designed for fuzz testing.
*   `intrusive`: Scripts considered intrusive and likely to crash targets or generate excessive network noise. Not run by default.
*   `malware`: Scripts that check for malware infections.
*   `safe`: Scripts considered generally safe and non-intrusive.
*   `version`: Special scripts used by the `-sV` version detection engine.
*   `vuln`: Scripts specifically checking for known vulnerabilities.

Scripts can belong to multiple categories. 
