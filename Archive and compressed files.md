# 📦 Archive & Compression in Linux
### Overview

Archiving means combining multiple files into a single file (using `tar`).
Compression reduces the file size (using tools like `gzip`, `bzip2`, `xz`).

---
## 🗂️ 1. Archive (`tar`)
🔹 Common Flags
| Flag | Description                     |
| ---- | ------------------------------- |
| `-c` | Create a new archive            |
| `-v` | Verbose (show progress)         |
| `-x` | Extract files                   |
| `-f` | Specify file name               |
| `-t` | List contents                   |
| `-C` | Extract to a specific directory |

### 🔹 Syntax
```sh
tar -<flags> <archive-name>.tar <source>
```
### 🔹 Examples
✔️ Create archive
```sh
tar -cvf opt.tar /opt
```
✔️ Extract in same location
```sh
tar -xvf opt.tar
```
✔️ Extract to different location
```sh
tar -xvf opt.tar -C /etc
```
✔️ List contents
```sh
tar -tvf opt.tar
```
---
## 🗜️ 2. Compression
🔹 Tools Comparison
| Tool  | Compression Level | Speed  | Extension | Decompress Command |
| ----- | ----------------- | ------ | --------- | ------------------ |
| gzip  | Low               | High   | `.gz`     | `gunzip`           |
| bzip2 | Medium            | Medium | `.bz2`    | `bunzip2`          |
| xz    | High              | Low    | `.xz`     | `unxz`             |
