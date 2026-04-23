# Verify User Management Changes
1. tail -(no.) /etc/passwd -----------> to check user detail
 - (tail --------> to check last line of file)
2. tail -(no.) /etc/shadow -----------> user's password detail
3. tail -(no.) /etc/group ----------> group details
4. tail -(no.) /etc/gshadow ------------> group password

**/etc/skel (.bash-logout, bashrc, .profile)** ------> these files get copied into user's home dir.

---
## 1. /etc/passwd 

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
 
  - useradd -u 2002 -g 5001 -c "hii" -m -s /bin/bash adii

 to modify the user ---------
  - usermod <flag> <username>
 
 1. echo $SHELL ------------------> to check shell
 2. id --------------------> to show id
 3. usermod -l (new name) (old name) ----------> modify user name

## 2. /etc/shadow

```sh
sahilya:$y$j9T$tOKoajv37Jwn.wD2gLf1s0$wixK8mPHqs/s8zq1tQcINU7ArDWg1cddfVaPG39grt/:20295:0:99999:7:::
```

 - username
 - encrypted password
 - days count from 1 jan 1970 till the last password change --- chage -d
 - min days --- chage -m
 - max days --- chage -M
 - warning days --- chage -W
 - date of expiry --- chage -I
 - password inactive --- chage -E
 - future use --- chage -F
