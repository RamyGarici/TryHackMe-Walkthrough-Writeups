# Linux Fundamentals Part 2

**Platform:** TryHackMe  
**Type:** Room  
**Difficulty:** Easy  
**Name:** Linux Fundamentals Part 2

------------------------------------------------------------------------

## Questions & Answers

### Introduction to Flags and Switches

Q: What directional arrow key would we use to navigate down the manual page?  
A: down

Q: What flag would we use to display the output in a "human-readable" way?  
A: -h

------------------------------------------------------------------------

### Filesystem Interaction Continued

Q: How would you create the file named "newnote"?  
A: touch newnote

Q: On the deployable machine, what is the file type of "unknown1" in "tryhackme's" home directory?  
A: ASCII text

Q: How would we move the file "myfile" to the directory "myfolder"?  
A: mv myfile myfolder

Q: What are the contents of this file?  
A: THM{FILESYSTEM}

------------------------------------------------------------------------

### Permissions 101

Q: On the deployable machine, who is the owner of "important"?  
A: user2

Q: What would the command be to switch to the user "user2"?  
A: su user2

------------------------------------------------------------------------

### Common Directories

Q: What is the directory path that would we expect logs to be stored in?  
A: /var/log

Q: What root directory is similar to how RAM on a computer works?  
A: /tmp

Q: Name the home directory of the root user  
A: /root

---

## Notes

### SSH (Secure Shell)

- **SSH:** A protocol used to communicate between devices in an encrypted form.
- Any input sent in a human-readable format is encrypted for traveling over a network and decrypted once it reaches the remote machine.
- **Command syntax:** `ssh username@ip`

------------------------------------------------------------------------

### Flags and Switches

- Commands perform their default behavior unless modified by flags or switches.
- `ls`: Shows content of the working directory (excluding hidden files).
- `ls -a` or `ls --all`: Shows all files, including hidden ones.
- `ls --help`: Lists possible options and definitions for the command.
- `man [command]`: Opens the manual page of the specific command.

------------------------------------------------------------------------

### Filesystem Interaction

- `touch`: Creates an empty file (e.g., `touch newnote`).
- `mkdir`: Makes a new directory.
- `cp`: Copies a file or folder into another one.
- `mv`: Moves a file/folder to a destination, or renames it (e.g., `mv myfile myfolder`).
- `rm`: Removes a file or folder.
- `rm -r`: Recursively removes a directory and all its contents.
- `file`: Determines and outputs the specific type of a file (e.g., ASCII text).

------------------------------------------------------------------------

### Permissions 101

#### Switching Users
- `su user2`: Switches to `user2`, but the current environment (working directory, environment variables) does not change.
- `su -l user2`: Resets the environment to reflect `user2`'s actual home directory setup.

#### Permission Triads & Octal Notation
Permissions are divided into three tiers: **Owner**, **Group**, and **Others**.
- **r** (Read) = `4`
- **w** (Write) = `2`
- **x** (Execute) = `1`

*Examples:*
- `rwxr-xr-x` $\rightarrow$ `755`: Owner can do everything (7); Group and Others can only read and execute (5).
- `chmod 750 test.txt`: Changes permissions so the Owner can do everything (7), Group can read and execute (5), and Others have no permissions (0).

------------------------------------------------------------------------

### Common Directories

- **/etc**: One of the most important root directories. Used to store system files and configurations used by the OS.
  - `sudoers` file: Contains users and groups with permissions to run `sudo` commands as root.
  - `passwd` and `shadow` files: Stores user accounts and their passwords hashed in SHA-512.
- **/var**: Stores variable data that is frequently accessed or written to by running services and apps.
  - `/var/log`: Standard location for system and application log files.
- **/root**: The specific home directory for the `root` system user (administrator).
- **/tmp**: A temporary, volatile directory used to store transient data. It acts similarly to RAM; its entire content is cleared out once the computer restarts.
