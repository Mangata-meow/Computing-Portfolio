<h1>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linux/linux-original.svg" alt="Linux" width="40" align="center" />
  Vim Text Editor
</h1>


Vim (Vi Improved) is a powerful, terminal-based text editor commonly used in Linux.

Unlike Nano, Vim is a modal editor, meaning that different keyboard inputs perform different actions depending on the currently active mode.

Vim is generally more complex than Nano but provides advanced features for editing and manipulating text efficiently.

---

## 1. Vim Modes

Vim has several modes that determine how keyboard input is interpreted.

### 1.1. Normal Mode

In Normal mode, keyboard inputs are interpreted as editor commands rather than being inserted into the text.

This is the default mode when Vim starts.

Normal mode allows users to:
- Navigate through text
- Delete characters or lines
- Copy and paste text
- Switch between modes

Press `Esc` to return to Normal mode from most other modes.

### 1.2. Insert Mode

In Insert mode, typed characters are inserted into the file.

**Entering Insert mode:**

- `i` → inserts text before the cursor
- `a` → inserts text after the cursor
- `o` → creates a new line below the current line and enters Insert mode

Press `Esc` to return to Normal mode.

### 1.3. Visual Mode

Visual mode is used to select and highlight parts of the text.

The selected text can then be edited, deleted, copied, or replaced.

**Entering Visual mode:**

- `v` → character-wise selection
- `V` → line-wise selection
- `Ctrl + V` → block-wise selection

### 1.4. Command-line Mode

Command-line mode allows users to enter commands at the bottom of the editor.

It is commonly used for:
- Saving files
- Exiting Vim
- Searching and replacing text
- Executing editor commands

**Entering Command-line mode:**

Press `:` while in Normal mode.

### 1.5. Replace Mode

Replace mode allows newly typed characters to overwrite existing text.

If there are no more characters to overwrite, additional characters can be inserted.

**Entering Replace mode:**

Press `R` in Normal mode.

### 1.6. Ex Mode

Ex mode provides an interface for executing a sequence of Ex commands.

It originates from the Ex text editor, which preceded Vi.

**Entering Ex mode:**

Press `Q` in Normal mode.

To return to Normal mode, type `visual` and press `Enter`.

---

## 2. Basic Vim Commands

### Opening a File

```bash
vim notes.txt
```

Opens `notes.txt` in Vim.

If the file does not exist, it can be created when the contents are saved.

### Saving and Exiting

These commands are entered from Normal mode by typing `:` followed by the command.

| Command | Description |
|---|---|
| `:w` | Save the file |
| `:q` | Quit Vim |
| `:wq` | Save and quit |
| `:q!` | Quit without saving unsaved changes |
| `:w!` | Force writing the file when permitted |
| `:x` | Save changes if necessary and quit |

### Basic Navigation

In Normal mode:

| Key | Description |
|---|---|
| `h` | Move left |
| `j` | Move down |
| `k` | Move up |
| `l` | Move right |
| `gg` | Move to the beginning of the file |
| `G` | Move to the last line |
| `0` | Move to the beginning of the current line |
| `$` | Move to the end of the current line |

### Basic Text Editing

In Normal mode:

| Command | Description |
|---|---|
| `x` | Delete the character under the cursor |
| `dd` | Delete (cut) the current line |
| `yy` | Copy (yank) the current line |
| `p` | Paste after the cursor or below the current line |
| `u` | Undo the last change |
| `Ctrl + R` | Redo an undone change |

---

## 3. Vim Tutorial

Vim provides an interactive tutorial to help beginners learn its commands and navigation.

**Launch the tutorial from the Linux terminal:**

```bash
vimtutor
```

The tutorial includes practical exercises covering:
- Navigation
- Editing text
- Deleting and inserting characters
- Saving and exiting
- Searching within files

---

## 4. Practical Example

**Task:** Create a text file, write a message, save it, and exit Vim.

**Step 1:** Open Vim.

```bash
vim notes.txt
```

**Step 2:** Press `i` to enter Insert mode.

**Step 3:** Type:

```text
Hello, Linux!
I am learning Vim.
```

**Step 4:** Press `Esc` to return to Normal mode.

**Step 5:** Type:

```vim
:wq
```

Press `Enter` to save the file and exit.

**Step 6:** Verify the file contents.

```bash
cat notes.txt
```

**Expected output:**

```text
Hello, Linux!
I am learning Vim.
```

---
