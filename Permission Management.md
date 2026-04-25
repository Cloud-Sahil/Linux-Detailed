# 🔐 Permission Management in Linux

## 📌 Overview
Permission management in Linux controls **who can read, write, and execute** files and directories.

---

## 🔢 Permission Types

| Symbol | Meaning  | Value |
|--------|----------|-------|
| r      | Read     | 4     |
| w      | Write    | 2     |
| x      | Execute  | 1     |
| -      | No Permission | 0 |

👉 Example:
- `rwx = 7` (4+2+1)
- `rw- = 6`
- `r-- = 4`

---

## 👤 Permission Levels

| Symbol | Description |
|--------|-------------|
| u      | User (Owner) |
| g      | Group        |
| o      | Others       |

---

## ⚙️ Commands

### 🔹 Change Permissions

```bash
chmod 777 file.txt
chmod u+rwx file.txt
chmod g-w file.txt
```
### 🔹 Change Ownership
```sh
chown user file.txt
chown user:group file.txt
```
### 🔹 Change Group
```sh
chgrp group file.txt
```
### 🧾 File Permission Format
```sh
-rw-r--r-- 1 root root 0 Apr 25 21:20 file.txt
```
#### Breakdown
| Field       | Meaning       |
| ----------- | ------------- |
| `-`         | File type     |
| `rw-r--r--` | Permissions   |
| `1`         | Link count    |
| `root`      | Owner         |
| `root`      | Group         |
| `0`         | File size     |
| Date        | Last modified |
| Name        | File name     |

### 📂 File Types
| Symbol | Type             |
| ------ | ---------------- |
| `-`    | Regular file     |
| `d`    | Directory        |
| `l`    | Symbolic link    |
| `b`    | Block device     |
| `c`    | Character device |
| `p`    | Pipe             |
| `s`    | Socket           |

### 🔗 Links in Linux
#### 🔹 Hard Link
```sh
ln file.txt hardlink.txt
```
 - Same inode
 - Cannot link directories
 - Link count increases
#### 🔹 Soft Link (Symbolic)
```sh
ln -s file.txt softlink.txt
```
 - Points to original file
 - Works across filesystems
 - If original deleted → link breaks
#### Link Count
 - File → usually `1`
 - Directory → `2` (default)
### Check File Size
```sh
du -sh file.txt
```
### Practical Example
```sh
# Create directory structure
mkdir -p cloud/rain/drop

# Create file
nano cloud/rain/drop/flower

# Create hard link
ln cloud/rain/drop/flower flower_hard

# Create symbolic link
ln -s cloud/rain/drop/flower flower_soft

# Check details
ls -l
```
