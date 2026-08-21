# Day 21 – Shell Scripting Cheat Sheet

## 1. Shell Script Basics

### Shebang

The shebang tells Linux which shell should be used to run the script.

```bash
#!/bin/bash
```

### Run a Script

```bash
chmod +x script.sh
./script.sh
```

We can also run it using:

```bash
bash script.sh
```

### Comments

Comments are used to explain the code. Linux does not execute them.

```bash
# This is a comment
echo "Hello"  # This is an inline comment
```

### Variables

Variables are used to store values.

```bash
NAME="Adnan"
echo "$NAME"
```

Double quotes use the variable value:

```bash
echo "$NAME"
```

Single quotes print it as it is:

```bash
echo '$NAME'
```

### User Input

`read` is used to take input from the user.

```bash
read -p "Enter your name: " NAME
echo "Hello $NAME"
```

### Command-Line Arguments

```bash
$0   # Script name
$1   # First argument
$2   # Second argument
$#   # Number of arguments
$@   # All arguments
$?   # Exit status of last command
```

Example:

```bash
./script.sh hello world
```

---

# 2. Conditions and Operators

## String Comparison

```bash
[ "$NAME" = "Adnan" ]
[ "$NAME" != "Adnan" ]
[ -z "$NAME" ]
[ -n "$NAME" ]
```

* `=` → equal
* `!=` → not equal
* `-z` → empty string
* `-n` → not empty

## Number Comparison

```bash
[ $A -eq $B ]   # equal
[ $A -ne $B ]   # not equal
[ $A -lt $B ]   # less than
[ $A -gt $B ]   # greater than
[ $A -le $B ]   # less/equal
[ $A -ge $B ]   # greater/equal
```

## File Checks

```bash
[ -f file.txt ]   # File exists
[ -d folder ]     # Directory exists
[ -e file ]       # File or directory exists
[ -r file ]       # Read permission
[ -w file ]       # Write permission
[ -x file ]       # Execute permission
[ -s file ]       # File is not empty
```

## If-Else

```bash
if [ -f file.txt ]; then
    echo "File exists"
else
    echo "File does not exist"
fi
```

## Logical Operators

```bash
command1 && command2
```

Runs command2 if command1 succeeds.

```bash
command1 || command2
```

Runs command2 if command1 fails.

```bash
! command
```

Reverses the result.

## Case

Useful when there are multiple choices.

```bash
case $CHOICE in
    start)
        echo "Starting"
        ;;
    stop)
        echo "Stopping"
        ;;
    *)
        echo "Invalid option"
        ;;
esac
```

---

# 3. Loops

## For Loop

Used when we want to repeat something for a list.

```bash
for fruit in apple mango banana
do
    echo "$fruit"
done
```

## C-Style For Loop

```bash
for ((i=1; i<=5; i++))
do
    echo "$i"
done
```

## While Loop

Runs while the condition is true.

```bash
count=1

while [ $count -le 5 ]
do
    echo "$count"
    ((count++))
done
```

## Until Loop

Runs until the condition becomes true.

```bash
count=1

until [ $count -gt 5 ]
do
    echo "$count"
    ((count++))
done
```

## Break and Continue

```bash
break
```

Stops the loop.

```bash
continue
```

Skips the current iteration.

## Loop Through Files

```bash
for file in *.log
do
    echo "$file"
done
```

## Read Lines

```bash
while read line
do
    echo "$line"
done < file.txt
```

---

# 4. Functions

Functions help me reuse the same code.

## Create a Function

```bash
greet() {
    echo "Hello"
}
```

## Call a Function

```bash
greet
```

## Function Arguments

```bash
greet() {
    echo "Hello $1"
}

greet "Adnan"
```

## Return Value

`return` is mainly used for status codes.

```bash
check() {
    return 0
}
```

`echo` can be used to return/display a value.

```bash
add() {
    echo $(( $1 + $2 ))
}

result=$(add 10 20)
echo "$result"
```

## Local Variable

`local` keeps a variable inside the function.

```bash
test() {
    local NAME="Adnan"
    echo "$NAME"
}
```

---

# 5. Useful Text Commands

## grep

Used to search text.

```bash
grep "ERROR" app.log
```

Useful options:

```bash
grep -i "error" file
grep -n "error" file
grep -c "error" file
grep -r "error" folder/
grep -v "error" file
grep -E "ERROR|Failed" file
```

## awk

Useful for working with columns.

```bash
awk '{print $1}' file.txt
```

Example:

```bash
awk -F: '{print $1}' /etc/passwd
```

## sed

Used to replace or modify text.

```bash
sed 's/old/new/g' file.txt
```

Edit file directly:

```bash
sed -i 's/old/new/g' file.txt
```

## cut

Used to extract columns.

```bash
cut -d: -f1 /etc/passwd
```

## sort

Sorts data.

```bash
sort file.txt
sort -n numbers.txt
sort -r file.txt
```

## uniq

Removes repeated lines or counts them.

```bash
uniq file.txt
uniq -c file.txt
```

## tr

Used to replace or remove characters.

```bash
echo "hello" | tr 'a-z' 'A-Z'
```

## wc

Counts lines, words and characters.

```bash
wc -l file.txt
wc -w file.txt
wc -c file.txt
```

## head and tail

Show the beginning or end of a file.

```bash
head file.txt
tail file.txt
```

Follow a log in real time:

```bash
tail -f app.log
```

---

# 6. Useful One-Liners

### Find large files

```bash
du -sh * | sort -h
```

### Find old log files

```bash
find /var/log -name "*.log" -mtime +7
```

### Check service status

```bash
systemctl status nginx
```

### Check disk usage

```bash
df -h
```

### Find errors in a log

```bash
tail -f app.log | grep "ERROR"
```

---

# 7. Error Handling

## Exit Status

Every command returns an exit status.

```bash
echo $?
```

Usually:

```text
0 = success
non-zero = error
```

## exit

```bash
exit 0
```

Means successful completion.

```bash
exit 1
```

Means the script ended with an error.

## set -e

Stops the script when a command fails.

```bash
set -e
```

## set -u

Treats an undefined variable as an error.

```bash
set -u
```

## pipefail

Helps catch errors inside a pipeline.

```bash
set -o pipefail
```

## Strict Mode

I can use all three together:

```bash
set -euo pipefail
```

This makes my scripts safer.

## set -x

Shows commands while the script is running. Useful for debugging.

```bash
set -x
```

## trap

Used to run cleanup code when the script exits.

```bash
trap 'echo "Script finished"' EXIT
```

---

# 8. Quick Reference

| Topic    | Example                   |
| -------- | ------------------------- |
| Variable | `NAME="Adnan"`            |
| Argument | `$1`                      |
| Input    | `read NAME`               |
| If       | `if [ condition ]; then`  |
| For      | `for i in 1 2 3; do`      |
| While    | `while [ condition ]; do` |
| Function | `greet() { ... }`         |
| Search   | `grep "ERROR" file`       |
| Columns  | `awk '{print $1}' file`   |
| Replace  | `sed 's/old/new/g' file`  |
| Sort     | `sort file`               |
| Count    | `wc -l file`              |
| Logs     | `tail -f app.log`         |
| Service  | `systemctl status nginx`  |
| Disk     | `df -h`                   |

---

# What I Learned

* I learned how to write Bash scripts using variables, conditions, loops and functions.
* I learned how commands like `grep`, `awk`, `sed` and `sort` help in log analysis.
* I learned basic error handling using `set -euo pipefail`.
* I also practiced writing scripts that can be useful in real DevOps tasks.

## Day 21 Completed ✅

Continuing my **90 Days of DevOps** journey and improving my Linux and Shell Scripting skills step by step.
