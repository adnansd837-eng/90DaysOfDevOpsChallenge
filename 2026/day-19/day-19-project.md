# Day 19 – Shell Scripting Project: Log Rotation, Backup & Crontab

## Objective

Today I worked on a small real-world Shell Scripting project where I combined everything I learned over the last few days. I created scripts for log rotation, server backup, and scheduled automation using crontab. This challenge helped me understand how Bash scripting is used in daily DevOps tasks.

---

# Task 1 – Log Rotation Script

I created a script called **log_rotate.sh**.

### What the script does

* Accepts a log directory as an argument.
* Compresses `.log` files older than 7 days using `gzip`.
* Deletes compressed log files older than 30 days.
* Displays how many files were compressed and deleted.
* Stops with an error if the directory does not exist.

### Commands Used

```bash
find /path/to/logs -name "*.log" -mtime +7 -exec gzip {} \;
find /path/to/logs -name "*.gz" -mtime +30 -delete
```

### Sample Output

```text
Checking log directory...
Compressed: 5 log files
Deleted: 2 old archive files
Log rotation completed successfully.
```

---

# Task 2 – Server Backup Script

I created a script called **backup.sh**.

### What the script does

* Accepts source and backup directories as arguments.
* Creates a timestamped `.tar.gz` backup.
* Verifies that the backup was created successfully.
* Displays the backup file name and size.
* Removes backup files older than 14 days.
* Exits if the source directory is missing.

### Commands Used

```bash
tar -czf backup-$(date +%Y-%m-%d).tar.gz /source
find /backup -name "*.tar.gz" -mtime +14 -delete
```

### Sample Output

```text
Backup created successfully.
File: backup-2026-08-06.tar.gz
Size: 18 MB
Old backups cleaned successfully.
```

---

# Task 3 – Understanding Crontab

I learned how cron jobs automate repetitive tasks in Linux.

### Cron Entries

Run log rotation every day at **2:00 AM**

```cron
0 2 * * * /home/user/log_rotate.sh
```

Run backup every **Sunday at 3:00 AM**

```cron
0 3 * * 0 /home/user/backup.sh
```

Run health check every **5 minutes**

```cron
*/5 * * * * /home/user/health_check.sh
```

---

# Task 4 – Scheduled Maintenance Script

I created **maintenance.sh** to combine both log rotation and backup tasks.

The script:

* Runs the log rotation script.
* Runs the backup script.
* Saves all output to `/var/log/maintenance.log` with timestamps.

Example logging command:

```bash
echo "$(date): Maintenance completed successfully." >> /var/log/maintenance.log
```

Cron entry:

```cron
0 1 * * * /home/user/maintenance.sh
```

---

# Commands I Practiced

```bash
find
gzip
tar
date
cron
crontab -l
crontab -e
```

---

# What I Learned

* I learned how log rotation helps manage old log files and saves disk space.
* I understood how to automate server backups using Bash scripts.
* I learned the basics of scheduling jobs with cron.
* I practiced combining multiple scripts into a single maintenance script.
* I realized that automation reduces manual work and makes server management more reliable.

---



**Day 19 completed ✅**
