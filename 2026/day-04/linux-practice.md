# Day 04 – Linux Practice: Processes and Services

Today, I practiced some basic Linux commands related to processes, services, and logs. These commands are very useful for troubleshooting issues in Linux systems.

## Process Checks

### 1. Checking Running Processes

```bash
ps aux
```

I used this command to see all the processes currently running on my system.

### 2. Monitoring Processes in Real Time

```bash
top
```

This command helped me monitor CPU and memory usage in real time and observe active processes.

---

## Service Checks

### 3. Checking SSH Service Status

```bash
systemctl status ssh
```

I checked whether the SSH service was running or not. I learned that systemd services can be managed using the `systemctl` command.

### 4. Listing Running Services

```bash
systemctl list-units --type=service --state=running
```

This command displayed all the services that are currently running on my system.

---

## Log Checks

### 5. Viewing SSH Service Logs

```bash
journalctl -u ssh -n 10
```

I viewed the latest logs for the SSH service to understand how logs help in troubleshooting.

### 6. Checking System Logs

```bash
tail -n 50 /var/log/syslog
```

I used this command to see the last 50 lines from the system log file.

---

## Mini Troubleshooting

### Scenario: SSH Connection Issue

If I am unable to connect to my server using SSH, I can follow these steps:

1. Check whether the SSH service is running.

```bash
systemctl status ssh
```

2. Start the service if it is stopped.

```bash
sudo systemctl start ssh
```

3. Check SSH logs for errors.

```bash
journalctl -u ssh -n 20
```

4. Verify that SSH is listening on port 22.

```bash
sudo ss -tulnp | grep :22
```

## What I Learned

* How to check running processes.
* How to inspect and manage services using systemctl.
* How to read logs for troubleshooting.
* Basic troubleshooting steps for SSH-related issues.

This hands-on practice improved my understanding of Linux fundamentals and troubleshooting.
