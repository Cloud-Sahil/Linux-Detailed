# Linux User Management — Verification & Configuration

> Files covered: `/etc/passwd` · `/etc/shadow` · `/etc/group` · `/etc/gshadow` · `/etc/skel`

---

## Verification Commands (tail)

`tail` shows the **last N lines** of a file — useful after adding a user to confirm it was created correctly.

```bash
tail -3 /etc/passwd       # last 3 lines of passwd (user accounts)
tail -3 /etc/shadow       # last 3 lines of shadow (password hashes)
tail -3 /etc/group        # last 3 lines of group (group list)
tail -3 /etc/gshadow      # last 3 lines of gshadow (group passwords)
```

---

## /etc/skel — Skeleton Directory

When a new user is created with `-m` (make home dir), Linux copies the files from `/etc/skel` into the new user's home directory automatically.

```bash
ls -a /etc/skel
# .bash-logout   .bashrc   .profile
```

| File | Purpose |
|---|---|
| `.bashrc` | Shell config loaded on every interactive shell session |
| `.profile` | Loaded on login — sets PATH and env variables |
| `.bash-logout` | Runs when user logs out |

---

## 1. `/etc/passwd` — User Account Details

Each line represents one user account.

### Format

```
sahil : x : 5001 : 5001 : comment : /home/sahil : /bin/sh
  1     2    3      4       5           6              7
```

| Field | Meaning |
|---|---|
| 1 — `sahil` | Username |
| 2 — `x` | Password placeholder (actual password is in `/etc/shadow`) |
| 3 — `5001` | User ID (UID) |
| 4 — `5001` | Primary Group ID (GID) |
| 5 — comment | Description / full name (optional) |
| 6 — `/home/sahil` | User's home directory |
| 7 — `/bin/sh` | Default login shell |

### Creating a Custom User

```bash
useradd -u 2002 -g 5001 -c "Developer Account" -m -s /bin/bash adii
```

| Flag | Meaning |
|---|---|
| `-u 2002` | Set UID to 2002 |
| `-g 5001` | Set primary group to GID 5001 |
| `-c "Developer Account"` | Add a comment/description |
| `-m` | Create home directory automatically |
| `-s /bin/bash` | Set default shell to bash |

### Modifying a User

```bash
usermod <flag> <username>

usermod -l aditya adii          # rename user "adii" to "aditya"
usermod -s /bin/bash sahil      # change shell to bash
usermod -u 3001 sahil           # change UID to 3001
usermod -c "New Comment" sahil  # update comment field
```

### Useful Checks

```bash
echo $SHELL       # check current shell (e.g. /bin/bash)
id                # show current user's UID, GID, and groups
id sahil          # show UID, GID, groups for user "sahil"
```

---

## 2. `/etc/shadow` — Encrypted Password Details

Only readable by root. Stores password hashes and password aging policy.

### Format

```
sahilya : $y$j9T$tOKo...grt/ : 20295 : 0 : 99999 : 7 : : :
   1             2               3     4     5      6   7  8  9
```

| Field | Meaning |
|---|---|
| 1 — `sahilya` | Username |
| 2 — `$y$...` | Encrypted (hashed) password |
| 3 — `20295` | Days since Jan 1, 1970 of last password change |
| 4 — `0` | Minimum days before password can be changed |
| 5 — `99999` | Maximum days before password must be changed |
| 6 — `7` | Days of warning before password expires |
| 7 — (empty) | Days after expiry before account is disabled (inactive) |
| 8 — (empty) | Absolute account expiry date (days since epoch) |
| 9 — (empty) | Reserved for future use |

### Managing Password Aging with `chage`

```bash
chage -M 90 -W 10 -I 7 sahilya
# max 90 days, warn 10 days before, disable 7 days after expiry

chage -d 0 -m 0 sahilya
# force password change on next login (-d 0 = last change set to epoch)

chage -l sahilya
# list all password aging info for sahilya
```

| `chage` Flag | Meaning |
|---|---|
| `-d` | Set date of last password change |
| `-m` | Minimum days between password changes |
| `-M` | Maximum days a password is valid |
| `-W` | Warning days before expiry |
| `-I` | Inactive days after expiry before account locks |
| `-E` | Account expiry date (YYYY-MM-DD) |

---

## 3. `/etc/group` — Group Details

Each line represents one group.

### Format

```
sahil : ! : 20297 : ram,adii
  1     2     3       4
```

| Field | Meaning |
|---|---|
| 1 — `sahil` | Group name |
| 2 — `!` | Password placeholder (managed in `/etc/gshadow`) |
| 3 — `20297` | Group ID (GID) |
| 4 — `ram,adii` | Comma-separated list of member usernames |

### Group Commands

```bash
groupadd developers            # create a new group called "developers"
groupadd -g 3001 developers    # create group with specific GID 3001

groupmod -n devteam developers # rename group "developers" to "devteam"
groupmod -g 4001 developers    # change GID of group

usermod -aG developers sahil   # add sahil to the "developers" group
                               # (-a = append, -G = supplementary group)

groups sahil                   # show all groups sahil belongs to
```

> **Note:** `addgroup` is a friendlier wrapper around `groupadd` available on Debian/Ubuntu.

---

## 4. `/etc/gshadow` — Group Password Details

Stores encrypted group passwords and group admins. Only readable by root.

### Format

```
sahil : ! : adminuser : ram,adii
  1     2       3           4
```

| Field | Meaning |
|---|---|
| 1 — `sahil` | Group name |
| 2 — `!` | Encrypted group password (`!` means no password set) |
| 3 — `adminuser` | Group administrator(s) — can add/remove members |
| 4 — `ram,adii` | Group members |

### `gpasswd` Commands

```bash
gpasswd developers             # set a password for the group "developers"

gpasswd -a sahil developers    # add user sahil to group developers
gpasswd -d sahil developers    # remove user sahil from group developers

gpasswd -A sahil developers    # make sahil an admin of the developers group
                               # (admin can add/remove members)

gpasswd -M ram,adii developers # set the full member list of the group
```

| `gpasswd` Flag | Meaning |
|---|---|
| (none) | Set group password |
| `-a` | Add a user to the group |
| `-d` | Remove a user from the group |
| `-A` | Set group administrator |
| `-M` | Set full group member list |

---

## Full Example — Create and Verify a New User

```bash
# 1. Create user "adii" with custom settings
useradd -u 2002 -g 1001 -c "Aditya Dev" -m -s /bin/bash adii

# 2. Set password
passwd adii

# 3. Set password aging policy
chage -M 90 -W 7 -I 5 adii

# 4. Verify in /etc/passwd
tail -1 /etc/passwd
# adii:x:2002:1001:Aditya Dev:/home/adii:/bin/bash

# 5. Verify in /etc/shadow
tail -1 /etc/shadow
# adii:$y$...:20295:0:90:7:5::

# 6. Add adii to the developers group
gpasswd -a adii developers

# 7. Verify group membership
tail -1 /etc/group
# developers:x:1001:adii

# 8. Check home directory was populated from /etc/skel
ls -a /home/adii
# .bash-logout  .bashrc  .profile
```

---

## Quick Reference Summary

| File | Contains | Key Command |
|---|---|---|
| `/etc/passwd` | User accounts (UID, shell, home dir) | `useradd`, `usermod` |
| `/etc/shadow` | Encrypted passwords + aging policy | `passwd`, `chage` |
| `/etc/group` | Groups and their members | `groupadd`, `groupmod` |
| `/etc/gshadow` | Group passwords and admins | `gpasswd` |
| `/etc/skel` | Default files copied to new home dirs | (automatic on `useradd -m`) |
