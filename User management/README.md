# User Management
**User management** means creating, modifying, deleting users and controlling their access/permissions in a Linux system.

---
## User Types
**1. local user** 
 - limited access
 - /home
 - /bin
 - $
 - range 1000-65000

**2. super user** 
 - admin access
 - /root
 - /sbin or bin
 - (#)
 - 0-499
 - root user - 0 (id)

**3. system/service user** 
 - perform specific service or system related task

---

1. adduser/useradd --------> to create user
2. su -(username) --------> to switch user
3. useradd -m (username) --------> to create user with its home
4. sudo -i --------> to switch into root user
5. exit --------> to logout from existing user
6. ls/home/ ---------> to check user's home dir.
7. passwd (username) ---------> to set password for user
8. groupadd (groupname) ---------> to create group
9. gpasswd (groupname) ----------> to create group password
10. sudo userdel (username) ----------> to delete username
11. sudo groupdel (groupname) ---------> to delete groupname
