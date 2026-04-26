#  Introduction to Linux

> Topics covered: What is Linux · Architecture · History · Shell Prompt · User Types · Distributions · Key Concepts · DevOps · Cloud · OS · Windows vs Linux

---

## What is Linux?

Linux is a **free, open-source operating system kernel** created by **Linus Torvalds in 1991**.
It is widely used in servers, cloud platforms, DevOps pipelines, embedded systems, and cybersecurity.

Unlike Windows, Linux is:
- Free to use and distribute
- Highly customizable
- Extremely stable and secure
- Preferred for servers and development environments

### Popular Linux Distributions

| Distribution | Based On | Best For |
|---|---|---|
| Ubuntu | Debian | Beginners, Desktops |
| CentOS / RHEL | Red Hat | Enterprise Servers |
| Fedora | Red Hat | Developers |
| Arch Linux | Independent | Advanced Users |
| Kali Linux | Debian | Cybersecurity |
| Raspberry Pi OS | Debian | IoT, Embedded Systems |

---

## Linux History Timeline

| Year | Event |
|---|---|
| 1969 | UNIX created at AT&T Bell Labs |
| 1983 | GNU Project started by Richard Stallman |
| 1991 | Linus Torvalds released Linux kernel v0.01 |
| 1994 | Linux kernel v1.0 officially released |
| 2004 | Ubuntu launched — Linux for everyday users |
| 2008 | Android (Linux-based) launched by Google |

---

## Architecture of Linux
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/df314487-3794-4114-8a72-2e5a725e3b99" />

---

## Key Linux Concepts

| Concept | Meaning |
|---|---|
| Kernel | Core of Linux — manages hardware resources |
| Shell | Interface between the user and the kernel |
| Terminal | Application used to access the shell (e.g. GNOME Terminal) |
| Distro | Linux kernel + bundled software (e.g. Ubuntu, Fedora) |
| Root | Superuser with full system permissions |
| Package | Software bundled for easy installation (`.deb`, `.rpm`) |

### Kernel vs Shell vs Terminal — Difference

```
You type a command
       ↓
   Terminal        ← the window/app (e.g. GNOME Terminal)
       ↓
     Shell         ← interprets the command (e.g. bash)
       ↓
    Kernel         ← executes it by talking to hardware
       ↓
   Hardware        ← actual action performed
```

**Example:**

```bash
ls /home
# You type in Terminal → Shell (bash) interprets "ls"
# → Kernel reads the /home directory from disk
# → Shell prints result back in Terminal
```

---

## Shell Prompt — Understanding the Command Line

```bash
labex:project/ $
```

| Part | Meaning |
|---|---|
| `labex` | Currently logged-in username |
| `project/` | Current working directory (where you are in the filesystem) |
| `$` | Prompt symbol — indicates the user type |

### User Types

| Symbol | User Type | Permissions |
|---|---|---|
| `$` | Regular / Local User | Limited — cannot modify system files |
| `#` | Root / Super User | Full access — can do anything on the system |

**Example:**

```bash
sahil@ubuntu:~$          # regular user "sahil" in home directory
root@ubuntu:/etc#        # root user in /etc directory
```

> **Warning:** Always work as a regular user (`$`). Use `sudo` only when required.
> Running everything as root is dangerous — one wrong command can break the system.

---

## What is an Operating System (OS)?

An **Operating System** is system software that:
- Manages hardware (CPU, RAM, disk, input/output)
- Manages software resources and running programs
- Acts as a bridge between the user and hardware

```
User
 ↓
Applications (browser, editor, etc.)
 ↓
Operating System (Linux, Windows)
 ↓
Hardware (CPU, RAM, Disk)
```

### Linux helps you:
- Run programs and manage processes
- Manage files and directories
- Control hardware devices
- Communicate over networks

---

## Windows vs Linux

| Feature | Windows | Linux |
|---|---|---|
| Cost | Paid license required | Free and open-source |
| Performance | Good for personal use | Best for servers and development |
| Security | Moderate (frequent malware targets) | Very secure, fewer vulnerabilities |
| Interface | GUI-focused | CLI + GUI (CLI is primary for servers) |
| Customization | Limited | Highly customizable |
| Use Case | Desktops, gaming, office | Servers, DevOps, cloud, development |
| Package Manager | Manual installers (`.exe`) | `apt`, `yum`, `dnf`, `pacman` |

**Example — Installing software:**

```bash
# Linux (Ubuntu) — one command, no clicking
sudo apt install nginx

# Windows — download installer → click Next → Next → Finish
```

---

## What is DevOps?

**DevOps** = **Dev**elopment + **Op**eration**s**

It is a set of practices that bridges the gap between software development teams and IT operations, enabling **faster, more reliable software delivery**.

### The Three Roles

| Role | Responsibility | Example Task |
|---|---|---|
| Developer | Writes code, builds features | Create a login page |
| Tester | Checks if features work correctly | Test login with wrong password |
| DevOps Engineer | Deploys, automates, and monitors | Push code live, monitor server health |

### DevOps Lifecycle (simplified)

```
Developer writes code
        ↓
Tester checks for bugs
        ↓
DevOps builds & packages the app
        ↓
DevOps deploys to server (Deployment)
        ↓
App is publicly available
        ↓
DevOps monitors performance & uptime
```

**Deployment** = making an application publicly available on a server so real users can access it.

---

## What is an Application?

An **application** is a piece of software designed to perform a specific task.

| Type | Example |
|---|---|
| Web Application | Gmail, YouTube |
| Mobile Application | WhatsApp, Instagram |
| Desktop Application | VS Code, VLC |
| Server Application | Nginx (web server), MySQL (database) |

---

## What is Cloud?

**Cloud** is a platform that provides computing resources — servers, storage, databases, networking, and software — **over the internet**, instead of using local hardware.

### Why Cloud?

| Without Cloud | With Cloud |
|---|---|
| Buy physical servers | Rent servers on demand |
| Maintain hardware yourself | Provider handles maintenance |
| Fixed capacity | Scale up/down instantly |
| High upfront cost | Pay only for what you use |

### Major Cloud Providers

| Provider | Platform |
|---|---|
| Amazon | AWS (Amazon Web Services) |
| Microsoft | Azure |
| Google | GCP (Google Cloud Platform) |

**Example:**

```bash
# Without cloud: deploy app on your own server at home/office
# With cloud: spin up a server in seconds
aws ec2 run-instances --image-id ami-12345 --instance-type t2.micro
# A new Linux server is running in the cloud within 30 seconds
```

---

## Quick Reference Summary

| Topic | One-Line Summary |
|---|---|
| Linux | Free, open-source OS kernel — powers servers, cloud, DevOps |
| Kernel | Core of the OS — directly talks to hardware |
| Shell | Interprets and runs your commands (`bash`, `zsh`) |
| Terminal | The app/window where you type commands |
| `$` prompt | Regular user — limited permissions |
| `#` prompt | Root user — full system access |
| DevOps | Bridges Dev and Ops — automates delivery and deployment |
| Cloud | Internet-based computing resources on demand |
| OS | Software layer managing hardware and applications |
