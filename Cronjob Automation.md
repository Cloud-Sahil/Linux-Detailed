# ⏰ Cron Jobs (Automation in Linux)

## 📌 Overview
A **cron job** is used to schedule tasks automatically at specific times or intervals in Linux.

---

## ⚙️ Installation & Service Management

```bash
apt update
apt install cron
```
```sh
service cron start     # Start cron service
service cron status    # Check cron status
```
## 📂 Cron Commands
```sh
crontab -e   # Edit cron jobs
crontab -l   # List cron jobs
crontab -r   # Remove all cron jobs (⚠️ Not recommended)
```
```sh
cat /etc/crontab   # View system-wide cron jobs
```
### Cron Schedule Format

| Minute | Hour | Day (Date) | Month           | Day (Week)       |
| ------ | ---- | ---------- | --------------- | ---------------- |
| 0-59   | 0-23 | 1-31       | 1-12 or Jan-Dec | 0-7 (Sun=0 or 7) |

### 🔹 Special Characters
| Symbol | Meaning                     |
| ------ | --------------------------- |
| `*`    | Every value                 |
| `,`    | Multiple values (e.g., 1,5) |
| `-`    | Range (e.g., 1-5)           |
| `/`    | Step values (e.g., */5)     |

### 🔹 Examples
✔️ Daily backup at 7:35 PM
```sh
35 19 * * * /bin/tar -czf /root/opt.tar.gz /opt
```
✔️ Every Saturday at midnight
```sh
0 0 * * sat /bin/touch xyz
```
✔️ Every 5 minutes
```sh
*/5 * * * * /script.sh
```
---
### 📊 Log File (Important)
```sh
/var/log/syslog     # Debian/Ubuntu
/var/log/cron       # RHEL/CentOS
```
