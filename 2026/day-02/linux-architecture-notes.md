# Linux Architecture Notes

## 1. Core Components of Linux

### Kernel

* The kernel is the core part of Linux.
* It acts as a bridge between hardware and software.
* It manages CPU, memory, devices, files, and processes.

### User Space

* User space is where applications run.
* Programs like browsers, editors, and shell commands execute here.
* Users cannot directly access hardware; they communicate through the kernel.

### Init / systemd

* `systemd` is the first process started by the Linux kernel (PID 1).
* It initializes the system during boot.
* It starts and manages background services.

---

## 2. How Processes Are Created and Managed

* A process is a running instance of a program.
* New processes are created using `fork()`.
* A process can start another program using `exec()`.
* Every process has a unique Process ID (PID).
* Linux scheduler decides which process gets CPU time.


### Common Process States

                State                     Description                                    
| Running (R)               | Process is executing on CPU.     
| Sleeping (S)              | Waiting for an event or resource.
| Stopped (T)               | Process execution is paused.  
| Zombie (Z)                | Process has finished but still    exists in process table.

| Uninterruptible Sleep (D) | Waiting for I/O operation to complete. 

---

## 3. What systemd Does and Why It Matters

### What systemd Does

* Starts services during system boot.
* Stops, restarts, and monitors services.
* Maintains system logs using `journald`.
* Handles dependencies between services.

### Why It Matters for DevOps

* Helps troubleshoot failed services.
* Automatically restarts crashed applications.
* Simplifies server management.

---

## 4. Five Daily Linux Commands

1. `ps` - Display running processes.
2. `top` - Monitor CPU and memory usage in real time.
3. `systemctl` - Start, stop, and manage services.
4. `df -h` - Check disk space usage.
5. `free -h` - Check memory usage.

## Example Commands

'''''bash''''''
ps aux
top
systemctl status nginx
df -h
free -h
```
