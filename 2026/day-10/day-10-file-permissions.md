# Day 10 – File Permissions & File Operations Challenge

Today I practiced Linux file operations and permissions management using commands like `touch`, `cat`, `vim`, and `chmod`.

---

# Task 1 – Create Files

## Create Empty File

```bash
touch devops.txt
```

Used to create an empty file.

---

## Create notes.txt with Content

```bash
echo "Linux file permissions practice" > notes.txt
```

Used to create a file and write text into it.

---

## Create script.sh using vim

```bash
vim script.sh
```

Added this inside the file:

```bash
echo "Hello DevOps"
```

Used to create and edit shell script files.

---

## Verify Files

```bash
ls -l
```

Used to display files and permissions.

---

# Task 2 – Read Files

## Read notes.txt

```bash
cat notes.txt
```

Used to display file content.

---

## Open script.sh in Read-only Mode

```bash
vim -R script.sh
```

Used to open file in read-only mode.

---

## Display First 5 Lines of passwd File

```bash
head -n 5 /etc/passwd
```

Used to display first 5 lines of a file.

---

## Display Last 5 Lines of passwd File

```bash
tail -n 5 /etc/passwd
```

Used to display last 5 lines of a file.

---

# Task 3 – Understand Permissions

## Check File Permissions

```bash
ls -l devops.txt notes.txt script.sh
```

Example output:

```bash
-rw-r--r-- 1 user user 0 May 25 10:30 devops.txt
-rw-r--r-- 1 user user 35 May 25 10:31 notes.txt
-rw-r--r-- 1 user user 20 May 25 10:32 script.sh
```

Permission format:
```bash
rwxrwxrwx
```

- `r` = read
- `w` = write
- `x` = execute

First 3 characters → Owner permissions  
Middle 3 characters → Group permissions  
Last 3 characters → Others permissions

---

# Task 4 – Modify Permissions

## Make script.sh Executable

```bash
chmod +x script.sh
```

Used to add execute permission.

---

## Run the Script

```bash
./script.sh
```

Used to execute the shell script.

---

## Make devops.txt Read-only

```bash
chmod a-w devops.txt
```

Used to remove write permission from everyone.

---

## Set notes.txt Permission to 640

```bash
chmod 640 notes.txt
```

Permission meaning:
- Owner → read/write
- Group → read only
- Others → no permission

---

## Create project Directory with 755 Permission

```bash
mkdir project
chmod 755 project
```

Used to create directory with standard Linux permissions.

---

## Verify Permissions

```bash
ls -l
```

Used to check updated permissions.

---

# Task 5 – Test Permissions

## Try Writing to Read-only File

```bash
echo "test" >> devops.txt
```

Result:
Permission denied because file is read-only.

---

## Remove Execute Permission

```bash
chmod -x script.sh
```

Used to remove execute permission.

---

## Try Running Script Again

```bash
./script.sh
```

Result:
Permission denied because execute permission was removed.

---

# What I Learned

- How Linux file permissions work
- Difference between read, write, and execute permissions
- How to modify permissions using chmod
- How to create and execute shell scripts
- How Linux restricts access using permissions
