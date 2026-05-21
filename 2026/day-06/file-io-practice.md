# Day 06 – Linux Fundamentals: Read and Write Text Files

Today I practiced basic file handling commands in Linux. I learned how to create a file, write text into it, append new lines, and read file contents using different commands.

---

# File Creation

## touch notes.txt
Creates an empty file named `notes.txt`.

---

# Writing to File

## echo "Linux basics practice" > notes.txt
Writes text into the file and replaces existing content.

## echo "Learning file handling commands" >> notes.txt
Appends a new line to the file without removing old content.

## echo "Practicing Linux daily" | tee -a notes.txt
Displays the text on terminal and also appends it to the file.

---

# Reading File Content

## cat notes.txt
Displays the full content of the file.

## head -n 2 notes.txt
Displays the first 2 lines from the file.

## tail -n 2 notes.txt
Displays the last 2 lines from the file.

---

# What I Learned

- Difference between `>` and `>>`
- How to append text into files
- How to read full and partial file contents
- Basic Linux file handling workflow
