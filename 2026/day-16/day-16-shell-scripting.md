# Day 16 – Shell Scripting Basics

## Objective

Today I started learning Shell Scripting. Until now, I was running Linux commands one by one, but today I learned how to automate tasks by writing simple Bash scripts. I practiced using variables, user input, and basic if-else conditions.

---

# Task 1 – My First Shell Script

I created my first Bash script called **hello.sh**. I added the shebang line at the top and used the `echo` command to print a message.

### Script

```bash
#!/bin/bash

echo "Hello, DevOps!"
```

### Commands Used

```bash
chmod +x hello.sh

./hello.sh
```

### Output

```text
Hello, DevOps!
```

### What I Learned

The shebang (`#!/bin/bash`) tells Linux which interpreter should execute the script.

If I remove the shebang and try to execute the script directly, Linux may not know which shell should run it. The script can fail or behave differently depending on the default shell.

---

# Task 2 – Variables

Next, I learned how to create variables and use them inside a script.

### Script

```bash
#!/bin/bash

NAME="Adnan"
ROLE="DevOps Engineer"

echo "Hello, I am $NAME and I am a $ROLE."
```

### Output

```text
Hello, I am Adnan and I am a DevOps Engineer.
```

### Single Quotes vs Double Quotes

```bash
echo '$NAME'
```

Output:

```text
$NAME
```

```bash
echo "$NAME"
```

Output:

```text
Adnan
```

### What I Learned

Single quotes print the text exactly as written, while double quotes allow variables to expand and display their values.

---

# Task 3 – Taking User Input

I learned how to accept input from the user using the `read` command.

### Script

```bash
#!/bin/bash

read -p "Enter your name: " NAME
read -p "Enter your favourite tool: " TOOL

echo "Hello $NAME, your favourite tool is $TOOL."
```

### Example Output

```text
Enter your name: Adnan
Enter your favourite tool: Docker

Hello Adnan, your favourite tool is Docker.
```

### What I Learned

The `read` command makes the script interactive by accepting values from the user.

---

# Task 4 – If-Else Conditions

### Check Positive or Negative Number

```bash
#!/bin/bash

read -p "Enter a number: " NUM

if [ $NUM -gt 0 ]
then
    echo "Positive Number"
elif [ $NUM -lt 0 ]
then
    echo "Negative Number"
else
    echo "Zero"
fi
```

### File Exists Check

```bash
#!/bin/bash

read -p "Enter file name: " FILE

if [ -f "$FILE" ]
then
    echo "File exists."
else
    echo "File not found."
fi
```

### What I Learned

The `if-else` statement helps make decisions based on conditions. It is useful for checking files, services, user input, and many other system tasks.

---

# Task 5 – Server Status Check

Finally, I combined everything into one script.

### Script

```bash
#!/bin/bash

SERVICE="nginx"

read -p "Do you want to check the service status? (y/n): " CHOICE

if [ "$CHOICE" = "y" ]
then
    systemctl status $SERVICE

    if systemctl is-active --quiet $SERVICE
    then
        echo "Service is active."
    else
        echo "Service is not running."
    fi

else
    echo "Skipped."
fi
```

### What I Learned

This task helped me understand how variables, user input, and conditions work together in a real script. It also showed me how Bash scripts can automate routine system administration tasks.

---

# Commands Used

```bash
chmod +x hello.sh

./hello.sh

bash variables.sh

bash greet.sh

bash check_number.sh

bash file_check.sh

bash server_check.sh
```

---

# What I Learned

* I learned how to create and execute my first Bash script.
* I understood the purpose of the shebang line (`#!/bin/bash`).
* I learned how to use variables to store values.
* I practiced taking user input with the `read` command.
* I learned how to use `if`, `elif`, and `else` to make decisions.
* I created a simple script to check the status of a Linux service.

---

