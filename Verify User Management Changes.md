# Verify User Management Changes
1. tail -(no.) /etc/passwd -----------> to check user detail
 - (tail --------> to check last line of file)
2. tail -(no.) /etc/shadow -----------> user's password detail
3. tail -(no.) /etc/group ----------> group details
4. tail -(no.) /etc/gshadow ------------> group password

### /etc/skel (.bash-logout, bashrc, .profile) -- these files get copied into user's home dir.
