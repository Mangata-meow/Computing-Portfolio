<h1>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linux/linux-original.svg" alt="Linux" width="40" align="center" />
  Input, Output, Pipes, and Redirection
</h1>

## 1. File Descriptors and Standard Streams

A **file descriptor (FD)** is a nonnegative integer used by a process to refer to an open file, socket, pipe, or other I/O resource.

| FD | Stream | Purpose |
|---|---|---|
| `0` | STDIN | Standard input |
| `1` | STDOUT | Normal output |
| `2` | STDERR | Error output |

In an interactive terminal, all three streams are typically connected to the terminal, but they can be redirected.

```bash
cat
```

Type some text and press Enter: `cat` reads from standard input and writes the text to standard output. Press `Ctrl + D` on an empty line to signal end-of-file (EOF).

**EOF** is a condition indicating that no more input is available; it is not a special character stored at the end of every file.

## 2. Output Redirection (`>` and `>>`)

```bash
echo 'Hello world' > hello.txt
cat hello.txt
```

`>` redirects standard output to a file, creating it if needed and truncating it if it exists.

```bash
echo 'Another line' >> hello.txt
```

`>>` appends standard output without replacing existing content.

```bash
echo 'Hello world' 1> hello.txt
```

`1>` is the explicit form of `>` for standard output.

## 3. Error Redirection (`2>`)

```bash
cat nonexistent.txt
cat nonexistent.txt 2> errors.txt
cat errors.txt
```

`2>` sends standard error to a file instead of displaying it in the terminal.

### `/dev/null`

```bash
find /etc -name '*.conf' 2>/dev/null
```

`/dev/null` discards data written to it. The example hides errors; it does not change which files `find` searches.

## 4. Input Redirection (`<`) and Here-Documents (`<<`)

```bash
wc -l < hello.txt
```

`<` supplies a file as standard input.

```bash
cat <<EOF
Hello
This is a here-document.
EOF
```

`<<` introduces a here-document: the shell provides the following lines as standard input until it encounters the delimiter (`EOF` here).

## 5. Pipes (`|`)

A pipe connects one command's standard output to the next command's standard input.

```bash
ls | grep cat
```

This filters the displayed filenames to lines containing `cat`. For robust filename processing, avoid parsing `ls` output in scripts.

```bash
cat /etc/passwd | grep '/bin/bash'
```

The second command keeps lines containing `/bin/bash`.

## 6. Counting Output

wc -l hello.txt
find /etc -name '*.conf' 2>/dev/null | wc -l
```

`wc -l` counts newline characters; for typical line-oriented command output, that is the number of lines.

## 7. Combined Hack The Box Example

```bash
find /etc/ -name '*.conf' 2>/dev/null | grep systemd | wc -l
```

| Part | Explanation |
|---|---|
| `find /etc/` | Search under `/etc/` |
| `-name '*.conf'` | Match names ending in `.conf` |
| `2>/dev/null` | Discard error messages |
| `| grep systemd` | Keep paths containing `systemd` |
| `| wc -l` | Count remaining output lines |

## 8. Redirection Cheat Sheet

| Operator | Effect |
|---|---|
| `<` | Read standard input from a file |
| `>` | Write standard output, replacing file contents |
| `>>` | Append standard output |
| `2>` | Redirect standard error |
| `|` | Pipe standard output into another command |
| `<<` | Provide a here-document as standard input |

See [Text Processing](Text%20Processing.md) for commands commonly used in pipelines.
