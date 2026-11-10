
# Regular Expressions (RegEx)

Regular Expressions (RegEx) allow users to search, filter, replace, and manipulate text with precision.

A regular expression is a sequence of characters and special symbols that together form a search pattern.

RegEx is commonly used for:
- Searching through files and text
- Filtering command output
- Finding patterns in system logs
- Validating data
- Replacing or manipulating text
- Analyzing data during cybersecurity investigations

In Linux, regular expressions are frequently used with tools such as `grep`, `sed`, and `awk`.

---

## 1. RegEx Dictionary

### Basic Metacharacters

Metacharacters are special characters that have a specific meaning in regular expressions.

| Symbol | Meaning | Example |
|---|---|---|
| `.` | Matches any single character (except newline by default) | `c.t` matches `cat`, `cut`, `cot` |
| `^` | Matches the beginning of a line | `^Hello` |
| `$` | Matches the end of a line | `world$` |
| `*` | Matches zero or more repetitions of the preceding element | `ab*` |
| `+` | Matches one or more repetitions of the preceding element | `ab+` |
| `?` | Matches zero or one occurrence of the preceding element | `colou?r` |
| `\|` | Alternation (OR) | `cat\|dog` |
| `()` | Groups parts of a regular expression | `(ab)+` |
| `[]` | Defines a character class | `[abc]` |
| `[^...]` | Matches characters not included in the specified class | `[^0-9]` |
| `{n}` | Matches exactly n repetitions | `[0-9]{3}` |
| `{n,m}` | Matches between n and m repetitions | `[0-9]{2,4}` |

**Important:** The examples above use Extended Regular Expressions (ERE), supported by `grep -E`.

### Character Classes

Square brackets `[]` define a set or range of characters to match.

| Pattern | Meaning |
|---|---|
| `[abc]` | Matches `a`, `b`, or `c` |
| `[a-z]` | Matches a lowercase letter from a to z |
| `[A-Z]` | Matches an uppercase letter from A to Z |
| `[0-9]` | Matches a digit from 0 to 9 |
| `[a-zA-Z]` | Matches an uppercase or lowercase ASCII letter |
| `[^abc]` | Matches any character except `a`, `b`, or `c` |
| `[.,]` | Matches a literal dot or comma |

**Example:**

```bash
echo "cat cot cut" | grep -Eo "c[ao]t"
```

**Output:**

```text
cat
cot
```

The pattern `c[ao]t` matches words containing either `a` or `o` between `c` and `t`.

### Special Character Sequences

Some regex engines support additional sequences.

| Sequence | Meaning |
|---|---|
| `\d` | Digit |
| `\D` | Non-digit |
| `\b` | Word boundary |
| `\A` | Beginning of the entire text |
| `\Z` | End of the entire text |

**Important:** These sequences are not all supported by every regex engine.

For example, Python supports all five, but standard POSIX regular expressions do not define them. GNU `grep` supports `\b` and certain other extensions, but `\d`, `\D`, `\A`, and `\Z` should not be assumed to work with `grep -E`.

For portable Linux `grep` patterns, use `[0-9]` instead of `\d`, and `[^0-9]` instead of `\D`.

---

## 2. Important Patterns Worth Memorizing

### A Word Beginning with a Capital Letter

```regex
^[A-Z][a-z]+
```

This pattern matches text at the beginning of a line that:
1. Starts with an uppercase ASCII letter.
2. Is followed by one or more lowercase ASCII letters.

**Examples:**
- `Hello` → matches
- `Linux` → matches
- `hello` → does not match
- `HELLO` → does not match as a complete word

Note that the pattern does not require the entire line to end after the word.

To match the entire line, use:

```regex
^[A-Z][a-z]+$
```

### Words Containing Exactly Three Letters

```regex
\b[a-zA-Z]{3}\b
```

This pattern matches three-letter ASCII words.

**Examples:**
- `cat` → matches
- `dog` → matches
- `Linux` → does not match

This example uses `\b`, which is supported by GNU `grep` as an extension.

**Linux example:**

```bash
echo "cat dog Linux sun" | grep -Eo '\b[a-zA-Z]{3}\b'
```

**Output:**

```text
cat
dog
sun
```

### Beginning and End of a Line

- `^` → matches the beginning of a line
- `$` → matches the end of a line

**Example:**

```regex
^admin$
```

This matches a line containing exactly `admin`.

It does not match `administrator` or `myadmin`.

### Searching for Literal Special Characters

Some characters have special meanings in regex.

To search for them literally, place a backslash `\` before the character.

**Examples:**

```regex
\.
\*
\+
\?
\^
\$
```

These match literal dots, asterisks, plus signs, question marks, carets, and dollar signs.

**Example:**

```bash
echo "Price: $50" | grep -E '\$50'
```

This searches for the literal text `$50`.

---

## 3. Grouping Search Patterns

### Parentheses `()`

Round brackets group parts of a regular expression.

They allow multiple characters or patterns to be processed together.

**Example:**

```regex
(ab)+
```

Matches:
- `ab`
- `abab`
- `ababab`

The `+` applies to the entire group `(ab)`.

### Square Brackets `[]`

Square brackets define character classes.

**Example:**

```regex
[a-z]
```

Matches one lowercase ASCII letter.

**Example:**

```regex
[0-9]
```

Matches one digit.

### Curly Brackets `{}`

Curly brackets define quantifiers.

They specify how many times the preceding character, character class, or group should appear.

| Pattern | Meaning |
|---|---|
| `a{3}` | Exactly three `a` characters |
| `a{2,5}` | Between two and five `a` characters |
| `a{2,}` | At least two `a` characters |
| `[0-9]{4}` | Exactly four digits |

**Example:**

```regex
^[0-9]{4}$
```

Matches a line containing exactly four digits.

### Pipe `|` — OR Operator

The pipe symbol represents alternation (OR) in Extended Regular Expressions.

It matches either the expression on the left or the expression on the right.

**Example:**

```regex
(cat|dog)
```

Matches `cat` or `dog`.

### Dot and Asterisk `.*`

The combination `.*` means:

- `.` → any character except newline by default
- `*` → zero or more repetitions

Together, they match any sequence of zero or more characters.

**Example:**

```regex
my.*false
```

This matches text containing `my` followed later by `false`, with any number of characters between them.

It is sometimes used to express an AND-like condition, but it is not a true AND operator.

The order matters: `my` must appear before `false`.

---

## 4. Using RegEx with grep

The `grep` command searches text for lines matching a specified pattern.

**General syntax:**

```bash
grep [options] "pattern" filename
```

### Extended Regular Expressions

To use Extended Regular Expressions, add `-E`:

```bash
grep -E "pattern" filename
```

This enables operators such as:

- `+`
- `?`
- `|`
- `()`
- `{}`

Without `-E`, GNU `grep` uses Basic Regular Expressions (BRE), where several of these operators require different escaping.

Some features, such as `.`, `*`, `^`, `$`, and character classes, already work in basic regex.

---

## 5. Example: OR Operator

We want to find lines in `/etc/passwd` containing either `my` or `false`.

**Command:**

```bash
grep -E "(my|false)" /etc/passwd
```

**Example output:**

```text
lxd:x:105:65534::/var/lib/lxd/:/bin/false
pollinate:x:109:1::/var/cache/pollinate:/bin/false
mysql:x:116:120:MySQL Server,,:/nonexistent:/bin/false
```

**Explanation:**

| Part | Meaning |
|---|---|
| `grep` | Tool used to search text |
| `-E` | Enables Extended Regular Expressions |
| `(my\|false)` | Searches for either `my` or `false` |
| `/etc/passwd` | File being searched |

The command displays every line containing at least one of the two patterns.

**Note:** Actual output depends on the user accounts configured on the system.

---

## 6. Example: AND-like Pattern

We want to find lines containing both `my` and `false`, with `my` appearing first.

**Command:**

```bash
grep -E "my.*false" /etc/passwd
```

**Example output:**

```text
mysql:x:116:120:MySQL Server,,:/nonexistent:/bin/false
```

**Explanation:**

- `my` → matches the literal characters `my`
- `.*` → matches zero or more characters
- `false` → matches the literal text `false`

The command returns lines where `my` appears before `false`.

**Important:** This is not a general AND operator because the order of the patterns matters.

---

## 7. Combining grep Commands with Pipes

Another way to find lines containing both patterns is to combine two `grep` commands using a pipe.

**Example:**

```bash
grep -E "my" /etc/passwd | grep -E "false"
```

**Example output:**

```text
mysql:x:116:120:MySQL Server,,:/nonexistent:/bin/false
```

**How it works:**

1. `grep -E "my" /etc/passwd` searches for lines containing `my`.
2. The pipe `|` passes the output of the first command to the second command.
3. `grep -E "false"` filters those lines to keep only those containing `false`.

This approach matches lines containing both patterns, regardless of their order.

For these literal search strings, `-E` is optional.

**Difference between the two methods:**

```bash
grep -E "my.*false" /etc/passwd
```

Requires `my` to appear before `false`.

```bash
grep "my" /etc/passwd | grep "false"
```

Requires both patterns to appear somewhere on the same line, in any order.

---

## 8. Additional Practical Examples

### Find Lines Beginning with a Specific Word

```bash
grep -E "^root" /etc/passwd
```

Finds lines starting with `root`.

### Find Lines Ending with a Specific Word

```bash
grep -E "false$" /etc/passwd
```

Finds lines ending with `false`.

### Find Lines Containing Numbers

```bash
grep -E "[0-9]" example.txt
```

Finds lines containing at least one digit.

### Find Lines Containing Exactly Three Digits

```bash
grep -E "^[0-9]{3}$" example.txt
```

Finds lines containing exactly three digits and nothing else.

### Find Multiple Keywords in a Log File

```bash
grep -Ei "error|failed|denied" /var/log/auth.log
```

Searches for lines containing `error`, `failed`, or `denied`, ignoring case.

The log file path and its availability depend on the Linux distribution.

---

## 9. Useful grep Options

| Option | Description |
|---|---|
| `-E` | Uses Extended Regular Expressions |
| `-i` | Ignores uppercase/lowercase differences |
| `-n` | Displays matching line numbers |
| `-v` | Displays lines that do not match |
| `-r` | Searches recursively through directories |
| `-o` | Displays only matching parts of lines |
| `-c` | Counts matching lines |
| `-l` | Displays filenames containing matches |
| `-w` | Matches whole words |
| `-x` | Matches whole lines |

**Example:**

```bash
grep -Ein "error|failed" /var/log/syslog
```

This searches for `error` or `failed`, ignores case, and displays matching line numbers.

---

## 10. Useful Resources

- [Regex101](https://regex101.com/) - Interactive regular expression testing and explanation. Choose the appropriate regex flavor.
- [ExplainShell](https://explainshell.com/) - Explains Linux shell commands and their arguments.
- [GNU grep Manual](https://www.gnu.org/software/grep/manual/grep.html) - Official documentation for GNU grep.

---
