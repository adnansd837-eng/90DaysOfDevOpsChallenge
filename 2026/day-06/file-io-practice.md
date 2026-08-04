# Day 06 – Linux File Read & Write Practice

Task
Today I practiced some basic Linux file commands.

The main goal was to learn how to create a file, write data into it, add more lines, and read the file using different commands.

This is an important skill because in DevOps we often work with log files, configuration files, and scripts.

# What I Practiced
Created a new file named notes.txt
Wrote text into the file using >
Added more lines using >>
Used tee to write and display text at the same time
Read the complete file using cat
Viewed the first few lines using head
Viewed the last few lines using tail

# Commands I Used
        touch notes.txt
    echo "Linux File Practice" > notes.txt
    echo "Learning file commands" >> notes.txt
    echo "Practicing every day" | tee -a notes.txt
    cat notes.txt
    head -n 2 notes.txt
    tail -n 2 notes.txt

# What I Learned
touch creates a new empty file.
> writes data and replaces old content.
>> adds new data without deleting existing content.

#tee writes and shows the output at the same time.
cat displays the complete file.
head shows the beginning of the file.
tail shows the end of the file.

                Why This Is Useful

As a DevOps engineer, I will work with log files, configuration files, and scripts every day. Knowing these basic commands will help me read files, update configurations, and troubleshoot problems more efficiently.

