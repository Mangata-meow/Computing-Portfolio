
# Shell and Prompt Customization

The shell is a command-line interface that allows users to interact with the operating system by entering commands.

Bash (Bourne Again Shell) is one of the most widely used shells on Linux.

## Bash Prompt (PS1)

The Bash prompt is the text displayed before each command in an interactive terminal.

It is controlled by the `PS1` variable (Prompt String 1).

By modifying `PS1`, we can customize the information displayed in the terminal, including:

- Username
- Hostname
- Current working directory
- Date and time

## Special Characters

| Character | Description |
|---|---|
| `\d` | Current date (e.g., Tue Oct 26) |
| `\D{%Y-%m-%d}` | Custom date format (YYYY-MM-DD) |
| `\H` | Full hostname |
| `\j` | Number of jobs managed by the shell |
| `\n` | New line |
| `\r` | Carriage return |
| `\s` | Shell name |
| `\t` | Current time (24-hour HH:MM:SS) |
| `\T` | Current time (12-hour HH:MM:SS) |
| `\@` | Current time (12-hour AM/PM format) |
| `\u` | Current username |
| `\w` | Current working directory, with the home directory abbreviated as `~` |

## Example

This prompt displays the username, hostname, current working directory, and time.

```bash
PS1="\u@\H:\w [\t]$ "
```

**Example output:**

```text
julia@cyber:/home/julia/projects [14:32:10]$
```


---

## Useful Resources

- [ExplainShell](https://explainshell.com/) – An interactive tool that explains Linux shell commands and their arguments. Useful for understanding unfamiliar commands, options, and command combinations.

