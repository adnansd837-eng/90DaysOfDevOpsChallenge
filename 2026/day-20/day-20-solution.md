
# Day 20 – Bash Scripting: Log Analyzer & Report Generator

## Objective

Today I worked on a Bash scripting project to analyze a log file and generate a simple report.

The main goal was to practice commands like `grep`, `awk`, `sort`, `uniq`, and `wc` and understand how they can be used together for log analysis.

---

## Task 1 – Input Validation

I created a script called `log_analyzer.sh`.

The script first checks whether a log file was provided.

```bash
if [ $# -eq 0 ]
then
    echo "Usage: ./log_analyzer.sh <log-file>"
    exit 1
fi

if [ ! -f "$1" ]
then
    echo "Error: Log file does not exist."
    exit 1
fi
```

This prevents the script from running when the log file is missing.

---

## Task 2 – Count Errors

I used `grep` to find lines containing `ERROR` or `Failed`.

```bash
error_count=$(grep -Ei "ERROR|Failed" "$log_file" | wc -l)

echo "Total Errors: $error_count"
```

### Example Output

```text
Total Errors: 15
```

---

## Task 3 – Find Critical Events

I used `grep -n` to display critical events along with their line numbers.

```bash
grep -n "CRITICAL" "$log_file"
```

### Example Output

```text
84:2026-08-07 10:15:23 CRITICAL Disk space is low
217:2026-08-07 14:32:01 CRITICAL Database connection lost
```

This is useful because I can quickly find where critical problems occurred in the log.

---

## Task 4 – Find Top Error Messages

I used `grep`, `sort`, `uniq`, and `head` to find frequently occurring errors.

```bash
grep "ERROR" "$log_file" | \
awk '{$1=$2=$3=""; print}' | \
sort | uniq -c | sort -rn | head -5
```

### Example Output

```text
45 Connection timed out
32 File not found
28 Permission denied
15 Disk I/O error
9 Out of memory
```

This helped me understand which errors are happening most often.

---

## Task 5 – Generate Report

The script creates a report with the current date.

```bash
date=$(date +%Y-%m-%d)
report="log_report_${date}.txt"
```

The report contains:

* Date of analysis
* Log file name
* Total lines processed
* Total error count
* Top 5 errors
* Critical events

### Example Report

```text
===== Log Analysis Report =====

Date: 2026-08-07
Log File: sample_log.log

Total Lines: 500
Total Errors: 15

--- Top 5 Errors ---

45 Connection timed out
32 File not found
28 Permission denied
15 Disk I/O error
9 Out of memory

--- Critical Events ---

84: CRITICAL Disk space is low
217: CRITICAL Database connection lost
```

---

## Commands I Used

```bash
grep
grep -n
awk
sort
uniq
head
wc
date
mv
```

---

## What I Learned

* I learned how to analyze log files using Bash commands.
* I understood how `grep` can quickly find errors and critical events.
* I learned how `awk`, `sort`, and `uniq` can be combined to find common errors.
* I practiced taking command output and saving it into a report.
* I understood how log analysis can help identify problems on a server.

---


**Day 20 completed ✅**
