# Editors (Linux) 

 - **1. nano**
 - **2. pica**
 - **3. vi**
 - **4. vim**

---
## 1. Nano Editor
```sh
nano file.txt
```
### Example:
 - Write text directly
 - Press **Ctrl + O** → Save
 - Press **Ctrl + X** → Exit
---
## 2. Pico Editor
```sh
pico file.txt
```
### Example:
 - Edit file easily
 - Save → **Ctrl + O**
 - Exit → **Ctrl + X**
---
## vi Editor
```sh
vi file.txt
```
### Example:
 - i ------------------> Go to Insert Mode
 - Esc ------------------> Go out of insert mode / go to command mode
 - :w ------------------> To save the changes
 - :wq ------------------> To save & exit
 - :q! ------------------> To exit without save
## vim Editor
```sh
vim file.txt
```
### Example:
 - i ------------------> Go to Insert Mode
 - Esc ------------------> Go out of insert mode / go to command mode
 - :w ------------------> To save the changes
 - :wq ------------------> To save & exit
 - :q! ------------------> To exit without save

## 🔹Quick Comparison
| Editor | Difficulty  | Use              |
|--------|-------------|------------------|
| Nano   | Easy      | Beginners        |
| Pico   | Easy        | Simple editing   |
| vi     | Medium      | Default editor   |
| Vim    | Advanced  | Professionals    |

---
## Vim Editor Modes
### 1. Command mode (Default Mode)


1. yy -------------------> to copy the line (yanked)
2. (no.) yy -------------------> to copy multiple lines
3. p -------------------> to paste 
4. u -------------------> undo
5. yw ------------------->   to copy single words
6. (no.) yw ------------------>- to copy multiple words
7. dd -------------------> to delete particular line
8. (no.) dd -------------------> to delete multiple lines
9. dw -------------------> to delete single word
10. (no.) dw ------------------>-to delete multiple words
11. gg -------------------> go to top
12. (no.)gg ------------------->go to top (n = numbers)
13. G ------------------->go to last line
14. H -------------------> top of line which is visible
15. L ------------------->> bottom of line which is visible
16. M ------------------>> middle of line which is visible

### 2. Insert Mode (Typing Mode)

1. i   --------------------> to go to insert mode	
2. I   --------------------> to go to insert mode and cursor at the starting of a line
3. a   --------------------> to go to insert mode and cursor jump at next character
4. A   --------------------> to go to insert mode and cursor jump at end of the line
5. o   --------------------> to go to insert mode and adding a new line below (खाली )
6. O   --------------------> to go to insert mode and adding a new line upwards (वर)
7. s   --------------------> to go to insert mode and delete single character
8. S   --------------------> to go to insert mode and delete line 	
9. r   --------------------> to go to insert mode and replace the character 
10. R   --------------------> to go to insert mode and replace the line 

### 3. Command-Line Mode (Execute Mode)

1. :w  -------------->- to save the changes
2. :wq -------------->- to save and exit
     - :x  -------------->- to save and exit
     - :x! -------------->- to save and exit
     -  ZZ -------------->- to save and exit
     - :write | exit -------------->- save and exit
3. :q! -------------->- to exit without saving
4. :/(word to highlight) -------------->- to find the specific word or highlight it
5. :noh -------------->- to cancel highlighted word
6. :set no(num.) -------------->- to remove numbering
7. :set number -------------->- to add numbering
