# Verify User Management Changes
1. tail -(no.) /etc/passwd -----------> to check user detail
 - (tail --------> to check last line of file)
2. tail -(no.) /etc/shadow -----------> user's password detail
3. tail -(no.) /etc/group ----------> group details
4. tail -(no.) /etc/gshadow ------------> group password

**/etc/skel (.bash-logout, bashrc, .profile)** ------> these files get copied into user's home dir.

## 1. /etc/passwd ---------- fields
```sh
sahil:x:5001:5001: :/home/sahil:/bin/sh
```
   - username
   - linked to password
   - user id 
   - group id 
   - comment
   - user's home dir.
   - shell

 to make customized user ------------
	useradd -u 2002 -g 5001 -c "hii" -m -s /bin/bash adii

 to modify the user ---------
	usermod <flag> <username>
 
 1. echo $SHELL ------------------> to check shell
 2. id --------------------> to show id
 3. usermod -l (new name) (old name) ----------> modify user name
