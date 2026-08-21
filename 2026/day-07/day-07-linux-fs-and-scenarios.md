# Day 07 – Linux File System Hierarchy & Scenario Practice

# Part 1: Linux File System Hierarchy

## 1. `/` (Root Directory)

* This is the main directory in Linux.
* Every file and folder starts from here.

**Example:**

```bash
ls -l /
```

**I would use this when:**
I need to understand the overall Linux directory structure.

---

## 2. `/home`

* Stores personal files of normal users.
* Every user gets a separate home directory.

**Example:**

```bash
ls -la /home
```

**I would use this when:**
I want to access or manage a user's files.

---

## 3. `/root`

* Home directory of the root (administrator) user.
* Only the root user normally works here.

**Example:**

```bash
ls -la /root
```

**I would use this when:**
I am logged in as the root user and need to manage system files.

---

## 4. `/etc`

* Contains system configuration files.
* Most application settings are stored here.

**Example:**

```bash
cat /etc/hostname
```

**I would use this when:**
I need to change server or application configuration.

---

## 5. `/var/log`

* Stores system and application log files.
* Very useful while troubleshooting issues.

**Example:**

```bash
ls -l /var/log
```

**I would use this when:**
I need to find errors or check why a service failed.

---

## 6. `/tmp`

* Used for temporary files.
* Files here may be deleted after reboot.

**Example:**

```bash
ls -la /tmp
```

**I would use this when:**
I need temporary storage while testing scripts.

---

## 7. `/bin`

* Contains important Linux commands.
* These commands are available to all users.

**Example:**

```bash
ls /bin
```

**I would use this when:**
I want to know where basic Linux commands are stored.

---

## 8. `/usr/bin`

* Stores additional user commands and applications.

**Example:**

```bash
ls /usr/bin
```

**I would use this when:**
I need to locate installed command-line programs.

---

## 9. `/opt`

* Used for third-party software.
* Applications installed manually are often stored here.

**Example:**

```bash
ls /opt
```

**I would use this when:**
I install software that is not part of the default Linux packages.

---

# Hands-on Practice

## Find the Largest Log Files

```bash
du -sh /var/log/* 2>/dev/null | sort -h | tail -5
```

This command shows the biggest log files.

---

## View Hostname

```bash
cat /etc/hostname
```

Shows the current hostname of the server.

---

## Check Home Directory

```bash
ls -la ~
```

Lists all files and hidden files in my home directory.

---

# Part 2: Scenario-Based Practice

## Scenario 1: Service Not Starting

### Step 1

```bash
systemctl status myapp
```

**Why:** Check whether the service is running, stopped, or failed.

### Step 2

```bash
journalctl -u myapp -n 50
```

**Why:** Read the latest logs to find the error.

### Step 3

```bash
systemctl is-enabled myapp
```

**Why:** Check if the service starts automatically after reboot.

### Step 4

```bash
systemctl restart myapp
```

**Why:** Restart the service after fixing the issue.

**What I learned:**
Always check the service status first, then logs, then restart if needed.

---

## Scenario 2: High CPU Usage

### Step 1

```bash
top
```

**Why:** View CPU usage in real time.

### Step 2

```bash
ps aux --sort=-%cpu | head -10
```

**Why:** Find the process using the most CPU.

### Step 3

```bash
kill <PID>
```

**Why:** Stop the process if it is causing problems.

**What I learned:**
First identify the process, then decide whether it should be stopped.

---

## Scenario 3: Finding Service Logs

### Step 1

```bash
systemctl status docker
```

**Why:** Check whether Docker is running.

### Step 2

```bash
journalctl -u docker -n 50
```

**Why:** View the last 50 log entries.

### Step 3

```bash
journalctl -u docker -f
```

**Why:** Watch logs in real time while troubleshooting.

**What I learned:**
Most systemd services store their logs in journald.

---

## Scenario 4: File Permission Issue

### Step 1

```bash
ls -l /home/user/backup.sh
```

**Why:** Check the current file permissions.

### Step 2

```bash
chmod +x /home/user/backup.sh
```

**Why:** Give execute permission to the script.

### Step 3

```bash
ls -l /home/user/backup.sh
```

**Why:** Verify that execute permission has been added.

### Step 4

```bash
./backup.sh
```

**Why:** Run the script and confirm it works.

**What I learned:**
A script needs execute (`x`) permission before it can run.

---

# Key Takeaways

* Linux stores files in different directories based on their purpose.
* `/etc` contains configuration files.
* `/var/log` is the first place to check during troubleshooting.
* `systemctl` and `journalctl` are useful for managing and debugging services.
* File permissions are important for security and execution.
* Following a step-by-step troubleshooting approach helps solve problems faster.
