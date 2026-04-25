# Editors 

## 📌 What are Text Editors?

Text editors in Linux are tools to **create, read, and modify files** directly from the terminal.  
Unlike Windows Notepad, Linux editors are **powerful, fast, and work over SSH** — no GUI needed.

---

## 🗂️ Editors Covered in This Section

| Editor | Difficulty | Best For |
|--------|------------|----------|
| [Nano](#1-nano-editor) | ⭐ Easy | Beginners, quick edits |
| [Pico](#2-pico-editor) | ⭐ Easy | Simple editing |
| [vi](#3-vi-editor) | ⭐⭐ Medium | Default on all Linux systems |
| [Vim](#4-vim-editor) | ⭐⭐⭐ Advanced | Professionals, power users |

---

## 1. Nano Editor

**Nano** is the **most beginner-friendly** terminal editor.  
All shortcuts are shown at the bottom of the screen — no memorization needed.

### Open / Create a File
```bash
nano file.txt
nano /etc/nginx/nginx.conf    # edit system config
nano newfile.txt              # creates file if not exists
```

### Nano Interface
```
GNU nano 7.2         file.txt

Hello, this is my file content.
I can type here directly!
█

^G Help   ^O Write Out   ^W Where Is   ^K Cut   ^T Execute
^X Exit   ^R Read File   ^\ Replace    ^U Paste  ^J Justify
```

### Essential Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl + O` | Save file (Write Out) |
| `Ctrl + X` | Exit |
| `Ctrl + W` | Search (Where Is) |
| `Ctrl + \` | Find and Replace |
| `Ctrl + K` | Cut line |
| `Ctrl + U` | Paste |
| `Ctrl + G` | Help |
| `Ctrl + C` | Show cursor position |
| `Alt + U` | Undo |
| `Alt + E` | Redo |
| `Ctrl + A` | Go to beginning of line |
| `Ctrl + E` | Go to end of line |
| `Ctrl + Y` | Page Up |
| `Ctrl + V` | Page Down |

### Practical Example
```bash
# Step 1: Open a file
$ nano myscript.sh

# Step 2: Type your content
#!/bin/bash
echo "Hello from nano!"

# Step 3: Save → Ctrl+O → Press Enter to confirm filename

# Step 4: Exit → Ctrl+X
```

### Nano with Line Numbers
```bash
# Open with line numbers
$ nano -l file.txt

# Or add to ~/.nanorc permanently
echo "set linenumbers" >> ~/.nanorc
```

---

## 2. Pico Editor

**Pico** (Pine Composer) is similar to Nano — also beginner-friendly.  
Nano was actually created as a free clone of Pico.

> 💡 On most modern systems, `pico` is just an alias for `nano`. If it's not installed:

```bash
# Install on Ubuntu/Debian
$ sudo apt install alpine-pico

# OR just use nano — they're nearly identical
```

### Open a File
```bash
pico file.txt
```

### Pico Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl + O` | Save |
| `Ctrl + X` | Exit |
| `Ctrl + W` | Search |
| `Ctrl + K` | Cut line |
| `Ctrl + U` | Paste |
| `Ctrl + G` | Help |

### Pico vs Nano — Key Differences

| Feature | Pico | Nano |
|---------|------|------|
| Undo | ❌ No | ✅ Yes (Alt+U) |
| Syntax highlight | ❌ No | ✅ Yes |
| Mouse support | ❌ Limited | ✅ Yes |
| Availability | Needs install | Pre-installed |

---

## 3. vi Editor

**vi** (Visual editor) is the **original Unix text editor**, available on **every** Linux/Unix system.  
Even if no other editor exists, `vi` will be there — essential for sysadmins.

### Open a File
```bash
vi file.txt
vi /etc/hosts         # edit system hosts file
vi +10 file.txt       # open at line 10
vi +/word file.txt    # open at first match of "word"
```

### The Two Modes of vi

vi has **two main modes** — this is what confuses beginners:

```
┌─────────────────────────────────────────┐
│           COMMAND MODE                  │
│   (default when you open vi)            │
│   Navigate, copy, delete, search        │
│                                         │
│   Press 'i' to go to INSERT MODE ──────►│
│◄─ Press 'Esc' to return                 │
│                                         │
│           INSERT MODE                   │
│   Type and edit text freely             │
└─────────────────────────────────────────┘
```

### Command Mode — Navigation
```bash
h    → move left
l    → move right
j    → move down
k    → move up

w    → jump forward one word
b    → jump backward one word
e    → jump to end of word

0    → go to beginning of line
$    → go to end of line
gg   → go to top of file
G    → go to bottom of file
```

### Command Mode — Editing
```bash
dd   → delete current line
yy   → copy (yank) current line
p    → paste below
P    → paste above
u    → undo
x    → delete character under cursor
r    → replace single character
```

### Insert Mode — Enter/Exit
```bash
i    → insert before cursor
a    → insert after cursor
o    → new line below and insert
O    → new line above and insert

Esc  → exit insert mode (back to command)
```

### Saving and Exiting
```bash
:w         → save
:q         → quit (only if no changes)
:wq        → save and quit
:q!        → quit WITHOUT saving (force)
:wq!       → save and quit (force)
```

### Practical Example
```bash
# Step 1: Open vi
$ vi notes.txt

# Step 2: Press 'i' to enter INSERT mode
# (You'll see -- INSERT -- at bottom)

# Step 3: Type your text
This is my note.

# Step 4: Press Esc to go back to COMMAND mode

# Step 5: Type :wq and press Enter to save and exit
:wq
```

---

## 4. Vim Editor

**Vim** (Vi IMproved) is a greatly enhanced version of vi.  
It adds syntax highlighting, plugins, undo history, multiple windows, and much more.

### Install Vim
```bash
# Ubuntu/Debian
$ sudo apt install vim

# CentOS/RHEL
$ sudo yum install vim

# Verify
$ vim --version
```

### Open a File
```bash
vim file.txt
vim +25 file.txt           # open at line 25
vim -R file.txt            # read-only mode
vim file1.txt file2.txt    # open multiple files
```

---

## 🔵 Vim's 4 Modes — Detailed

```
┌──────────────────────────────────────────────────────────┐
│                   NORMAL / COMMAND MODE                  │
│              (Default — where you start)                 │
│                                                          │
│    i/I/a/A/o/O/s/S/r/R  ─────────► INSERT MODE         │
│    v/V/Ctrl+V            ─────────► VISUAL MODE         │
│    :                     ─────────► COMMAND-LINE MODE   │
│                                                          │
│    All modes return to NORMAL with Esc                   │
└──────────────────────────────────────────────────────────┘
```

---

### Mode 1: Normal / Command Mode (Default)

This is where you **navigate and manipulate text**.

#### 📋 Copy (Yank), Paste, Delete

| Command | Action | Example |
|---------|--------|---------|
| `yy` | Copy current line | Copy line 5 |
| `3yy` | Copy 3 lines | Copy lines 5, 6, 7 |
| `yw` | Copy one word | Copy word at cursor |
| `3yw` | Copy 3 words | Copy next 3 words |
| `p` | Paste below cursor | Paste copied line |
| `P` | Paste above cursor | |
| `dd` | Delete current line | |
| `3dd` | Delete 3 lines | |
| `dw` | Delete one word | |
| `3dw` | Delete 3 words | |
| `x` | Delete character | Delete char under cursor |
| `X` | Delete char before | Backspace behavior |

#### 🧭 Navigation

| Command | Action |
|---------|--------|
| `h` | Move left |
| `l` | Move right |
| `j` | Move down |
| `k` | Move up |
| `w` | Next word |
| `b` | Previous word |
| `0` | Start of line |
| `$` | End of line |
| `gg` | Go to top of file |
| `G` | Go to last line |
| `5G` | Go to line 5 |
| `H` | Top of visible screen |
| `M` | Middle of visible screen |
| `L` | Bottom of visible screen |
| `Ctrl+D` | Scroll half page down |
| `Ctrl+U` | Scroll half page up |
| `Ctrl+F` | Scroll full page down |
| `Ctrl+B` | Scroll full page up |

#### ↩️ Undo / Redo

| Command | Action |
|---------|--------|
| `u` | Undo last action |
| `Ctrl+R` | Redo |
| `5u` | Undo last 5 actions |

---

### Mode 2: Insert Mode (Typing Mode)

Press these keys from **Normal mode** to enter insert mode:

| Key | Action | Where cursor goes |
|-----|--------|-------------------|
| `i` | Insert | Before cursor |
| `I` | Insert | Start of line |
| `a` | Append | After cursor |
| `A` | Append | End of line |
| `o` | New line below | New line below current |
| `O` | New line above | New line above current |
| `s` | Substitute char | Delete char, enter insert |
| `S` | Substitute line | Delete line, enter insert |
| `r` | Replace char | Replace one char, stay normal |
| `R` | Replace mode | Overwrite chars (like Insert key) |

```bash
# Example: Add text to end of every line
# Position cursor on line → Press A → type text → Esc
```

Press **`Esc`** to return to Normal mode.

---

### Mode 3: Command-Line Mode (Execute Mode)

Press **`:`** from Normal mode to enter this mode.

#### 💾 Saving & Exiting

| Command | Action |
|---------|--------|
| `:w` | Save (write) |
| `:wq` | Save and exit |
| `:x` | Save and exit |
| `:x!` | Save and exit (force) |
| `ZZ` | Save and exit (shortcut) |
| `:q!` | Exit WITHOUT saving |
| `:write \| exit` | Save and exit (verbose) |

#### 🔍 Search & Replace

```bash
# Search for a word (highlights all matches)
:/hello

# Search backwards
:?hello

# Go to next match
n

# Go to previous match
N

# Remove search highlight
:noh

# Replace first occurrence on current line
:s/old/new/

# Replace all occurrences on current line
:s/old/new/g

# Replace on lines 1 to 10
:1,10s/old/new/g

# Replace throughout entire file
:%s/old/new/g

# Replace with confirmation
:%s/old/new/gc
```

#### 🔢 Line Numbers

```bash
:set number        # Show line numbers
:set nonumber      # Hide line numbers
:set relativenumber  # Show relative line numbers
```

#### ➕ Other Useful Commands

```bash
:10                # Jump to line 10
:e file2.txt       # Open another file
:split file2.txt   # Horizontal split
:vsplit file2.txt  # Vertical split
:!ls               # Run shell command without leaving vim
:syntax on         # Enable syntax highlighting
:set tabstop=4     # Set tab width to 4 spaces
```

---

### Mode 4: Visual Mode (Selection Mode)

Press these from **Normal mode**:

| Key | Selection Type |
|-----|---------------|
| `v` | Character-by-character |
| `V` | Entire lines |
| `Ctrl+V` | Column/block selection |

```bash
# Example: Copy a block of lines
1. Press V (line visual mode)
2. Use j/k to select lines
3. Press y to copy
4. Move cursor to destination
5. Press p to paste
```

#### Visual Mode Operations
```bash
# After selecting text:
y    → copy selection
d    → delete selection
>    → indent right
<    → indent left
~    → toggle case
u    → lowercase
U    → uppercase
```

---

## ⚙️ Vim Configuration (`~/.vimrc`)

You can customize Vim by editing `~/.vimrc`:

```bash
$ vim ~/.vimrc
```

### Recommended `~/.vimrc` Settings

```vim
" Show line numbers
set number

" Enable syntax highlighting
syntax on

" Set tab width to 4 spaces
set tabstop=4
set shiftwidth=4
set expandtab

" Show cursor position at bottom
set ruler

" Highlight search results
set hlsearch

" Incremental search (find as you type)
set incsearch

" Ignore case in search
set ignorecase

" Auto-indent
set autoindent

" Show matching brackets
set showmatch

" Enable mouse support
set mouse=a

" Set color scheme
colorscheme desert
```

Apply without restarting:
```bash
:source ~/.vimrc
```

---

## 🏆 Vim Cheat Sheet — Quick Reference

```
┌────────────────────────────────────────────────────────┐
│                   VIM CHEAT SHEET                      │
├─────────────┬──────────────────────────────────────────┤
│ MODE SWITCH │                                          │
│ i           │ Insert before cursor                     │
│ I           │ Insert at line start                     │
│ a           │ Insert after cursor                      │
│ A           │ Insert at line end                       │
│ o           │ New line below                           │
│ O           │ New line above                           │
│ Esc         │ Back to Normal mode                      │
├─────────────┼──────────────────────────────────────────┤
│ NAVIGATE    │                                          │
│ gg / G      │ Top / Bottom of file                     │
│ H / M / L  │ Top / Middle / Bottom of screen          │
│ w / b       │ Next / Prev word                         │
│ 0 / $       │ Start / End of line                      │
├─────────────┼──────────────────────────────────────────┤
│ EDIT        │                                          │
│ yy / 3yy   │ Copy line / 3 lines                      │
│ dd / 3dd   │ Delete line / 3 lines                    │
│ dw / 3dw   │ Delete word / 3 words                    │
│ p / P       │ Paste below / above                      │
│ u / Ctrl+R  │ Undo / Redo                              │
├─────────────┼──────────────────────────────────────────┤
│ SAVE/EXIT   │                                          │
│ :w          │ Save                                     │
│ :wq or ZZ   │ Save and exit                            │
│ :q!         │ Exit without saving                      │
├─────────────┼──────────────────────────────────────────┤
│ SEARCH      │                                          │
│ /word       │ Search forward                           │
│ ?word       │ Search backward                          │
│ n / N       │ Next / Prev match                        │
│ :noh        │ Remove highlight                         │
│ :%s/a/b/g   │ Replace all 'a' with 'b'                │
└─────────────┴──────────────────────────────────────────┘
```

---

## 🔹 Full Comparison Table

| Feature | Nano | Pico | vi | Vim |
|---------|------|------|----|-----|
| Pre-installed | ✅ | ❌ | ✅ | Sometimes |
| Beginner friendly | ✅ | ✅ | ❌ | ❌ |
| Shortcuts on screen | ✅ | ✅ | ❌ | ❌ |
| Syntax highlighting | ✅ | ❌ | ❌ | ✅ |
| Multiple modes | ❌ | ❌ | ✅ | ✅ |
| Plugins support | ❌ | ❌ | ❌ | ✅ |
| Undo/Redo | ✅ | ❌ | Limited | ✅ |
| Split windows | ❌ | ❌ | ❌ | ✅ |
| Works over SSH | ✅ | ✅ | ✅ | ✅ |
| Speed | Fast | Fast | Very fast | Fast |
| Learning curve | Low | Low | Medium | High |

---

## 🧪 Practice Exercises

### Nano Practice
```bash
# 1. Create and edit a file in nano
nano practice.txt

# 2. Type some text, save (Ctrl+O), exit (Ctrl+X)

# 3. Search for a word
# Open file → Ctrl+W → type word → Enter

# 4. Find and replace
# Open file → Ctrl+\ → enter old word → new word
```

### Vim Practice
```bash
# 1. Open vim and try modes
vim practice.txt

# 2. Press i → type text → Esc → :wq

# 3. Practice navigation
# gg to go top, G to go bottom, /word to search

# 4. Practice yank and paste
# yy to copy line, p to paste it

# 5. Practice visual mode
# V → select 3 lines with j → y to copy → G → p to paste

# 6. Practice replace all
# :%s/hello/world/g
```

### Vimtutor — Built-in Tutorial
```bash
# Best way to learn vim!
$ vimtutor
```

---

## 🌟 Pro Tips

```bash
# Open file at specific line in vim
$ vim +42 file.txt

# Vim in read-only mode (safe to view system files)
$ vim -R /etc/passwd

# Compare two files side by side
$ vimdiff file1.txt file2.txt

# Record a macro in vim (automate repetitive edits)
# qa → start recording in register 'a'
# ... do edits ...
# q → stop recording
# @a → play macro
# 10@a → play macro 10 times
```

---

## ➡️ Back to Main

👉 [Back to Main README](../README.md)
