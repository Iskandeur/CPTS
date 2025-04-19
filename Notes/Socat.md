## Overview

[Socat](https://linux.die.net/man/1/socat) is a versatile network utility, often considered a more powerful alternative or complement to [[Netcat]].

## Key Features

`Socat` includes several features not found in traditional `netcat`, such as:

*   **Advanced Port Forwarding:** More complex relaying and forwarding capabilities.
*   **Device Connectivity:** Ability to connect to serial devices and other types of addresses.
*   **TTY Upgrade:** Can be used to [upgrade simple reverse shells to fully interactive TTYs](https://blog.ropnop.com/upgrading-simple-shells-to-fully-interactive-ttys/#method-2-using-socat), which is a common technique in penetration testing (examples will be shown in relevant sections).

## Use in Penetration Testing

`Socat` is a valuable tool for penetration testers.

*   **Stable Shells:** A [statically compiled binary](https://github.com/andrew-d/static-binaries) of `socat` can often be transferred to a compromised system after gaining initial remote code execution (RCE) to establish a more stable and feature-rich reverse or bind shell compared to basic shells.
*   **Relaying Traffic:** Useful for pivoting and tunneling traffic within networks.

Due to its power and flexibility, `socat` should be part of every penetration tester's toolkit.
