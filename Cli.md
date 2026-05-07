# Command Line Interface

## Actions

### File and Folder Operations in Linux

#### Create

```bash
touch file.txt        # Create a new file
mkdir folder_name     # Create a new folder
```

#### Read

```bash
cat file.txt          # View file content
ls                    # List files and folders
```

#### Update

```bash
nano file.txt         # Edit a file
mv old_name new_name  # Rename file or folder
```

#### Delete

```bash
rm file.txt           # Delete a file
rmdir folder_name     # Delete an empty folder
rm -rf folder_name    # Delete folder and contents
```

#### Move

```bash
mv file.txt /path/      # Move file to another location
mv folder_name /path/   # Move folder to another location
```

* Destination does not exist: Source gets renamed
* Destination exists as file: Destination gets replaced/overwritten
* Destination exists as directory: Source is moved into directory

### Check Disk Status

```bash
df -h        # disk space in human-readable format
du -sh *     # size of files and folders in current directory(disk usage)
```

### Process Status

```bash
ps aux                           # all running processes
ps aux | grep firefox            # search match
ps aux | awk '{print $2}'        # PIDs in column 2
ps aux | grep firefox | awk '{print $2}'  # Extract PID of firefox process
```

* `a` → all users
* `u` → user-oriented format
* `x` → processes not attached with terminal

### Getting the Most Senior Parent Process

```bash
ps -ef                          # all processes, formatted
ps -p 1                         # root parent process (PID 1)
pstree                          # process hierarchy tree
```

* `PID` → Process ID
* `PPID` → Parent Process ID
* `PID 1` is the most senior parent process (`init` or `systemd`)

### File Permissions

```bash
ls -l file.txt                  # View file permissions
chmod 755 file.txt              # Change permissions 
chmod -R 755 folder_name        # recursive
chmod u+x file.txt              # add execute for owner
chmod a+x script.sh             # for everyone
chown user file.txt             # Change file owner
chown user:group file.txt       # Change owner and group
```

#### Permission Symbols

* `u` → User/Owner
* `g` → Group
* `o` → Others
* `a` → All users

#### Permission Types

* `r` → Read
* `w` → Write
* `x` → Execute

#### Permission Numbers

* `4` → Read (`r`)
* `2` → Write (`w`)
* `1` → Execute (`x`)

### Text Processing

```bash
tail -n 10 file.txt                         # last 10 lines
grep "word" file.txt                        # search word
grep -oi "word" file.txt | wc -l            # occurrences of a word ('o'-output, 'i'-case)
```

* `grep` → Search text patterns
* `wc -l` → Count lines

### Basics of `sed` and `awk`

```bash
awk '{print $1}' file.txt                   # Print first column
awk '/word/ {print}' file.txt               # Print lines with a word
awk '{print NF}' file.txt                   # number of fields in each line

sed -n '1,5p' file.txt                      # Print lines 1 to 5
sed 's/old/new/g' file.txt                  # Replace old with new
sed -i "" 's/old/new/g' file.txt            # Save changes
sed '/word/d' file.txt                      # Delete lines with word
```

* `s` → substitute (replace 1st match in a line)
* `g` → global (all matches)

### Absolute vs Relative Paths

#### Absolute Path

```bash
cd /Users/name/Documents      # Full path from root 
```

#### Relative Path

```bash
cd Documents/project          # Path relative to current directory
```

#### Special Symbols

```bash
.     # Current directory
..    # Parent directory
~     # Home directory
```

### `find` Command

```bash
find . -name "file.txt"                 # Find file by name
find d1 -type d                         # all directories in d1
find . -type f                          # all files
find . -name "*.txt"                    # all .txt files
find . -size +10M                       # files larger than 10MB
find . -mtime -1                        # files modified in last 1 day
find . -name "file.txt" -delete         # Find and delete
```

### `ls` Command Flags

```bash
ls -a                 # hidden files
ls -l                 # long format
ls -t                 # Sort by time
ls -r                 # Reverse sort order
ls -h                 # Human-readable file sizes (KB, MB, GB)
ls -altrh             # Combine flags
```

### Terminal Control Codes

```bash
Ctrl + C    # Stop current running process
Ctrl + D    # Exit terminal(EOF)
Ctrl + Z    # Suspend the current process
Ctrl + R    # Search previous commands
Ctrl + L    # Clear terminal screen
Ctrl + A    # Cursor to beginning of line
Ctrl + E    # Cursor to end of line
Ctrl + U    # Delete text before cursor
Ctrl + K    # Delete text after cursor
Ctrl + W    # Delete previous word
```

### Difference Between `Ctrl + C` and `Ctrl + Z`

```bash
Ctrl + C    # Stop and terminate the running process
Ctrl + Z    # Pause/suspend the running process
```

* `Ctrl + C`

  * Sends `SIGINT` signal
  * Process is terminated immediately
  * Usually cannot continue from where it stopped

* `Ctrl + Z`

  * Sends `SIGTSTP` signal
  * Process is suspended (paused)
  * Can be found using jobs
  * Can be resumed later using:

```bash
fg    # Resume in foreground
bg    # Resume in background
```

### Reverse Search with `Ctrl + R`

```bash
Ctrl + R    # Search previous commands from history
```

#### How to Use

1. Press `Ctrl + R`
2. Start typing a previous command
3. Matching command shows automatically
4. Press:

   * `Enter` → Run the command
   * Right Arrow → Edit the command
   * `Ctrl + R` again → Next matching result
   * `Ctrl + C` → Exit search

#### Example

```bash
(reverse-i-search)`git': git status
```

### Tab Autocompletion

```bash
Tab         # Auto-complete commands, file names, and folder names
```

```bash
cd Doc<Tab>
```

Automatically gives:

```bash
cd Documents/
```

* Press `Tab` once → Auto-complete if match is unique
* Press `Tab` twice → Show all matching options
* Works for:

  * Commands
  * File names
  * Folder names
  * Paths

### Navigate Command History with Arrow Keys

```bash
↑    # Show previous command
↓    # Show next command
←    # Move cursor left
→    # Move cursor right
```

## Review Questions

### 1. Go into your home directory

```bash
cd ~
```

### 2. Create a directory `d1`

```bash
mkdir d1
```

### 3. Create a file `a.txt` inside `d1`

```bash
touch d1/a.txt
```

### 4. Check permissions of `a.txt`

```bash
ls -l d1/a.txt
```

Example output:

```bash
-rw-r--r--  1 user  staff  0 May 7 10:00 a.txt
```

```text
rw-r--r-- = 644
```

### 5. Permission Elements and Number Conversion

#### User Categories

```text
User   Group   Others
```

Example:

```text
rwxr-xr-x
```

* `rwx` → User
* `r-x` → Group
* `r-x` → Others

#### Decimal to Binary Conversion

```text
r = 4 = 100
w = 2 = 010
x = 1 = 001
```

Example:

```text
7 = rwx = 111
5 = r-x = 101
4 = r-- = 100
```

### 6. Change permissions of `a.txt` to `755`

```bash
chmod 755 d1/a.txt
```

### 7. Add a directory `d2`

```bash
mkdir d2
```

### 8. Change permissions of `d2` and everything inside to `755`

```bash
chmod -R 755 d2
```

### 9. Start the Firefox browser

#### Linux

```bash
firefox
```

#### macOS

```bash
open -a Firefox
```

### 10. List all processes in your computer

```bash
ps aux
```

### 11. Find PID of Firefox Browser

```bash
ps aux | grep firefox
```

```bash
ps aux | grep firefox | awk '{print $2}'
```

#### Parent Process vs Child Process

* Parent Process → A process that starts another process
* Child Process → A process created by another process

Example:

Terminal → Parent Process
Firefox  → Child Process

```text
PID   → Process ID
PPID  → Parent Process ID
```

### 12. Kill the Firefox process

```bash
ps aux | grep firefox | awk '{print $2}' | xargs kill
```

#### Force Kill

```bash
ps aux | grep firefox | awk '{print $2}' | xargs kill -9
```

* `awk '{print $2}'` → Extract PID
* `xargs` → Pass PID as argument
* `kill` → Stop process
* `kill -9` → Force terminate process

### 13. Find your current user in Linux

```bash
whoami
```

### 14. Find your group in Linux

```bash
groups
```

```bash
id
```

### 15. Find your computer architecture

```bash
uname -m        # architecture
uname -a        # all system information
uname -s        # kernel name
uname -r        # kernel release
```

### 16. Find your audio driver

#### linux

```bash
lspci | grep -i audio
```

```bash
lspci -k | grep -A 3 -i audio
```

#### mac

```bash
system_profiler SPAudioDataType
```

### 17. Find all files and directories containing `java`

```bash
cd ~
find . | grep "java"
```

#### Case-insensitive search

```bash
find . | grep -i "java"
```

#### Using `find` only

```bash
find . -iname "*java*"
```

### 18. List everything in the home directory

```bash
cd ~
ls -altrh
```

### About Flags

* `-a` → Show hidden files
* `-l` → Long listing format
* `-t` → Sort by time
* `-r` → Reverse sort
* `-h` → Human-readable file sizes

### 19. Get last 30 lines and word counts

```bash
tail -n 30 harrypotter.txt                 # Show last 30 lines
```

```bash
grep -oi "harry" harrypotter.txt | wc -l  # Count occurrences of "harry"
```

```bash
grep -oi "magic" harrypotter.txt | wc -l  # Count occurrences of "magic"
```

## Questions

### 1. What is the difference between a service and an application?

* **Application** → Program directly used by users (Firefox, VS Code)
* **Service** → Background process that supports system(nginx, sshd)

---

### 2. What are these wildcards/symbols: `~`, `.`, `..`, `*`, `?`

```text
~   → Home directory
.   → Current directory
..  → Parent directory
*   → Match any number of characters
?   → Match exactly one character
```

Examples:

```bash
ls *.txt        # All .txt files
ls file?.txt    # file1.txt, file2.txt
```

---

### 3. What are the different flags for `kill`? Why do we use `kill -9`?

```bash
kill PID        # Default terminate signal
kill -9 PID     # Force kill process
kill -15 PID    # Graceful termination (default)
kill -STOP PID  # Pause process
kill -CONT PID  # Resume process
```

* `kill -9` sends `SIGKILL`
* Used when a process does not stop normally
* Process is terminated immediately by the kernel

---

### 4. Explain file permissions. `chmod` and `chown` commands

### Permissions

```text
r = Read
w = Write
x = Execute
```

```text
User   Group   Others
```

Example:

```text
755 = rwxr-xr-x
644 = rw-r--r--
```

### Commands

```bash
chmod 755 file.txt          # Change permissions
chmod u+x script.sh         # Add execute permission

chown user file.txt         # Change owner
chown user:group file.txt   # Change owner and group
```

---

### 5. Usage of `Ctrl + R`, arrow keys, and tab autocompletion

```text
Ctrl + R  → Reverse search previous commands
↑ ↓       → Navigate command history
Tab       → Auto-complete commands/files
```
