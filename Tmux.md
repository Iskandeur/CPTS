#new 
*I used it for the pentest module with Synacktiv.*

![[simple-tmux-cheatsheet.jpg]]

Terminal multiplexers, like `tmux` or `Screen`, are great utilities for expanding a standard Linux terminal's features, like having multiple windows within one terminal and jumping between them. Let's see some examples of using `tmux`, which is the more common of the two. If `tmux` is not present on our Linux system, we can install it with the following command:

```shell-session
Iskandeur@htb[/htb]$ sudo apt install tmux -y
```

Once we have `tmux`, we can start it by entering `tmux` as our command: ![Parrot Terminal with user prompt showing command 'tmux'.](https://academy.hackthebox.com/storage/modules/77/getting_started_tmux_1.jpg)

The default key to input `tmux` commands prefix is `[CTRL + B]`. In order to open a new window in `tmux`, we can hit the prefix 'i.e. `[CTRL + B]`' and then hit `C`: ![Parrot Terminal with user prompt ready for input.](https://academy.hackthebox.com/storage/modules/77/getting_started_tmux_2.jpg)

We see the numbered windows at the bottom.

We can switch to each window by hitting the prefix and then inputting the window number, like `0` or `1`. We can also split a window vertically into panes by hitting the prefix and then `[SHIFT + %]`: ![Parrot Terminal with two panes, each showing user prompts ready for input.](https://academy.hackthebox.com/storage/modules/77/getting_started_tmux_3.jpg)

We can also split into horizontal panes by hitting the prefix and then `[SHIFT + "]`: ![Parrot Terminal with two panes, each showing user prompts ready for input.](https://academy.hackthebox.com/storage/modules/77/getting_started_tmux_4.jpg)

We can switch between panes by hitting the prefix and then the `left` or `right` arrows for horizontal switching or the `up` or `down` arrows for vertical switching. The commands above cover some basic `tmux` usage. It is a powerful tool and can be used for many things, including logging, which is very important during any technical engagement. This [cheatsheet](https://tmuxcheatsheet.com) is a very handy reference. Also, this [Introduction to tmux](https://www.youtube.com/watch?v=Lqehvpe_djs) video by `ippsec` is worth your time.

