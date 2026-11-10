# Linux Commands

A quick reference to common Linux commands. Detailed examples are organized into separate topic files.

## Navigation and File Management

| Command | Description |
|---|---|
| `ls` | Lists directory contents |
| `ls -l` | Displays a long listing with permissions, ownership, size, and timestamps |
| `ls -la` | Long listing including hidden entries |
| `cd` | Changes to the user's home directory when used without arguments |
| `cd -` | Returns to the previous working directory |
| `cd ..` | Moves to the parent directory |
| `pwd` | Prints the current working directory |
| `mkdir` | Creates directories |
| `touch` | Updates timestamps, or creates an empty file if absent |
| `cp` | Copies files and directories (use `-r` for directories) |
| `mv` | Moves or renames files and directories |
| `file` | Identifies a file's type |
| `find` | Searches filesystem trees using conditions |
| `locate` | Searches a prebuilt filename database, if installed |
| `which` | Shows the executable found on the command search path |
| `tree` | Displays a directory hierarchy, if installed |

See [File and Directory Management](File%20and%20Directory%20Management.md).

## Documentation and Help

| Command | Description |
|---|---|
| `man ls` | Opens the manual for `ls` |
| `ls --help` | Displays help when the command supports this option |
| `apropos network` | Searches manual-page descriptions for a keyword |

Not every command supports `-h` or `--help`.

```bash
man grep
apropos password
ls --help
```

## User and System Information

| Command | Description |
|---|---|
| `whoami` | Prints the effective username |
| `id` | Shows user and group IDs |
| `who` | Lists logged-in sessions |
| `hostname` | Displays the system hostname |
| `uname -a` | Shows kernel and machine information |
| `date` | Shows the current date and time |
| `cal` | Displays a calendar (if installed) |
| `env` | Prints environment variables |
| `ps` | Displays process information |
| `lsof` | Lists open files (if installed) |

## Networking

| Command | Description |
|---|---|
| `ip` | Inspects and configures addresses, links, and routes |
| `ss` | Inspects sockets and listening ports |
| `ifconfig` | Legacy network interface utility, possibly not installed |
| `netstat` | Legacy networking statistics utility, possibly not installed |

## Hardware, Storage, and Software

| Command | Description |
|---|---|
| `lsblk` | Lists block devices |
| `lsusb` | Lists USB devices (if installed) |
| `lspci` | Lists PCI devices (if installed) |
| `df -h` | Displays filesystem space usage in human-readable units |
| `free -h` | Displays memory and swap usage |
| `dpkg -l` | Lists packages known to dpkg on Debian-based systems |

See [System Information and Networking](System%20Information%20and%20Networking.md).

## Text Processing

| Command | Description |
|---|---|
| `cat` | Concatenates files and prints their contents |
| `more`, `less` | Displays text a screen at a time |
| `head`, `tail` | Displays the beginning or end of input |
| `grep` | Filters lines by pattern |
| `sort` | Sorts lines |
| `wc -l` | Counts newline characters (usually lines) |
| `cut` | Selects fields or characters |
| `tr` | Translates or deletes characters |
| `column -t` | Aligns text into columns |
| `awk` | Processes records and fields |
| `sed` | Edits text streams |

See [Text Processing](Text%20Processing.md) and [Input, Output and Redirection](Input%2C%20Output%20and%20Redirection.md).

## Useful Resource

- [ExplainShell](https://explainshell.com/) — explains shell commands and arguments.
