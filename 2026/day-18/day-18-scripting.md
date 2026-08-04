# Day 18 – Shell Scripting: Functions & Intermediate Concepts

## Objective

Today I learned how to write better Bash scripts using functions. I also explored strict mode (`set -euo pipefail`), local variables, and built a system information script by combining multiple functions. These concepts helped me understand how to write cleaner, reusable, and more reliable shell scripts.

---

# Task 1 – Basic Functions

I started by creating simple functions to understand how they work.

### Script

```bash
#!/bin/bash

greet() {
    echo "Hello, $1!"
}

add() {
    sum=$(( $1 + $2 ))
    echo "Sum = $sum"
}

greet "Adnan"
add 10 20
```

### Output

```text
Hello, Adnan!
Sum = 30
```

### What I Learned

Functions help organize code into smaller reusable blocks. Instead of writing the same code again, I can simply call the function whenever I need it.

---

# Task 2 – Functions for System Checks

Next, I created functions to check disk space and memory usage.

### Script

```bash
#!/bin/bash

check_disk() {
    echo "Disk Usage"
    df -h /
}

check_memory() {
    echo "Memory Usage"
    free -h
}

check_disk
check_memory
```

### What I Learned

Using separate functions makes scripts easier to read and maintain. Each function performs one specific task.

---

# Task 3 – Understanding Strict Mode

I added the following line after the shebang:

```bash
set -euo pipefail
```

Then I tested different situations like using an undefined variable and running a failing command.

### My Understanding

**set -e**

Stops the script immediately if any command fails.

**set -u**

Stops the script if an undefined variable is used.

**set -o pipefail**

Returns an error if any command inside a pipeline fails.

### What I Learned

Strict mode makes scripts safer because errors are detected immediately instead of continuing with incorrect results.

---

# Task 4 – Local Variables

I practiced using the `local` keyword inside a function.

### Script

```bash
#!/bin/bash

show_name() {
    local NAME="Adnan"
    echo "Inside Function: $NAME"
}

show_name

echo "Outside Function: $NAME"
```

### Output

```text
Inside Function: Adnan
Outside Function:
```

### What I Learned

A local variable is only available inside the function where it is created. It does not affect variables outside the function.

---

# Task 5 – System Information Reporter

Finally, I created a script that collects important system information using multiple functions.

The script displays:

* Hostname
* Operating System
* System Uptime
* Disk Usage
* Memory Usage
* Top 5 CPU-consuming processes

### Commands Used Inside the Script

```bash
hostname

uname -a

uptime

df -h

free -h

ps aux --sort=-%cpu | head -5
```

### What I Learned

Breaking a large script into multiple functions makes it easier to understand and update. It also improves code readability.

---

# Commands Used

```bash
chmod +x functions.sh
./functions.sh

chmod +x disk_check.sh
./disk_check.sh

chmod +x strict_demo.sh
./strict_demo.sh

chmod +x local_demo.sh
./local_demo.sh

chmod +x system_info.sh
./system_info.sh
```

---

# What I Learned

* I learned how to create and call functions in Bash scripts.
* I understood how to pass arguments to functions.
* I learned the purpose of `set -euo pipefail` and why it is considered a good practice.
* I practiced using local variables inside functions.
* I built a reusable system information script using multiple functions.
* I realized that organizing scripts into functions makes them easier to manage and troubleshoot.

---

