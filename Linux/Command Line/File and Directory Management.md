<h1>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linux/linux-original.svg" alt="Linux" width="40" align="center" />
  File and Directory Management
</h1>


## 1. Navigating Directories

```bash
pwd                  # Print working directory
cd                   # Go to home directory
cd /etc              # Go to an absolute path
cd ..                # Go to the parent directory
cd -                 # Return to the previous directory
ls                   # List entries
```

### Absolute and Relative Paths

- **Absolute path:** Starts at the root directory `/`, for example `/home/julia/projects`.
- **Relative path:** Starts from the current working directory, for example `projects/notes.txt` or `../notes.txt`.
- `.` means the current directory; `..` means the parent directory.

## 2. Listing Files

| Command | Meaning |
|---|---|
| `ls -l` | Long format, including permissions, ownership, size, and modification time |
| `ls -a` | Include hidden entries (names beginning with `.`) |
| `ls -la` | Long format including hidden entries |
| `ls -lt` | Long format, sorted by modification time (newest first) |
| `ls -r` | Reverse the current sorting order |
| `ls -S` | Sort by size (largest first) |
| `ls -t` | Sort by modification time |
| `tree` | Display the directory tree, if installed |
| `tree .` | Display the tree starting at the current directory |

## 3. Creating Files and Directories

```bash
mkdir Storage
mkdir -p Storage/local/user/documents
touch Storage/local/user/userinfo.txt
file Storage/local/user/userinfo.txt
```

- `mkdir -p` creates missing parent directories as needed.
- `touch` creates an empty file if it does not exist; otherwise it updates timestamps.
- `file` examines a file to identify its type.

## 4. Moving, Renaming, and Copying

```bash
mv info.txt information.txt      # Rename a file
mv information.txt Storage/      # Move it to another directory
cp Storage/readme.txt Storage/local/  # Copy a file
cp -r Storage/ Storage-backup/  # Copy a directory recursively
```

## 5. Finding Files

### `which`

```bash
which curl
which nc
```

Shows the path of an executable found via the current command search path, if one is found. Shell builtins and aliases may need other inspection tools such as `type`.

### `locate`

```bash
locate '*.bak'
sudo updatedb
```

`locate` searches a prebuilt filename database, so results can be outdated. `updatedb` refreshes that database when the relevant tools are installed.

### `find`

```bash
find /etc -type f -name '*.conf'
```

`find` traverses directories and can filter by name, type, ownership, size, and timestamps.

**Detailed example from the exercises:**

```bash
find / -type f -name '*.conf' -user root -size +20k -newermt 2020-03-03 -exec ls -al {} \; 2>/dev/null
```

| Part | Explanation |
|---|---|
| `/` | Search starting from the filesystem root |
| `-type f` | Regular files only |
| `-name '*.conf'` | Filenames ending in `.conf` |
| `-user root` | Files owned by `root` |
| `-size +20k` | Files larger than 20 KiB in `find`'s 1-KiB units |
| `-newermt 2020-03-03` | Modification time later than the specified date/time |
| `-exec ls -al {} \;` | Run `ls -al` for each matching path |
| `2>/dev/null` | Discard error output, including permission errors |

**Size range example:**

```bash
find / -type f -name '*.conf' -size +25k -size -28k -newermt 2020-03-03 2>/dev/null
```

Note: `find` rounds sizes into units when applying `-size k`; the two bounds select files whose rounded-up size is 26 or 27 KiB. Quote wildcard patterns so the shell does not expand them before `find` receives them.

## 6. Inodes

An **inode** is a filesystem data structure that stores metadata about a file, such as its permissions, ownership, and block locations. Each inode has a number unique within its filesystem. A filename is stored in a directory entry that refers to an inode.

```bash
ls -i notes.txt
```

See [File System](../01%20-%20Linux%20Fundamentals/File%20System.md) for the Linux directory hierarchy.
