# Linux User Management

> User management means creating, modifying, deleting users and controlling their access/permissions in a Linux system.

---

## User Types

| Type | Home Dir | Prompt | UID Range | Access |
|---|---|---|---|---|
| Local user | /home/username | `$` | 1000–65000 | Limited |
| Super user (root) | /root | `#` | 0 | Full admin |
| System/service user | varies | no login | 1–499 | Service tasks only |

- **Local user** — regular human users; daily use accounts.
- **Super user** — root; complete control over the system. UID is always `0`.
- **System user** — created by the OS for services like `nginx`, `www-data`, `mysql`. No interactive login.

---

## 1. Creating Users

### `useradd` — scripting / non-interactive

| Command | Description |
|---|---|
| `useradd username` | Create user (no home dir by default) |
| `useradd -m username` | Create user WITH home directory `/home/username` |
| `useradd -m -s /bin/bash username` | Create user with home + bash shell |
| `useradd -m -g groupname username` | Create user and assign to a primary group |

### `adduser` — interactive (asks for password, name etc.)

```bash
adduser sita
# prompts for password, full name, phone, etc.
```

> **Tip:** Use `adduser` when setting up manually. Use `useradd` inside shell scripts for automation.

**Examples:**

```bash
useradd -m ram
# creates user "ram" + creates /home/ram

useradd -m -s /bin/bash -g developers arjun
# creates arjun with home dir, bash shell, in "developers" group
```

---

## 2. Setting Passwords

### `passwd` — set or change a user's password

| Command | Description |
|---|---|
| `passwd username` | Set password for user (run as root) |
| `passwd` | Change your own password |
| `passwd -l username` | Lock a user account |
| `passwd -u username` | Unlock a user account |

**Examples:**

```bash
passwd ram
# prompts: New password: ****

passwd -l ram
# locks ram — user cannot login until unlocked
```

---

## 3. Switching Users / Logging In

### `su` — switch user in current terminal

| Command | Description |
|---|---|
| `su username` | Switch to user (keeps current environment) |
| `su - username` | Switch + load user's full environment (recommended) |
| `su -` | Switch to root with full root environment |

> **Always use `su - username`** (with the dash). Without it, PATH and HOME may not be set correctly.

**Examples:**

```bash
su - ram
# switch to user ram (prompts for ram's password)

su -
# switch to root (prompts for root password)

exit
# return to the previous user
```

---

### `sudo -i` — become root using your own password

| Command | Description |
|---|---|
| `sudo -i` | Open interactive root shell (uses YOUR password) |
| `sudo command` | Run a single command as root |
| `sudo -u user command` | Run a command as a specific user |

> **`sudo -i` vs `su -`:** `sudo` uses YOUR password. `su` uses ROOT's password. In Ubuntu, root has no password by default — always use `sudo`.

**Examples:**

```bash
sudo -i
# become root (enter your own password)

sudo useradd -m newuser
# run useradd as root without fully switching to root

exit
# return to your normal user from root
```

---

## 4. Group Management

### `groupadd` — create a group

```bash
groupadd developers
# creates group "developers"

groupadd -g 1050 devops
# creates group with specific GID 1050
```

---

### `gpasswd` — manage group passwords and members

| Command | Description |
|---|---|
| `gpasswd groupname` | Set a password for the group |
| `gpasswd -a user groupname` | Add user to group |
| `gpasswd -d user groupname` | Remove user from group |
| `gpasswd -A user groupname` | Make user the group administrator |

**Examples:**

```bash
gpasswd developers
# set a password for "developers" group

gpasswd -a ram developers
# add user ram to the developers group

gpasswd -d ram developers
# remove ram from the developers group
```

---

### `usermod` — modify existing user's group/settings

| Command | Description |
|---|---|
| `usermod -aG groupname user` | Add user to a group (keeping existing groups) |
| `usermod -g groupname user` | Change user's primary group |
| `usermod -l newname oldname` | Rename a user |

> **Always use `-aG`** (append + group). Without `-a`, it replaces ALL existing group memberships!

**Examples:**

```bash
usermod -aG sudo ram
# give ram sudo (admin) privileges

usermod -aG developers,devops ram
# add ram to multiple groups at once
```

---

## 5. Deleting Users and Groups

### `userdel` — delete a user

| Command | Description |
|---|---|
| `sudo userdel username` | Delete user (home directory remains) |
| `sudo userdel -r username` | Delete user AND remove home dir + mail spool |

> Use `-r` to fully clean up. Without `-r`, files in `/home/username` remain on disk.

```bash
sudo userdel ram
# deletes user ram (files in /home/ram still exist)

sudo userdel -r ram
# deletes user ram AND removes /home/ram completely
```

---

### `groupdel` — delete a group

```bash
sudo groupdel developers
# deletes the "developers" group
```

> You cannot delete a group that is the **primary group** of any existing user. Change or remove those users first.

---

## 6. Inspecting Users & Groups

| Command | What it shows |
|---|---|
| `ls /home` | List all user home directories |
| `cat /etc/passwd` | All users: username, UID, GID, home, shell |
| `cat /etc/group` | All groups and their members |
| `id username` | User's UID, GID, and all group memberships |
| `whoami` | Currently logged-in user |
| `groups username` | All groups a user belongs to |
| `w` | Who is logged in + their activity |
| `last` | Recent login history |

**Examples:**

```bash
id ram
# uid=1001(ram) gid=1001(ram) groups=1001(ram),27(sudo)

cat /etc/passwd | grep ram
# ram:x:1001:1001::/home/ram:/bin/bash

groups ram
# ram : ram sudo developers
```

---

## Quick Workflow — Full User Setup Example

```bash
# 1. Create user with home dir
useradd -m -s /bin/bash ram

# 2. Set password
passwd ram

# 3. Create a group
groupadd developers

# 4. Add user to group
usermod -aG developers ram

# 5. Verify
id ram
# uid=1001(ram) gid=1001(ram) groups=1001(ram),1002(developers)

# 6. Switch to new user and test
su - ram

# 7. Return to original user
exit

# --- Cleanup ---
sudo userdel -r ram
sudo groupdel developers
```

---

## Quick Reference Summary

| Command | Purpose |
|---|---|
| `useradd -m username` | Create user with home directory |
| `adduser username` | Interactive user creation |
| `passwd username` | Set/change user password |
| `su - username` | Switch to another user |
| `sudo -i` | Become root (using your password) |
| `exit` | Return to previous user |
| `ls /home` | Check existing home directories |
| `groupadd groupname` | Create a new group |
| `gpasswd -a user group` | Add user to a group |
| `usermod -aG group user` | Add user to group (keep existing) |
| `sudo userdel -r username` | Delete user + home directory |
| `sudo groupdel groupname` | Delete a group |
| `id username` | Show user's UID, GID, groups |
