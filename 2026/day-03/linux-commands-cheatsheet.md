# Linux Commands Cheat Sheet

## 1. File System Commands

| Command | Usage                            |
| ------- | -------------------------------- |
| `pwd`   | Show current working directory   |
| `ls`    | List files and directories       |
| `cd`    | Change directory                 |
| `mkdir` | Create a new directory           |
| `touch` | Create an empty file             |
| `cp`    | Copy files and directories       |
| `mv`    | Move or rename files             |
| `rm`    | Delete files and directories     |
| `cat`   | Display file contents            |
| `find`  | Search for files and directories |

### Examples

```bash
pwd
ls -l
cd /home/ubuntu
mkdir demo
touch file.txt
cp file.txt backup.txt
mv file.txt newfile.txt
rm newfile.txt
cat /etc/os-release
find /home -name "*.txt"
```

---

## 2. Process Management Commands

| Command     | Usage                          |
| ----------- | ------------------------------ |
| `ps`        | Display running processes      |
| `top`       | Monitor processes in real time |
| `htop`      | Interactive process viewer     |
| `kill`      | Terminate a process            |
| `killall`   | Kill processes by name         |
| `systemctl` | Manage system services         |
| `jobs`      | List background jobs           |

### Examples

```bash''''
ps aux
top
htop
kill 1234
killall nginx
systemctl status nginx
jobs
```

---

## 3. Networking Troubleshooting Commands

| Command   | Usage                             |
| --------- | --------------------------------- |
| `ping`    | Check network connectivity        |
| `ip addr` | Show IP address information       |
| `curl`    | Transfer data from or to a server |
| `dig`     | Query DNS information             |
| `ss`      | Display network connections       |
| `netstat` | Show network statistics           |

### Examples

```bash
ping google.com
ip addr
curl https://google.com
dig google.com
ss -tuln
netstat -tuln
```

---

## Why These Commands Matter

These commands help DevOps engineers:

* Navigate and manage files.
* Monitor and troubleshoot processes.
* Diagnose network and connectivity issues quickly.
