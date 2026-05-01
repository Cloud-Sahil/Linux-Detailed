# Advanced Linux Commands for DevOps Beginners

Let's discuss some more Linux commands which are kind of interesting and important.

**Topics Covered:**
1. find
2. sed
3. tr
4. adduser
5. File permissions (chmod)
6. awk

---

## 1. find

The `find` command is used to search for files and directories based on different conditions such as file type, name, size, and time of creation or modification. You can search files created or modified days ago or even minutes ago.

**Syntax:**
```
find <location> <options> <file_name_or_type>
```

**Examples:**

```bash
# Search for a file named code.txt in the home directory
find ~ -type f -name "code.txt"

# Search for a directory named india modified exactly 3 days ago
find / -type d -mtime 3 -name "india"

# Search for a directory named india modified within the last 3 days
find / -type d -mtime -3 -name "india"

# Search for a directory named india modified more than 3 days ago
find / -type d -mtime +3 -name "india"

# Search for a directory named india modified exactly 3 minutes ago (case-insensitive)
find / -type d -mmin 3 -iname "india"

# Search for a directory modified within the last 5 minutes
find / -type d -mmin -5 -iname "india"

# Search for a directory modified more than 5 minutes ago
find / -type d -mmin +5 -iname "india"
```

**Key Points:**

| Option   | Meaning                         |
|----------|---------------------------------|
| `-type f` | Files                          |
| `-type d` | Directories                    |
| `-mtime`  | Modification time (in days)    |
| `-mmin`   | Modification time (in minutes) |
| `-name`   | Case-sensitive search          |
| `-iname`  | Case-insensitive search        |

---

## 2. sed (Stream Editor)

The `sed` command is used to modify text in files without opening them in an editor. It works line by line, searches for patterns, and performs actions like replace, delete, insert, or print lines.

> **Note:** By default, `sed` does not change the original file. It only prints the modified output to the terminal. To permanently modify the file, use the `-i` (in-place) option. Be careful when using `-i` because it directly edits the file.

**Format:**
```
sed [OPTIONS] 'command' filename
```

**Examples:**

```bash
# Substitute text (replaces only the first occurrence in each line)
sed 's/old/new/' file.txt

# Global replacement (replaces all occurrences)
sed 's/dinesh/Dinesh/g' file.txt

# Edit the original file in-place
sed -i 's/dinesh/Dinesh/g' file.txt

# Print only the 2nd line
sed -n '2p' file.txt

# Print lines from 2 to 5
sed -n '2,5p' file.txt

# Replace globally and print only modified lines
sed -n 's/dinesh/Dinesh/gp' file.txt

# Delete the 2nd line
sed '2d' file.txt

# Delete lines from 2 to 20
sed '2,20d' file.txt

# Replace text only in line 2
sed '2s/dinesh/Dinesh/' file.txt
```

**Important Concept: Word Boundary**

Suppose the file contains:
```
engineer
engineering
```

If you run:
```bash
sed 's/engineer/engineering/' file.txt
```
Output:
```
engineering
engineeringing   ← incorrect!
```

This happens because `sed` finds `engineer` inside `engineering`. The correct way is:
```bash
sed 's/\<engineer\>/engineering/' file.txt
```
`\<` and `\>` ensure exact word matching — only `engineer` is replaced, not `engineering`.

**sed Option Reference:**

| Option | Explanation                                  |
|--------|----------------------------------------------|
| `s`    | Substitute the text                          |
| `g`    | Global edit                                  |
| `p`    | Print                                        |
| `-i`   | Make changes and edit the original file      |
| `d`    | Delete the line                              |
| `-n`   | Do not print the output automatically        |
| `a`    | Append after the line                        |
| `i`    | Insert before the line                       |
| `c`    | Change the existing line                     |

---

## 3. tr (Translate)

The `tr` command is used to translate or transform text that comes as output from another command. It works on standard input, so it is usually used with a pipe (`|`). `tr` does not read files directly — it processes text passed to it.

**Syntax:**
```
command | tr 'set1' 'set2'
```

**Examples:**

```bash
# Convert lowercase to uppercase
cat demo.txt | tr 'a-z' 'A-Z'

# Convert uppercase to lowercase
cat demo.txt | tr 'A-Z' 'a-z'

# Remove all numbers from output
cat demo.txt | tr -d '0-9'

# Replace multiple spaces with a single space
cat demo.txt | tr -s ' '
```

**When to use `tr`:**
- Change text case (upper ↔ lower)
- Remove unwanted characters
- Clean up output from other commands

---

## 4. adduser

The `adduser` command is a simple and user-friendly way to create a new user in Linux.

**Example:**
```bash
adduser dinesh
```

This command creates a user named `dinesh`. During the process, it will:
- Create the user
- Create a home directory
- Ask for and set the password
- Ask for basic user details (optional)

**`adduser` vs `useradd`:**

| `adduser`                            | `useradd`                              |
|--------------------------------------|----------------------------------------|
| High-level and interactive           | Low-level command                      |
| Easy to use                          | Requires more options                  |
| Prompts for password and user details | Does not set a password automatically |

When you use `useradd`, you must manually set the password using:
```bash
passwd username
# Example:
passwd dinesh
```

**When to use `adduser`:**
- When you want a quick and simple way to create users
- When you prefer an interactive setup

---

## 5. chmod (File Permissions)

`chmod` is an important Linux command used to change file or directory permissions. It controls who can read, write, or execute a file or folder.

**Permissions are given to:**
- **User** (owner)
- **Group**
- **Others**

**Syntax:**
```
chmod <permissions> filename
```

**Permission Symbols:**

| Symbol | Meaning    |
|--------|------------|
| `d`    | Directory  |
| `r`    | Read       |
| `w`    | Write      |
| `x`    | Execute    |
| `l`    | Link       |
| `-`    | File       |

A file listing looks like: `-rwxrwxrwx`
- First 3 characters → User permissions
- Next 3 → Group permissions
- Last 3 → Others permissions

**Symbolic method examples:**

```bash
# Give all permissions to user
chmod u+rwx file.txt

# Give all permissions to group
chmod g+rwx file.txt

# Give all permissions to others
chmod o+rwx file.txt

# Give read permission to others only
chmod o+r file.txt
```

**Numeric (Octal) method:**

Each permission has a value:
- Read (r) = 4
- Write (w) = 2
- Execute (x) = 1

```bash
# Give all permissions to everyone (4+2+1 = 7 for each)
chmod 777 file.txt

# Full permissions to user and group, execute only to others
chmod 771 file.txt

# Read and write to user only
chmod 600 file.txt
```

> **Quick Tip:** `chmod` is powerful. Giving `777` permissions can be dangerous, especially on servers. Use it only when necessary.

---

## 6. awk

`awk` is a text processing tool. Think of `awk` as a smart filter that:
- Reads line by line
- Splits each line into columns
- Lets you print, calculate, and format data

If `sed` edits text, `awk` understands **structure** (columns).

**When to use `awk` in real life:**
- Log analysis
- CSV files
- Command output (`ps`, `df`, `free`)
- Reports
- Monitoring scripts

**Basic syntax:**
```bash
awk 'pattern { action }' file
# Or:
command | awk 'pattern { action }'
```

If the pattern is true — the action runs.

**How `awk` works internally:**
For every line:
1. Read the line
2. Split it into fields
3. Execute action
4. Move to next line

**Fields and Records (Most Important):**

Default separator = space

| Symbol | Meaning             |
|--------|---------------------|
| `$0`   | Whole line          |
| `$1`   | First column        |
| `$2`   | Second column       |
| `$NF`  | Last column         |
| `NF`   | Number of fields    |
| `NR`   | Line number         |

**Example file: `data.txt`**
```
Dinesh Linux 50000
Ravi DevOps 60000
Kumar AWS 55000
```

```bash
# Print whole line
awk '{print $0}' data.txt

# Print specific columns
awk '{print $1, $3}' data.txt
# Output:
# Dinesh 50000
# Ravi 60000
# Kumar 55000

# Print with formatting
awk '{print "Name:", $1, "Salary:", $3}' data.txt

# Conditions: Print only salary > 55000
awk '$3 > 55000 {print $1, $3}' data.txt

# Print lines where department is DevOps
awk '$2 == "DevOps" {print $0}' data.txt
```

**BEGIN and END blocks:**

- `BEGIN` — runs once before reading the file
- `END` — runs once after the file ends

```bash
awk 'BEGIN {print "Report Start"}
{print $1, $3}
END {print "Report End"}' data.txt
```

Output:
```
Report Start
Dinesh 50000
Ravi 60000
Kumar 55000
Report End
```

**Field Separator (`-F`) for CSV files:**

```bash
# CSV file content:
# Dinesh,Linux,50000
# Ravi,DevOps,60000

awk -F',' '{print $1, $3}' file.csv
```

Here `-F` specifies the field separator. In this case it is a comma (`,`).

**Removing symbols with `gsub()`:**

If you have values like `40%`, `55%`, `80%`, you can remove the `%` symbol:

```bash
awk '{ gsub(/%/, "", $0); print }' file.txt
```

- `gsub()` stands for **global substitution**
- It searches for the `%` symbol and removes it from each line
- `$0` represents the entire line

Output:
```
40
55
80
```

> **Real-time use case:** This is commonly used when extracting memory or disk usage values, which are often shown as percentages (like `40%`). To process or calculate these values, the `%` symbol must be removed — and `gsub` makes this easy.

In short, `gsub` helps clean unwanted characters from command output or files, making the data usable for further processing.
