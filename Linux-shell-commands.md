# 🐧 Linux Commands — Detailed Reference Guide

> **Byte Units Quick Reference**
>
> | Unit | Full Name | Size |
> |------|-----------|------|
> | `1 bit` | Binary digit | 0 or 1 |
> | `1 byte` | — | 8 bits |
> | `1 KB` | Kilobyte | 1,000 bytes |
> | `1 KiB` | Kibibyte | 1,024 bytes |
> | `1 MB` | Megabyte | 1,000 KB |
> | `1 GB` | Gigabyte | 1,000 MB |

---

## 1. `hostname` — Check Machine Name

**What it does:** Displays the name of your computer/server on the network.

```bash
hostname
```

**Example Output:**
```
ubuntu-server
```

> 💡 This is how your machine is identified on a network. Useful in SSH sessions to confirm which server you're on.

---

## 2. `pwd` — Present Working Directory

**What it does:** Shows the full path of the directory you are currently in.

```bash
pwd
```

**Example Output:**
```
/home/john/documents
```

> 💡 `pwd` = **P**rint **W**orking **D**irectory. Always use this when unsure of your current location in the filesystem.

---

## 3. `$` — Local User Prompt Symbol

**What it does:** The `$` symbol in the terminal means you are logged in as a **normal (non-root) user**.

```bash
john@ubuntu:~$    ← Normal user
root@ubuntu:~#    ← Root (admin) user
```

> ⚠️ If you see `#`, you are the root user — commands run here have full system access. Be very careful!

---

## 4. `lscpu` — Check CPU Information

**What it does:** Displays detailed information about your CPU — architecture, cores, threads, speed, etc.

```bash
lscpu
```

**Example Output:**
```
Architecture:        x86_64
CPU(s):              4
Thread(s) per core:  2
Core(s) per socket:  2
Model name:          Intel(R) Core(TM) i5-8250U CPU @ 1.60GHz
CPU MHz:             1600.000
Cache L3:            6144 KB
```

---

## 5. `lscpu | less` — Scrollable CPU Info

**What it does:** Pipes the `lscpu` output into `less` so you can scroll through it page by page.

```bash
lscpu | less
```

**Navigation Keys:**

| Key | Action |
|-----|--------|
| `↑ / ↓` | Scroll one line up/down |
| `Space` | Next page |
| `b` | Previous page |
| `/keyword` | Search for a word |
| `q` | Quit |

> 💡 The `|` symbol is called a **pipe** — it sends the output of one command as input to another.

---

## 6. `q` — Quit

**What it does:** Exits interactive viewers like `less`, `man`, `top`, and `vim`.

```bash
# When inside less or man, just press:
q
```

---

## 7. `free` — Check Memory (RAM)

**What it does:** Shows total, used, and available RAM and Swap memory.

```bash
free
```

### Options:

| Command | Unit | Description |
|---------|------|-------------|
| `free -k` | Kilobytes | Output in KB |
| `free -m` | Megabytes | Output in MB |
| `free -g` | Gigabytes | Output in GB |
| `free -h` | Auto | Human-readable (best for quick reading) |

**Example Output (`free -h`):**
```
              total        used        free      shared  buff/cache   available
Mem:           7.6Gi       2.1Gi       3.4Gi       312Mi       2.1Gi       4.9Gi
Swap:          2.0Gi          0B       2.0Gi
```

**Column Meanings:**

| Column | Meaning |
|--------|---------|
| `total` | Total installed RAM |
| `used` | RAM currently in use |
| `free` | RAM not used at all |
| `buff/cache` | RAM used by kernel for caching |
| `available` | RAM available for new processes |

---

## 8. Swap — Virtual Memory (Storage Attached to RAM)

**What it does:** Swap is disk space reserved to act as overflow RAM. When physical RAM is full, the OS moves inactive data to Swap.

```
RAM ──────► [Full!] ──────► Swap Space (on Disk)
```

**Check Swap:**
```bash
free -h           # Shows Swap row
swapon --show     # Detailed swap info
```

> ⚠️ Swap is much **slower** than RAM because it uses the hard drive. Heavy swap usage indicates you need more RAM.

---

## 9. `clear` — Clear the Terminal

**What it does:** Clears all visible text from the terminal screen.

```bash
clear
```

> 💡 Shortcut: `Ctrl + L` does the same thing instantly.

---

## 10. `cat` — Read File Content

**What it does:** Reads and prints the contents of a file directly in the terminal.

```bash
cat filename.txt
```

**Example:**
```bash
cat hello.txt
# Output:
Hello, World!
This is a Linux text file.
```

### Common Uses:

```bash
cat file.txt               # Read a single file
cat file1.txt file2.txt    # Read and combine two files
cat > newfile.txt          # Create a new file (type content, press Ctrl+D to save)
cat -n file.txt            # Show file with line numbers
```

---

## 11. `cat /etc/os-release` — Check OS Information

**What it does:** Displays information about the Linux distribution installed on the system.

```bash
cat /etc/os-release
```

**Example Output:**
```
NAME="Ubuntu"
VERSION="22.04.3 LTS (Jammy Jellyfish)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 22.04.3 LTS"
VERSION_ID="22.04"
HOME_URL="https://www.ubuntu.com/"
```

---

## 12. `uname` — Check Kernel Information

**What it does:** Displays information about the Linux kernel running on your system.

```bash
uname
# Output: Linux
```

### Options:

| Command | Description | Example Output |
|---------|-------------|----------------|
| `uname -a` | All kernel details | `Linux ubuntu 5.15.0-91-generic #101-Ubuntu SMP...` |
| `uname -r` | Kernel release/version ID | `5.15.0-91-generic` |
| `uname -v` | Kernel build version | `#101-Ubuntu SMP Tue Nov 14 13:30:08 UTC 2023` |

**`uname -a` Output Breakdown:**
```
Linux   ubuntu   5.15.0-91-generic   #101   SMP   Tue Nov 14   x86_64   GNU/Linux
  │       │              │              │     │         │          │           │
 OS   Hostname    Kernel version      Build  Type    Build Date  CPU Arch   OS Type
```

---

## 13. `man` — Manual Pages

**What it does:** Opens the built-in manual/documentation for any command.

```bash
man ls        # Manual for the ls command
man free      # Manual for the free command
man uname     # Manual for uname
```

**Navigation:**

| Key | Action |
|-----|--------|
| `Space` | Next page |
| `b` | Previous page |
| `/word` | Search for a term |
| `n` | Jump to next search result |
| `q` | Quit |

> 💡 When in doubt about a command, always check `man <command>` first.

---

## 14. `history` — View Command History

**What it does:** Lists all previously executed commands with line numbers.

```bash
history
```

**Example Output:**
```
  496  ls -la
  497  cd /home
  498  cat /etc/os-release
  499  uname -a
  500  history
```

### Useful Tricks:

```bash
history | grep "cat"    # Search history for commands containing "cat"
!!                       # Re-run the last command
!498                     # Re-run command number 498
history -c               # Clear all history
```

---

## 15. `date` — Check Date & Time

**What it does:** Displays the current system date and time.

```bash
date
# Output: Sat Apr 26 10:30:45 IST 2025
```

### Set the Date (requires sudo):
```bash
sudo date MMDDhhmm[[CC]YY]

# Example: Set to April 26, 2025 at 10:30
sudo date 042610302025
```

### Custom Formatting:
```bash
date "+%d/%m/%Y"         # 26/04/2025
date "+%H:%M:%S"         # 10:30:45
date "+%A, %B %d %Y"     # Saturday, April 26 2025
date "+%s"               # Unix timestamp (seconds since 1970)
```

---

## 16 & 17. `shutdown` — Shutdown Linux

**What it does:** Powers off or restarts the system, with optional delay and message.

```bash
shutdown           # Schedule shutdown in 1 minute (default)
shutdown now       # Shutdown immediately
shutdown -r now    # Restart immediately
shutdown -h +5     # Shutdown after 5 minutes
shutdown -c        # Cancel a scheduled shutdown
```

### With a Broadcast Message:
```bash
shutdown +10 "Server going down in 10 minutes for maintenance!"
# All logged-in users will see this message
```

---

## 18. `Ctrl + D` — Exit / Logout

**What it does:** Sends an EOF (End of File) signal — logs you out of the terminal or exits the current session.

```
Ctrl + D   →   Logs out / closes terminal session
```

> 💡 The `exit` command does the same thing.

---

## 19. `which` — Check Command Location

**What it does:** Shows the full file path of where a command is installed.

```bash
which python3
# Output: /usr/bin/python3

which ls
# Output: /bin/ls

which git
# Output: /usr/bin/git
```

> 💡 If a command is not installed, `which` returns no output. Use this to verify if a program exists on the system.

---

## 20. `who` — Check All Active Users

**What it does:** Lists all users currently logged into the system.

```bash
who
```

**Example Output:**
```
john     tty1         2025-04-26 09:00
alice    pts/0        2025-04-26 09:15 (192.168.1.10)
bob      pts/1        2025-04-26 10:00 (192.168.1.20)
```

| Column | Meaning |
|--------|---------|
| `john` | Username |
| `tty1` | Local terminal (physically at the machine) |
| `pts/0` | Remote/SSH terminal session |
| `(192.168.x.x)` | IP address of the remote user |

---

## 21. `uptime` — Check System Uptime

**What it does:** Shows how long the system has been running, number of users, and CPU load averages.

```bash
uptime
```

**Example Output:**
```
10:30:45 up 3 days, 4:15,  2 users,  load average: 0.15, 0.20, 0.18
```

**Output Breakdown:**

| Part | Meaning |
|------|---------|
| `10:30:45` | Current time |
| `up 3 days, 4:15` | System has been running for 3 days, 4 hours, 15 minutes |
| `2 users` | 2 users currently logged in |
| `load average: 0.15, 0.20, 0.18` | CPU load over last 1, 5, and 15 minutes |

> 💡 A load average **below the number of CPU cores** is healthy. Use `lscpu` to check how many cores you have.

---

## 22. `id` — Check User & Group Identity

**What it does:** Displays the User ID (UID), Group ID (GID), and all groups the current user belongs to.

```bash
id
```

**Example Output:**
```
uid=1000(john) gid=1000(john) groups=1000(john),4(adm),27(sudo),1001(docker)
```

| Term | Meaning |
|------|---------|
| `uid` | Unique User ID number |
| `gid` | Primary Group ID |
| `groups` | All groups the user belongs to |

### Additional Uses:
```bash
id username      # Check another user's identity
id -u            # Print only the UID
id -g            # Print only the GID
id -G            # Print all group IDs
```

---

## 📊 Quick Command Summary Table

| # | Command | Purpose |
|---|---------|---------|
| 1 | `hostname` | Show machine name |
| 2 | `pwd` | Show current directory path |
| 3 | `$` | Indicates normal (non-root) user |
| 4 | `lscpu` | Show CPU details |
| 5 | `lscpu \| less` | Scroll through CPU info |
| 6 | `q` | Quit any viewer (less/man) |
| 7 | `free -h` | Show RAM usage (human-readable) |
| 8 | Swap | Virtual memory stored on disk |
| 9 | `clear` | Clear terminal screen |
| 10 | `cat file` | Read file contents |
| 11 | `cat /etc/os-release` | Show OS information |
| 12 | `uname -a` | Show full kernel info |
| 13 | `man command` | Open command manual |
| 14 | `history` | List past commands |
| 15 | `date` | Show current date & time |
| 16-17 | `shutdown now` | Shutdown system immediately |
| 18 | `Ctrl + D` | Logout / exit terminal |
| 19 | `which cmd` | Show command install path |
| 20 | `who` | List all logged-in users |
| 21 | `uptime` | Show uptime and CPU load |
| 22 | `id` | Show user/group IDs |
