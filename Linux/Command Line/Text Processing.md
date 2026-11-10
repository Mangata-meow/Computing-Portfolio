
<h1>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linux/linux-original.svg" alt="Linux" width="40" align="center" />
  Text Processing in Linux
</h1>

Linux command-line tools can read, search, filter, format, and transform text streams.

## 1. Viewing Files

### `cat`

```bash
cat /etc/passwd
```

Prints the file contents to standard output.

### `more` and `less`

```bash
more /etc/passwd
less /etc/passwd
cat /etc/passwd | more
```

Both are pagers for reading long text. Press `q` to exit. `less` generally offers more navigation and search features; whether its text remains on the terminal after exit depends on terminal and pager settings.

### `head` and `tail`

```bash
head /etc/passwd       # First 10 lines by default
tail /etc/passwd       # Last 10 lines by default
tail -n 5 /etc/passwd  # Last 5 lines
```

## 2. Sorting and Counting

```bash
sort /etc/passwd
wc -l /etc/passwd
```

`sort` sorts lines using the active locale's collation rules. `wc -l` counts newline characters.

## 3. Searching with `grep`

```bash
grep '/bin/bash' /etc/passwd
```

Finds lines containing `/bin/bash` (often user entries configured with that login shell).

```bash
grep -E -v 'false|nologin' /etc/passwd
```

Excludes lines containing `false` or `nologin`. The `-E` flag makes `|` an alternation operator; without `-E`, GNU grep can use `\|` as an extension.

For detailed patterns, see [Regular Expressions](../03%20-%20Pattern%20Matching/Regular%20Expressions.md).

## 4. Extracting Fields with `cut`

`cut` selects delimited fields or character positions; it does not remove delimiters everywhere in a line.

```bash
cut -d ':' -f 1 /etc/passwd
```

- `-d ':'` sets the delimiter to a colon.
- `-f 1` selects the first field (username).

**Example using `family.txt`:** The file must contain colon-delimited text:

```text
Julia:22:Sweden
Albin:31:Poland
Bono:5:Sweden
```

```bash
cut -d ':' -f 1,2 family.txt
```

Output:

```text
Julia:22
Albin:31
Bono:5
```

## 5. Replacing Characters with `tr`

```bash
tr ':' ' ' < /etc/passwd
```

Replaces every colon with a space in the output. `tr` operates on character sets, not full regular expressions.

## 6. Formatting Columns

```bash
column -t family.txt
```

`column -t` aligns whitespace-separated fields by default. For the colon-separated example above, specify a delimiter when supported:

```bash
column -s ':' -t family.txt
```

## 7. Processing Records with `awk`

```bash
awk '{print $1, $NF}' /etc/passwd
```

By default, `awk` splits each input line on whitespace; `$1` is the first field and `$NF` is the last field. Since `/etc/passwd` is colon-delimited, use `-F ':'` for its actual fields:

```bash
awk -F ':' '{print $1, $3, $7}' /etc/passwd
```

This prints username, UID, and login shell.

## 8. Editing Streams with `sed`

```bash
sed 's/bin/HTB/g' /etc/passwd
```

The substitution command `s/old/new/g` replaces all matches on each line in the output. Without `-i`, the source file is not changed.

## 9. Practice Exercises: `/etc/passwd`

These exercises are from the original notes. They are presented with example solutions using colon-delimited fields.

| # | Task |
|---|---|
| 1 | Show the line for username `cry0l1t3` |
| 2 | Show all usernames |
| 3 | Show username `cry0l1t3` and its UID |
| 4 | Show username `cry0l1t3` and UID separated by a comma |
| 5 | Show username `cry0l1t3`, UID, and login shell separated by commas |
| 6 | Show all usernames, UIDs, and login shells separated by commas |
| 7 | Same as 6, excluding entries containing `nologin` or `false` |
| 8 | Same as 6, excluding entries containing `nologin`, and count the remaining lines |

**Example solutions:**

```bash
# 1
awk -F ':' '$1=="cry0l1t3"' /etc/passwd

# 2
cut -d ':' -f 1 /etc/passwd

# 3
awk -F ':' '$1=="cry0l1t3" {print $1, $3}' /etc/passwd

# 4
awk -F ':' '$1=="cry0l1t3" {print $1 "," $3}' /etc/passwd

# 5
awk -F ':' '$1=="cry0l1t3" {print $1 "," $3 "," $7}' /etc/passwd

# 6
awk -F ':' '{print $1 "," $3 "," $7}' /etc/passwd

# 7
awk -F ':' '$7 !~ /nologin|false/ {print $1 "," $3 "," $7}' /etc/passwd

# 8
awk -F ':' '$7 !~ /nologin/ {print $1 "," $3 "," $7}' /etc/passwd | wc -l
```

The `cry0l1t3` account may not exist on your own computer; those exercises assume the target lab environment contains it.

See [Input, Output and Redirection](Input%2C%20Output%20and%20Redirection.md) for pipelines and standard streams.

