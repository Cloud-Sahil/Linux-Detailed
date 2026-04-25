# 📁 File Management in Linux

## 📌 Overview
File management in Linux means handling files and directories —  
👉 creating, viewing, editing, organizing, copying, moving, and deleting them.

---

## 📂 Basic Commands

### 🔹 Create Files

```bash
touch file.txt
touch file{1..10}.txt   # create multiple files
```
### 🔹 List Files
```sh
ls          # list files
ls -l       # detailed view
ls -a       # show hidden files
```
### 🔹 Remove Files & Directories
```sh
rm file.txt              # delete file
rm -v file.txt           # verbose delete
rm -r folder             # delete folder with content
rm -rf folder            # force delete (⚠️ dangerous)
rm file{1..5}.txt        # delete multiple files
```
### 🔹 Create Directories
```sh
mkdir folder
mkdir -p a/b/c
```
### 🔹 Remove Directories
```sh
rmdir folder             # delete empty folder
```
### 🔹 Change Directory
```sh
cd /home/user            # go to path
cd /                     # root directory
cd ..                    # one level up
cd ../..                 # two levels up
```
### 🔹 View File Content
```sh
cat file.txt             # display content
```
### 🔹 Create & Append Content
```sh
cat > file.txt           # overwrite content
cat >> file.txt          # append content
```
### 🔹 Copy Files
```sh
cp source.txt dest.txt
cp -r folder1 folder2    # copy directory
```
### 🔹 Move / Rename
```sh
mv old.txt new.txt       # rename
mv file.txt /home/user   # move file
```
### 🔹 Word Count
```sh
wc file.txt              # lines, words, bytes
```
---
