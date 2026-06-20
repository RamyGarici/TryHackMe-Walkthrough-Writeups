# Windows PowerShell

**Platform:** TryHackMe  
**Type:** Room  
**Difficulty:** Easy  
**Name:** Windows PowerShell

------------------------------------------------------------------------

## Questions & Answers

### What is PowerShell

Q: What do we call the advanced approach used to develop PowerShell?  
A: Object-oriented

------------------------------------------------------------------------

### PowerShell Basics

Q: How would you retrieve a list of commands that start with the verb Remove? (Avoid the use of quotes in your answer)  
A: Get-Command -Name Remove*

Q: What cmdlet has its traditional counterpart echo as an alias?  
A: Write-Output

Q: What is the command to retrieve some example usage for the cmdlet New-LocalUser?  
A: Get-Help New-LocalUser -examples

------------------------------------------------------------------------

### Navigating the File System & Working with Files

Q: What cmdlet can you use instead of the traditional Windows command type?  
A: Get-Content

Q: What PowerShell command would you use to display the content of the "C:\Users" directory? (Avoid the use of quotes in your answer)  
A: Get-ChildItem -Path C:\Users

Q: How many items are displayed by the command described in the previous question?  
A: 4

------------------------------------------------------------------------

### Piping, Filtering and Sorting Data

Q: How would you retrieve the items in the current directory with size greater than 100? (Avoid the use of quotes in your answer)  
A: Get-ChildItem | Where-Object -Property Length -gt 100

------------------------------------------------------------------------

### System and Network Information

Q: Other than your current user and the default "Administrator" account, what other user is enabled on the target machine?  
A: p1r4t3

Q: This lad has hidden his account among the others with no regard for our beloved captain! What is the motto he has so bluntly put as his account's description?  
A: A merry life and a short one.

Q: Can you navigate the filesystem and find the hidden treasure inside this pirate's home? (Flag/Content)  
A: [Contenu du fichier big-treasure.txt après navigation]

------------------------------------------------------------------------

### Real-time System Analysis

Q: In the previous task, you found a marvellous treasure carefully hidden in the target machine. What is the hash of the file that contains it?  
A: 71FC5EC11C2497A32F8F08E61399687D90ABE6E204D2964DF589543A613F3E08

Q: What property retrieved by default by Get-NetTCPConnection contains information about the process that has started the connection?  
A: OwningProcess

Q: With this information and the PowerShell knowledge you have built so far, can you find the service name?  
A: p1r4t3-s-compass

------------------------------------------------------------------------

### Scripting

Q: What is the syntax to execute the command Get-Service on a remote computer named "RoyalFortune"? (Assume no credentials are needed and avoid the use of quotes)  
A: Invoke-Command -ComputerName RoyalFortune -ScriptBlock { Get-Service }

---

## Notes

### What is PowerShell

- **Definition:** A cross-platform task automation solution consisting of a command-line shell, a scripting language, and a configuration management framework. Built on top of the **.NET framework**.
- **Object-Oriented:** Unlike traditional text-based shells (like Bash or Cmd), PowerShell passes **objects** instead of plain text strings. This means outputs retain distinct properties and methods, allowing for advanced and flexible data manipulation.
- **Portability:** Originally exclusive to Windows, it has since expanded to macOS and Linux.

------------------------------------------------------------------------

### PowerShell Basics & Cmdlets

#### Ways to Launch PowerShell
1. **Start Menu:** Search for `powershell`.
2. **Run Dialog:** `Win + R` $\rightarrow$ `powershell`.
3. **File Explorer:** Type `powershell` in the address bar of any folder to open it directly in that path.
4. **Task Manager:** `File > Run new task` $\rightarrow$ `powershell`.
5. **Command Prompt:** Type `powershell` inside an active `cmd.exe` window.

#### Cmdlet Architecture (Verb-Noun)
PowerShell use **cmdlets** (command-lets) which follow a strict **Verb-Noun** naming convention making them highly intuitive:
- *Verb:* The action (e.g., `Get`, `Set`, `New`, `Remove`).
- *Noun:* The resource targeted (e.g., `Content`, `Location`, `Process`).
- *Examples:* `Get-Content` (reads a file), `Set-Location` (changes directory).

#### Essential Discovery Cmdlets
- `Get-Command`: Lists available commands. Use `-CommandType "Function"` or wildcards (`-Name Remove*`) to filter.
- `Get-Help`: Provides documentation. Appending `-examples` shows practical usage scenarios.
- `Get-Alias`: Lists all command shortcuts. 
  - `dir` $\rightarrow$ alias for `Get-ChildItem`
  - `cd` $\rightarrow$ alias for `Set-Location`
  - `echo` $\rightarrow$ alias for `Write-Output`

#### Package Management
- `Find-Module`: Searches online repositories for modules (supports wildcards, e.g., `*-Property "pattern*"`).
- `Install-Module`: Downloads and installs a module (e.g., `Install-Module -Name "PowerShellGet"`).

------------------------------------------------------------------------

### Navigating the File System

- `Get-ChildItem`: Lists files and folders. Accepts the `-Path` parameter. Defaults to the current directory if empty.
- `Set-Location`: Changes the working directory path (Counterpart to `cd`).
- `New-Item`: Creates a new file or directory.
- `Remove-Item`: Deletes files or folders (Counterpart to `rmdir` and `del`).
- `Copy-Item` / `Move-Item`: Copies or moves items within the filesystem.
- `Get-Content`: Displays file contents directly in the console (Counterpart to Unix `cat` or Cmd `type`).

------------------------------------------------------------------------

### Piping, Filtering and Sorting Data

- **The Pipeline (`|`):** Forwards the structural object output of one cmdlet directly into the input of the next.

#### Sorting & Selecting
- `Sort-Object`: Sorts objects by a specific property.
  - *Example (Sort by size):* `Get-ChildItem | Sort-Object Length`
  - *Example (Find biggest file):* `Get-ChildItem -Path [Path] | Sort-Object Length -Descending | Select-Object -First 1`
- `Select-Object`: Limits the number of objects returned or extracts specific object properties.
- `Select-String`: Searches for text patterns (`-Pattern`) within files. Supports regular expressions (Equivalent to `grep` or `findstr`).

#### Filtering with Where-Object
- `Where-Object`: Filters data based on conditional statements.
  - *Example (.txt files only):* `Get-ChildItem | Where-Object -Property "Extension" -eq ".txt"`

#### Comparison Operators
- `-eq` : Equal to
- `-ne` : Not equal to
- `-gt` : Greater than
- `-ge` : Greater than or equal to
- `-lt` : Less than
- `-le` : Less than or equal to

------------------------------------------------------------------------

### System & Network Administration

- `Get-ComputerInfo`: Gathers comprehensive system settings, OS configuration, hardware specs, and BIOS data (Counterpart to `systeminfo`).
- `Get-LocalUser`: Lists local accounts on the machine.
- `Get-NetIPConfiguration`: Displays network interfaces configurations (Counterpart to `ipconfig`).
- `Get-NetIPAddress`: Provides explicit details regarding configured IP addresses.

#### Real-time Monitoring & Hashes
- `Get-Process`: Monitors currently active processes.
- `Get-Service`: Retrieves the status of system services. Filters can be applied to find altered services: `Get-Service | Where-Object {$_.DisplayName -like "*pattern*"}`.
- `Get-NetTCPConnection`: Monitors active TCP network bindings. The property `OwningProcess` maps the connection back to its specific Process ID (PID).
- `Get-FileHash`: Computes cryptographic checksums (SHA-256 by default) to ensure file integrity or detect tampering.

------------------------------------------------------------------------

### PowerShell Scripting

- **Scripting:** Writing execution steps inside a `.ps1` text file to automate complex operations, mitigating human error and saving time.

#### Cyber Security & Admin Use Cases
- **Blue Team:** Log analysis, anomaly detection, extracting Indicators of Compromise (IOCs), automation of security scanning.
- **Red Team:** System enumeration, remote code execution (RCE), obfuscating code blocks to bypass detection controls.
- **SysAdmins:** Integrity baseline monitoring, infrastructure configuration state management.

#### Remote Management
- `Invoke-Command`: Runs commands or scripts on remote hosts.
  - *Remote Script:* `Invoke-Command -FilePath c:\scripts\test.ps1 -ComputerName Server01`
  - *Remote ScriptBlock:* `Invoke-Command -ComputerName RoyalFortune -ScriptBlock { Get-Service }`
