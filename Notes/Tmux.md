<!-- *I used it for the pentest module with Synacktiv.* -->

## Overview

![[_assets/images/simple-tmux-cheatsheet.jpg]]

Terminal multiplexers, like `tmux` or `Screen`, are valuable utilities that enhance standard Linux terminals by adding features like multiple windows within a single terminal and the ability to switch between them.

This note covers some basics of using `tmux`, which is generally more common than `Screen`.

## Installation

If `tmux` is not present on your Linux system, you can usually install it using your package manager. For Debian/Ubuntu-based systems:

```shell-session
Iskandeur@htb[/htb]$ sudo apt install tmux -y
```

## Basic Usage

Once installed, start `tmux` by simply typing the command:

```shell
tmux
```
![Parrot Terminal with user prompt showing command 'tmux'.](https://academy.hackthebox.com/storage/modules/77/getting_started_tmux_1.jpg)

## Commands

The default key prefix for `tmux` commands is `Ctrl+b`.

### Windows

*   **New Window:** Press `Ctrl+b`, then `c`.
    ![Parrot Terminal with user prompt ready for input.](https://academy.hackthebox.com/storage/modules/77/getting_started_tmux_2.jpg)
    Numbered windows are displayed at the bottom.
*   **Switch Window:** Press `Ctrl+b`, then the window number (e.g., `0`, `1`).

### Panes

*   **Split Vertically:** Press `Ctrl+b`, then `%` (Shift + 5).
    ![Parrot Terminal with two panes, each showing user prompts ready for input.](https://academy.hackthebox.com/storage/modules/77/getting_started_tmux_3.jpg)
*   **Split Horizontally:** Press `Ctrl+b`, then `"` (Shift + ').
    ![Parrot Terminal with two panes, each showing user prompts ready for input.](https://academy.hackthebox.com/storage/modules/77/getting_started_tmux_4.jpg)
*   **Switch Panes:** Press `Ctrl+b`, then use the arrow keys (`←`, `→`, `↑`, `↓`).

## Further Resources

The commands above cover basic `tmux` usage. It is a powerful tool with many applications, including session persistence and logging, which are crucial during technical engagements.

*   **Cheatsheet:** [tmuxcheatsheet.com](https://tmuxcheatsheet.com)
*   **Video Introduction:** [Introduction to tmux](https://www.youtube.com/watch?v=Lqehvpe_djs) by Ippsec.

