[Vim](https://linuxcommand.org/lc3_man_pages/vim1.html) is a powerful text editor commonly used for writing code or editing text files on Linux systems. A significant benefit of using `Vim` is that it relies entirely on the keyboard, eliminating the need for a mouse. Once mastered, this significantly increases productivity and efficiency in writing and editing code.

`Vim` or its predecessor `Vi` is often found installed on compromised Linux systems, so learning how to use it allows editing files even on remote systems. `Vim` also boasts numerous features, including extensions and plugins, which greatly extend its capabilities and make it an excellent code editor.

## Basic Usage

To open a file with `Vim`, provide the filename as an argument:

```shell-session
Iskandeur@htb[/htb]$ vim /etc/hosts
```

![Parrot Terminal displaying a configuration file with network settings and comments.](https://academy.hackthebox.com/storage/modules/77/getting_started_vim_1.jpg)

To create a new file, simply input the desired filename, and `Vim` will open a new window for that file.

## Modes

When a file is opened, `Vim` starts in read-only **normal mode**, allowing navigation and reading.

To edit the file, press `i` to enter **insert mode**. This is indicated by `-- INSERT --` at the bottom of the `Vim` window. In this mode, you can move the cursor and modify the text:

![Parrot Terminal displaying a configuration file with network settings and comments.](https://academy.hackthebox.com/storage/modules/77/getting_started_vim_2.jpg)

To exit `insert mode` and return to `normal mode`, press the `Esc` key.

## Common Commands

While in `normal mode`, you can use various keys for shortcuts:

| Command | Description      |
| :------ | :--------------- |
| `x`     | Cut character    |
| `dw`    | Cut word         |
| `dd`    | Cut full line    |
| `yw`    | Copy word        |
| `yy`    | Copy full line   |
| `p`     | Paste            |

**Tip:** You can prepend a number to a command to repeat it. For example, `4yw` copies four words instead of one.

## Saving and Quitting

To save a file or quit `Vim`, press `:` while in `normal mode` to enter **command mode**. Commands typed will appear at the bottom of the Vim window:

![Parrot Terminal displaying a configuration file with network settings and comments.](https://academy.hackthebox.com/storage/modules/77/getting_started_vim_3.jpg)

Common commands include:

| Command | Description          |
| :------ | :------------------- |
| `:1`    | Go to line number 1. |
| `:w`    | Write (save) the file |
| `:q`    | Quit                 |
| `:q!`   | Quit without saving  |
| `:wq`   | Write and quit       |

`Vim` is a very powerful tool with many other commands and features. This [cheatsheet](https://vimsheet.com) is an excellent resource for further exploring `Vim`'s capabilities.

<!-- Do the vimtutor. -->