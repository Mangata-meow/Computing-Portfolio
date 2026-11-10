
# Nano Text Editor

Nano is a beginner-friendly, terminal-based text editor available on many Linux systems.

It allows users to create, view, and edit text files directly from the command line.

## Opening and Creating Files

```bash
nano notes.txt
```

This command opens `notes.txt` in Nano.

If the file does not exist, Nano opens a new buffer, and the file is created when the changes are saved.

## Keyboard Shortcuts

In Nano, the `^` symbol represents the **Ctrl** key.

For example, `^O` means `Ctrl + O`.

| Shortcut | Description |
|---|---|
| `Ctrl + W` | Search for text |
| `Ctrl + O` | Save the file (Write Out) |
| `Ctrl + X` | Exit Nano |
| `Ctrl + K` | Cut the current line or selected text |
| `Ctrl + U` | Paste previously cut text |
| `Ctrl + G` | Display help |
| `Ctrl + C` | Display cursor position |

## Example

Open a new text file:

```bash
nano notes.txt
```

1. Type some text into the editor.
2. Press `Ctrl + O` to save.
3. Press `Enter` to confirm the filename.
4. Press `Ctrl + X` to exit.

To display the saved file:

```bash
cat notes.txt
```
