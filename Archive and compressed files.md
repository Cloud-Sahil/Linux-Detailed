# 📦 Archive & Compression in Linux

## 📌 Overview
Archiving म्हणजे multiple files एकाच file मध्ये pack करणे (tar),  
आणि Compression म्हणजे file size कमी करणे (gzip, bzip2, xz).

---

## 🗂️ 1. Archive (tar)

### 🔹 Common Flags

| Flag | Meaning |
|------|--------|
| -c   | Create archive |
| -v   | Verbose (show progress) |
| -x   | Extract archive |
| -f   | File name |
| -t   | List archive contents |
| -C   | Extract to specific directory |

---

### 🔹 Syntax
```sh
tar -<flags> <archive-name>.tar <source>
