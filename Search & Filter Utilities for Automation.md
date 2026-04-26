# Linux Search & Filter Utilities (for Automation)

> Commands covered: `cat` · `grep` · `sort` · `uniq` · `find`

---

## 1. `cat` — Display, Create & Merge Files

| Command | Description |
|---|---|
| `cat file` | Display file contents |
| `cat -n file` | Display with line numbers |
| `cat file1 file2 > merged.txt` | Merge two files into one |
| `cat >> file` | Append text to file (Ctrl+D to save) |

**Examples:**

```bash
cat /etc/os-release
# prints OS information

cat file1.txt file2.txt > combined.txt
# merges file1 + file2 into combined.txt

cat -n /etc/passwd
# shows /etc/passwd with line numbers
```

---

## 2. `grep` — Search Text Patterns in Files or Output

| Command | Description |
|---|---|
| `grep "word" file` | Find lines containing "word" (case-sensitive) |
| `grep -i "word" file` | Case-insensitive search |
| `grep -c "word" file` | Count matching lines |
| `grep -ci "word" file` | Count matches (case-insensitive) |
| `grep -n "word" file` | Show line numbers of matches |
| `grep -v "word" file` | Invert — show lines NOT matching |
| `grep -r "word" dir/` | Recursive search inside a directory |

**Examples:**

```bash
grep "ubuntu" /etc/os-release
# find lines containing "ubuntu"

grep -i "ubuntu" /etc/os-release
# finds Ubuntu, UBUNTU, ubuntu (any case)

grep -c "ubuntu" /etc/os-release
# prints a count, e.g.: 3

ls /etc | grep cron
# list /etc entries that contain "cron"

ls /etc | grep "^m"
# list /etc entries starting with letter m
```

---

## 3. `sort` — Sort Lines Alphabetically or Numerically

| Command | Description |
|---|---|
| `sort file` | Sort ascending (A → Z) |
| `sort -r file` | Sort descending (Z → A) |
| `sort -n file` | Numeric sort (1, 2, 10 — not 1, 10, 2) |
| `sort -u file` | Sort and remove duplicates |
| `sort -k2 file` | Sort by the 2nd column/field |

**Examples:**

```bash
sort /etc/os-release
# alphabetical A→Z sort of file lines

sort -r /etc/os-release
# reverse Z→A sort

sort -n numbers.txt
# correctly sorts: 1 2 5 10 20

ls /etc | sort -r
# list /etc files in reverse alphabetical order
```

---

## 4. `uniq` — Remove or Count Duplicate Lines

> **Important:** `uniq` only removes *adjacent* (side-by-side) duplicates.
> Always use `sort` first to group duplicates together!

| Command | Description |
|---|---|
| `uniq file` | Remove consecutive duplicate lines |
| `uniq -c file` | Prefix each line with its occurrence count |
| `uniq -d file` | Show only duplicate lines |
| `uniq -u file` | Show only unique (non-duplicate) lines |

**Examples:**

```bash
sort fruits.txt | uniq
# unique fruit names (sort first!)

sort fruits.txt | uniq -c
# count how many times each fruit appears

sort fruits.txt | uniq | wc -l
# total count of unique words/lines

sort access.log | uniq -c | sort -rn | head -10
# top 10 most repeated lines (e.g. frequent IP addresses)
```

---

## 5. `find` — Search Files by Name, Time, Permission, or Owner

### By Name

```bash
find / -name "file.txt"          # search entire filesystem
find /root -name "*.log"         # all .log files in /root
find . -iname "file.txt"         # case-insensitive name search
```

### By Time

| Command | Description |
|---|---|
| `find /root -cmin -2` | Changed within the last 2 minutes |
| `find /root -cmin +2` | Changed more than 2 minutes ago |
| `find /root -ctime 1` | Changed exactly 1 day ago |
| `find /root -mmin -10` | *Modified* within last 10 minutes |
| `find /root -mtime -1` | Modified within the last 1 day |

> **`-cmin` vs `-mmin`:**
> - `-cmin` / `-ctime` → file **c**hanged (metadata, permissions)
> - `-mmin` / `-mtime` → file content **m**odified

### By Permission & Owner

```bash
find /root -perm 777             # files with exactly 777 permission
find /home -user john            # files owned by user "john"
find / -user root | less         # all root-owned files (paginated)
find /home/ram -user ram -perm 644
```

### By Type & Size

```bash
find / -type f                   # files only (not directories)
find / -type d                   # directories only
find / -size +10M                # files larger than 10 MB
find / -size +100M -type f       # large files eating disk space
```

### Practical Examples

```bash
find /root -name "*.conf"
# all config files in /root

find /root -cmin -5
# files changed in the last 5 minutes (useful after edits)

find /var/log -mtime -1 -name "*.log"
# log files modified in the last 24 hours

find /home/ram -user ram -perm 644
# ram's files with 644 permission
```

---

## Pipe Combinations (Automation Power)

Combining commands with `|` (pipe) makes them far more powerful:

```bash
# Filter /etc entries by keyword
ls /etc | grep cron

# Count unique words in a file
sort words.txt | uniq | wc -l

# Top 10 most repeated lines (e.g. in access logs)
sort access.log | uniq -c | sort -rn | head -10

# Search for "error" inside all .log files found by find
find /var/log -name "*.log" | xargs grep "error"

# Case-insensitive word frequency count
cat file.txt | tr 'A-Z' 'a-z' | sort | uniq -c | sort -rn

# Save grep results to a new file
grep "error" /var/log/syslog > errors.txt
```

---

## Quick Reference Summary

| Command | Primary Use |
|---|---|
| `cat` | Display / merge / create files |
| `grep` | Search for patterns in text |
| `sort` | Sort lines alphabetically or numerically |
| `uniq` | Remove or count duplicate lines (use after `sort`) |
| `find` | Locate files by name, time, permission, or owner |
