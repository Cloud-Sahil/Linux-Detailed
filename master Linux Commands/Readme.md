# Complete  Master Linux Commands 
---

## Section 1: Basic Linux Commands

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `ls` | List directory contents | `ls` | Lists files and directories in the current directory |
| `cd` | Change directory | `cd /path/to/directory` | Changes the current directory to the specified path |
| `pwd` | Print working directory | `pwd` | Displays the full path of the current directory |
| `mkdir` | Create a new directory | `mkdir newdir` | Creates a directory named "newdir" |
| `rmdir` | Remove a directory | `rmdir olddir` | Removes the directory named "olddir" if it is empty |
| `rm -r` | Remove directory recursively | `rm -rv olddir` | Removes the directory named "olddir" and its contents |
| `touch` | Create a new file | `touch newfile` | Creates an empty file named "newfile" |
| `echo` | Print text to terminal or file | `echo "Hello" > file.txt` | Writes "Hello" to file.txt, creating it if it doesn't exist |
| `cat` | Concatenate and display file contents | `cat file.txt` | Displays the contents of file.txt |
| `cp` | Copy files | `cp file1 file2` | Copies file1 to file2 |
| `mv` | Move or rename files or directories | `mv file1 file2` | Moves or renames file1 to file2 |
| `clear` | Clear the terminal screen | `clear` | Clears the terminal |
| `exit` | Exit the terminal | `exit` | Closes the current shell session |
| `rm` | Remove files | `rm file.txt` | Deletes file.txt |

---

## Section 2: Getting Help at the Command Line

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `man` | Display the manual for a command | `man ls` | Opens the manual page for the `ls` command |
| `man -k` | Search manual pages by keyword | `man -k list` | Searches for manual pages containing the keyword |
| `info` | Display information about a command | `info ls` | Opens the info page for the `ls` command |
| `--help` | Display help for a command | `ls --help` | Displays a brief help message with available options |
| `whatis` | Brief description of a command | `whatis ls` | Provides a one-line description of the `ls` command |
| `apropos` | Search for commands related to a keyword | `apropos list` | Searches for commands related to the keyword "list" |

---

## Section 3: Working with Directories

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `cd` | Change directory | `cd /var/log` | Changes the current directory to /var/log |
| `mkdir` | Create a new directory | `mkdir projects` | Creates a directory named "projects" |
| `rmdir` | Remove a directory | `rmdir projects` | Removes the "projects" directory if it is empty |
| `pwd` | Print working directory | `pwd` | Displays the full path of the current directory |
| `ls` | List directory contents | `ls -l` | Lists files with detailed information |
| `rm -rf` | Recursively remove a directory | `rm -rf directory` | Forcefully removes the directory and all its contents |

**Special directory symbols:**
- `.` — This directory
- `..` — The parent directory
- `$PATH` — Determines command search path
- `./command` — Execute command in this directory

---

## Section 4: Listing Files and Understanding Output

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `ls -l` | List files in long format | `ls -l` | Displays detailed info including permissions, ownership, size, and date |
| `ls -F` | Reveal file type | `ls -F` | Appends `/` for directories, `@` for links, `*` for executables |
| `ls -r` | Reverse order | `ls -r` | Lists files in reverse order |
| `ls -a` | List all files including hidden | `ls -a` | Shows all files including those starting with a dot |
| `ls -lh` | List files in human-readable format | `ls -lh` | Displays file sizes in human-readable format (e.g., MB) |
| `ls -ltr` | List files sorted by modification time (newest last) | `ls -ltr` | Lists files sorted by modification time, newest at the bottom |
| `ls -R` | List files recursively | `ls -R` | Lists all files and directories recursively |
| `ls -S` | Sort files by size | `ls -S` | Lists files sorted by size, largest first |
| `ls -t` | Sort files by modification time | `ls -t` | Lists files sorted by modification time, newest first |
| `tree -C` | Colourize output | `tree -C` | Displays directory tree with colours |
| `tree -d` | List directories only | `tree -d` | Shows only directories in tree format |

---

## Section 5: File Permissions

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `chmod` | Change file permissions | `chmod 755 file.txt` | Sets permissions to 755 (owner: rwx, group: rx, others: rx) |
| `chown` | Change file owner | `chown user file.txt` | Changes the owner and group of file.txt to "user" |
| `chgrp` | Change file group | `chgrp group file.txt` | Changes the group of file.txt to "group" |
| `umask` | Set default file permissions | `umask 022` | Sets default permissions for newly created files (755) |
| `ls -l` | List files with permissions | `ls -l` | Displays file permissions in the listing |

**Permission values (Numeric/Octal method):**

| Permission | Symbol | Value |
|------------|--------|-------|
| Read | `r` | 4 |
| Write | `w` | 2 |
| Execute | `x` | 1 |
| No permission | `-` | 0 |

**Permission string format:** `-rwxrwxrwx`
- 1st character: file type (`d` = directory, `-` = file, `l` = link)
- Characters 2–4: User (owner) permissions
- Characters 5–7: Group permissions
- Characters 8–10: Others permissions

```bash
chmod u+rwx file.txt    # Give all permissions to user
chmod g+rwx file.txt    # Give all permissions to group
chmod o+rwx file.txt    # Give all permissions to others
chmod o+r   file.txt    # Give read permission to others only
chmod 777   file.txt    # Give all permissions to everyone
chmod 771   file.txt    # Full permissions to user and group, execute only to others
chmod 600   file.txt    # Read and write to user only
```

---

## Section 6: Viewing Files and Editors

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `cat` | Display file contents | `cat file.txt` | Displays the entire contents of file.txt |
| `more` | View file contents one screen at a time | `more file.txt` | Displays file.txt one screen at a time |
| `less` | View file contents with forward and backward navigation | `less file.txt` | Displays file with forward and backward scrolling |
| `nano` | Simple text editor | `nano file.txt` | Opens file.txt in the nano editor for editing |

**vi / vim Editor:**

| Command | Description | Explanation |
|---------|-------------|-------------|
| `vi` | Text editor with two modes (command & insert) | Opens file.txt in the vi editor, starting in command mode |
| `vim` | Improved version of vi | Opens file.txt in vim, which has additional features over vi |
| `i` | Insert Mode | Enter insert mode to add text |
| `Esc` | Command Mode | Exit to command mode to execute commands |
| `:w` | Save file in vi/vim | Saves changes made to the file |
| `:q` | Quit vi/vim | Quits the editor without saving changes |
| `:wq` | Save and quit vi/vim | Saves changes and quits the editor |
| `:q!` | Quit vi/vim without saving | Discards changes and quits the editor |

---

## Section 7: Removing Files and Directories

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `rm` | Remove files | `rm file.txt` | Deletes file.txt |
| `rm -r` | Remove directory recursively | `rm -r dir` | Deletes the directory "dir" and its contents |
| `rm -i` | Prompt before every removal | `rm -i file.txt` | Asks for confirmation before deleting file.txt |
| `rm -f` | Force remove files or directories | `rm -f file.txt` | Deletes file.txt without prompting, ignoring non-existent files |

---

## Section 8: Copying and Moving Files

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `cp` | Copy files or directories | `cp file1 file2` | Copies file1 to file2 |
| `cp -r` | Copy directories recursively | `cp -r dir1 dir2` | Copies directory dir1 and its contents to dir2 |
| `mv` | Move or rename files or directories | `mv file1 file2` | Moves or renames file1 to file2 |
| `mv -i` | Prompt before overwrite | `mv -i file1 file2` | Prompts before overwriting file2 with file1 |
| `rename` | Rename multiple files | `rename 's/old/new/g' *` | Renames all files by replacing 'old' with 'new' |

---

## Section 9: Wildcards

| Wildcard | Description | Example | Explanation |
|----------|-------------|---------|-------------|
| `*` | Matches any number of characters | `ls *.txt` | Lists all .txt files in the directory |
| `?` | Matches a single character | `ls file?.txt` | Lists files like file1.txt, file2.txt |
| `[...]` | Matches any one of the enclosed characters | `ls file[123].txt` | Lists files file1.txt, file2.txt, file3.txt |
| `{...}` | Matches any of the patterns within braces | `ls file{1,2}.txt` | Lists files file1.txt, file2.txt |

---

## Section 10: Input and Output Redirection

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `>` | Redirect output to a file, overwriting it | `echo "Hello" > file.txt` | Writes "Hello" to file.txt, creating or overwriting it |
| `>>` | Append output to a file | `echo "Hello" >> file.txt` | Appends "Hello" to the end of file.txt |
| `<` | Redirect input from a file | `wc -l < file.txt` | Counts the lines in file.txt |
| `\|` | Pipe output to another command | `ls \| less` | Passes the output of `ls` into `less` |

---

## Section 11: Searching Files and Directories

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `find` | Search for files and directories | `find /home -name "*.txt"` | Finds all .txt files in /home and its subdirectories |
| `locate` | Quickly find files by name | `locate file.txt` | Searches the prebuilt database for file.txt |
| `grep` | Search text using patterns | `grep "hello" file.txt` | Searches for the string "hello" in file.txt |
| `grep -r` | Recursively search directories | `grep -r "hello" /home` | Recursively searches for "hello" in /home |

---

## Section 12: File Compression and Archiving

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `tar -cvf` | Archive files | `tar -cvf archive.tar file1 file2` | Creates an archive named "archive.tar" containing file1 and file2 |
| `tar -xvf` | Extract files from an archive | `tar -xvf archive.tar` | Extracts files from "archive.tar" |
| `tar -tvf` | List contents of an archive | `tar -tvf archive.tar` | Lists the contents of "archive.tar" |
| `gzip` | Compress files | `gzip file.txt` | Compresses file.txt and creates file.txt.gz |
| `gunzip` | Decompress files | `gunzip file.txt.gz` | Decompresses file.txt.gz and restores file.txt |
| `zip` | Compress files into a zip archive | `zip archive.zip file1 file2` | Creates a zip archive "archive.zip" containing file1 and file2 |
| `unzip` | Extract files from a zip archive | `unzip archive.zip` | Extracts files from "archive.zip" |

---

## Section 13: Transferring and Copying Files Over Network

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `scp` | Secure copy files between hosts | `scp file.txt user@remote:/path/to/destination/` | Copies file.txt to a remote server at the specified path |
| `rsync` | Sync files and directories between hosts | `rsync -avz file.txt user@remote:/path/to/destination/` | Synchronizes file.txt to the remote server, preserving permissions and compressing data |
| `sftp` | Secure file transfer protocol | `sftp user@remote` | Opens an SFTP session to the remote server for file transfers |
| `ftp` | File Transfer Protocol (less secure) | `ftp remote` | Connects to a remote FTP server to transfer files |

---

## Section 14: Customizing Shell Prompt

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `PS1` | Customize the shell prompt | `export PS1="\u@\h:\w\$ "` | Sets the shell prompt to display username, hostname, and current working directory |
| `PROMPT_COMMAND` | Command to execute before the prompt | `export PROMPT_COMMAND="date"` | Executes the date command before displaying the prompt |
| `~/.bashrc` | Shell configuration file for bash | `source ~/.bashrc` | Loads the settings from the .bashrc file, which may include prompt customizations |

---

## Section 15: Shell Aliases

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `alias` | Create a shortcut for a command | `alias ll='ls -la'` | Defines `ll` as a shortcut for `ls -la` |
| `unalias` | Remove the alias | `unalias ll` | Removes the alias `ll` |

---

## Section 16: Environment Variables

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `export` | Set or export environment variable | `export PATH=$PATH:/new/path` | Adds a path to the system PATH variable |
| `env` | Display all environment variables | `env` | Lists all currently set environment variables |
| `printenv` | Print environment variable values | `printenv PATH` | Shows the value of the PATH environment variable |

---

## Section 17: Process Management

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `ps aux` | Display current processes | `ps aux` | Lists all running processes with detailed information |
| `top` | Display a real-time view of processes | `top` | Provides a dynamic, real-time view of system processes |
| `jobs` | List background jobs | `jobs` | Lists all jobs that are running in the background |
| `fg` | Bring job to foreground | `fg %1` | Brings the job with ID 1 to the foreground |
| `killall` | Terminate processes by name | `killall process` | Sends a SIGTERM signal to all processes named "process" |
| `pkill` | Terminate processes by pattern | `pkill pattern` | Sends a SIGTERM signal to all processes matching the pattern |

---

## Section 18: Scheduling Repeated Jobs with Cron

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `crontab -e` | Manage cron jobs | `crontab -e` | Edit the current user's cron jobs |
| `crontab -l` | List cron jobs | `crontab -l` | List all scheduled cron jobs for the current user |
| `crontab -r` | Remove all cron jobs | `crontab -r` | Removes all cron jobs for the current user |

**Cron syntax:**

```
* * * * * command
│ │ │ │ │
│ │ │ │ └─ Day of week (0–6, Sunday = 0)
│ │ │ └─── Month (1–12)
│ │ └───── Day of month (1–31)
│ └─────── Hour (0–23)
└───────── Minute (0–59)
```

**Example:** `0 5 * * * /path/to/script` — Executes at 5:00 AM every day.

---

## Section 20: Shell History and Tab Completion

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `history` | Display command history | `history` | Lists the command history of the current session |
| `!10` | Execute command from history | `!10` | Repeats the command at history position 10 |
| `Tab` | Autocomplete commands and filenames | `ls /et` + Tab | Completes the path to `/etc` if it exists |

---

## Section 21: Installing Software

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `apt` | Debian-based package manager | `apt install package` | Installs the specified package on Debian-based systems |
| `yum` | Red Hat-based package manager | `yum install package` | Installs the specified package on Red Hat-based systems |
| `dnf` | Next-generation Red Hat package manager | `dnf install package` | Installs the specified package on Fedora-based systems |
| `rpm` | Install RPM package files | `rpm -ivh package.rpm` | Installs the RPM package file |

---

## Section 22: Linux Boot Process

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `dmesg` | Display boot messages | `dmesg` | Displays kernel ring buffer messages from boot |
| `systemctl` | Manage system services | `systemctl status sshd` | Displays the status of system services |
| `journalctl` | View system logs | `journalctl -b` | Shows logs from the current boot |
| `telinit 0` | Shutdown the system | `telinit 0` | Initiates system shutdown |
| `telinit 6` | Reboot the system | `telinit 6` | Initiates system reboot |

---

## Section 23: System Logging

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `journalctl` | Query and view system logs | `journalctl` | Displays the system logs |
| `tail` | View the end of a file | `tail /var/log/syslog` | Shows the last lines of syslog |
| `logrotate` | Rotate, compress, and mail system logs | `logrotate /etc/logrotate.conf` | Rotates logs as specified in the configuration file |
| `syslogd` | System logging daemon | `syslogd -d` | Starts the syslog daemon with debugging output enabled |
| `rsyslogd` | Enhanced version of syslogd | `rsyslogd -n` | Starts the rsyslog daemon in the foreground for troubleshooting |
| `logger` | Add entries to the system log | `logger "This is a test message"` | Writes a custom log message to syslog |
| `systemctl status` | Display status of systemd services | `systemctl status sshd` | Shows the status and recent log entries for the SSH service |

---

## Section 24: Disk Management

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `df` | Display disk space usage | `df -h` | Shows disk space usage in a human-readable format |
| `du` | Display disk usage of files and directories | `du -sh /path` | Shows the disk usage of the directory at path |
| `fdisk` | Partition table manipulator | `fdisk /dev/sda` | Opens fdisk to manage partitions on /dev/sda |

---

## Section 25: LVM — Logical Volume Manager

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `lvcreate` | Create a logical volume | `lvcreate -n mylv -L 10G vgname` | Creates a 10GB logical volume named "mylv" in volume group "vgname" |
| `vgcreate` | Create a volume group | `vgcreate vgname /dev/sdal` | Creates a volume group named "vgname" with /dev/sdal |
| `pvcreate` | Create a physical volume | `pvcreate /dev/sdal` | Initializes /dev/sdal for use by LVM |

---

## Section 26: Managing Users and Groups

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `useradd` | Add a new user | `useradd username` | Creates a new user named "username" |
| `usermod` | Modify user account | `usermod -aG group username` | Adds user "username" to the "group" |
| `userdel` | Delete a user | `userdel username` | Deletes the user "username" |
| `groupadd` | Add a new group | `groupadd groupname` | Creates a new group named "groupname" |
| `groupdel` | Delete a group | `groupdel groupname` | Deletes the group "groupname" |

---

## Section 27: TCP/IP Networking

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `ip addr` | Show IP addresses | `ip addr show` | Displays IP addresses and network interfaces |
| `ip route` | Show routing table | `ip route` | Displays the routing table |
| `ifconfig` | Display network interfaces | `ifconfig` | Displays network interfaces and their configurations |
| `netstat` | Network statistics | `netstat -tuln` | Shows active network connections and listening ports |

---

## Section 28 & 29: Networking and Network Troubleshooting

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `ping` | Test network connectivity | `ping google.com` | Sends ICMP echo requests to google.com to test connectivity |
| `ping -c 3` | Send limited ping packets | `ping -c 3 google.com` | Sends exactly 3 packets |
| `traceroute` | Trace the route packets take | `traceroute example.com` | Shows the route packets take to reach example.com |
| `nmap` | Network exploration tool | `nmap 192.168.1.1` | Scans the host for open ports and services |
| `netstat` | Network statistics | `netstat -an` | Displays all network connections and listening ports |
| `tcpdump` | Capture and display packets | `tcpdump` | Starts capturing packets on the default interface |
| `ss` | Investigate sockets | `ss -tuln` | Shows TCP and UDP sockets with detailed information |

---

## Section 20: User Switching

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `su` | Switch user | `su username` | Switches to the user with a login shell |
| `sudo` | Execute commands as another user | `sudo command` | Runs a command with root privileges |
| `sudo su` | Start a root shell | `sudo su` | Opens an interactive root shell |

---

## Section 30: Special Modes

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `setuid` | Run executable with file owner's privileges | `chmod u+s /path/to/file` | When set on a program like `/usr/bin/passwd`, any user executes it with the file owner's (usually root) privileges |
| `setgid` | Run executable with group privileges | `chmod g+s /path/to/file` | The program runs with the file's group permissions; directories inherit group ownership for new files |
| `Sticky Bit` | Prevent users from deleting others' files | `chmod +t /path/to/directory` | Commonly used in `/tmp`; users can write files but cannot delete or rename files owned by others |
| `single` | Single-user mode | `systemctl isolate rescue.target` | Switches to single-user mode for system maintenance |
| `rescue` | Rescue mode | `systemctl isolate rescue.target` | Boots into rescue mode for system recovery |

---

## Section 31: Shell Scripting

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `bash` | Execute a shell script | `bash script.sh` | Executes the shell script "script.sh" |
| `chmod +x` | Make script executable | `chmod +x script.sh` | Makes "script.sh" executable |
| `#!/bin/bash` | Shebang line | `#!/bin/bash` at top of file | Indicates that the script should be run with bash |

---

## Section 32: Finding Files and Directories

| Command | Description | Example | Explanation |
|---------|-------------|---------|-------------|
| `find` | Search for files and directories | `find /home -name "*.txt"` | Finds all .txt files in the /home directory |
| `locate` | Quickly find files by name | `locate file.txt` | Finds file.txt using a prebuilt database |
| `which` | Locate a command | `which ls` | Shows the path to the executable for `ls` |

---

## Section 33: Linux Directory Structure

| Directory | Description | Typical Contents |
|-----------|-------------|-----------------|
| `/` | Root directory; the top-level directory | All other directories are subdirectories of `/` |
| `/bin` | Essential user binaries and commands | Common commands like `ls`, `cp`, `mv`, `cat` |
| `/boot` | Static files for the bootloader | Kernel images, bootloader config files (e.g., `vmlinuz`, `initrd.img`) |
| `/dev` | Device files; represents hardware devices | Device files like `/dev/sda`, `/dev/tty0`, `/dev/null` |
| `/etc` | System-wide configuration files | Config files for system services and applications (e.g., `passwd`, `fstab`, `network`) |
| `/home` | User home directories | Individual user directories (e.g., `/home/user1`, `/home/user2`) |
| `/lib` | Shared libraries required by binaries in `/bin` and `/sbin` | System libraries and kernel modules |
| `/lib64` | Shared libraries for 64-bit systems | 64-bit system libraries |
| `/media` | Mount point for removable media | Mount points for USB drives, CDs, DVDs |
| `/mnt` | Mount point for temporarily mounted filesystems | Temporary mounts (e.g., external drives) |
| `/opt` | Optional application software packages | Add-on application software (e.g., `/opt/application`) |
| `/proc` | Virtual filesystem providing process and system information | Kernel and process info (e.g., `/proc/cpuinfo`, `/proc/meminfo`) |
| `/root` | Home directory for the root user | Root user's personal files and settings |
| `/run` | Runtime data; information about the system since the last boot | PID files, lock files |
| `/srv` | Data for services provided by the system | Data for services (e.g., `/srv/www` for web data) |
| `/sys` | Virtual filesystem for kernel and device information | Kernel and device information (e.g., `/sys/class`) |
| `/tmp` | Temporary files created by applications | Temporary files and directories |
| `/usr` | User-related programs and data | System-wide applications and files (`/usr/bin`, `/usr/lib`) |
| `/usr/bin` | Binaries for user commands | Executable files for user commands |
| `/usr/lib` | Libraries for user programs | Libraries used by binaries in `/usr/bin` |
| `/usr/sbin` | System binaries for administrative tasks | System management commands (e.g., `useradd`, `shutdown`) |
| `/usr/local` | Local software and scripts installed by the user | Locally installed software and scripts |
| `/var` | Variable data; files that change frequently | Logs, spool files, mail, and temporary files (`/var/log`, `/var/spool`) |
| `/var/log` | System and application log files | Log files for system and applications |
| `/var/spool` | Spool directories for tasks and services | Mail queues, print jobs |
| `/var/tmp` | Temporary files that need to persist between reboots | Persistent temporary files |
| `/var/lib` | Variable data used by applications and services | Database files, application state information |
| `/var/cache` | Cached data from applications | Cached files to speed up application performance |
| `/var/mail` | User mailboxes | Mail storage for individual users |
| `/var/run` | Runtime information | PID files, process runtime data |
| `/var/opt` | Variable data for applications installed in `/opt` | Application-specific data |

---

## Important Configuration Files

| File | Description | Example Content |
|------|-------------|-----------------|
| `/etc/passwd` | User account information | `root:x:0:0:root:/root:/bin/bash` |
| `/etc/shadow` | Hashed passwords and account expiration info | Password hashes and expiration info |
| `/etc/group` | User groups and their members | `root:x:0:` |
| `/etc/fstab` | Static filesystem information; lists filesystems and mount points | `/dev/sda1 / ext4 defaults 0 1` |
| `/etc/hosts` | Static table of IP addresses to hostnames | IP address and hostname mappings |
| `/etc/hostname` | Contains the system's hostname | The system's hostname |
| `/etc/resolv.conf` | DNS resolver configuration file | Nameserver IPs and domain search paths |
| `/etc/sysctl.conf` | Configuration file for kernel parameters | Kernel parameter settings (e.g., `net.ipv4.ip_forward=1`) |
| `/etc/network/interfaces` | Network interface configuration file (Debian-based) | Network interface settings (e.g., `auto eth0 iface eth0 inet dhcp`) |
| `/var/log/httpd/` | Apache HTTP server log directory | Apache access and error logs |
| `/var/log/nginx/` | Nginx web server log directory | Nginx access and error logs |
