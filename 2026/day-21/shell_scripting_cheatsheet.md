# Shell Scripting Cheat Sheet

## Quick Reference

| Topic | Syntax | Example |
|---|---|---|
| Variable | `VAR="value"` | `NAME="DevOps"` |
| Argument | `$1 $2` | `./script.sh Ankit` |
| If | `if [ condition ]; then` | `if [ -f file ]; then` |
| For | `for i in list; do` | `for i in 1 2 3; do` |
| Function | `name(){}` | `greet(){ echo "Hi"; }` |
| grep | `grep pattern file` | `grep -i error app.log` |
| awk | `awk '{print $1}' file` | `awk -F: '{print $1}' /etc/passwd` |
| sed | `sed 's/a/b/g'` | `sed -i 's/foo/bar/g' file` |

# 1. Basics

### Shebang
```bash
#!/bin/bash
```
Tells Linux which interpreter runs the script.

### Run Script
```bash
chmod +x script.sh
./script.sh
bash script.sh
```

### Comments
```bash
# Single line
echo "Hello" # Inline
```

### Variables
```bash
NAME="Ankit"
echo $NAME
echo "$NAME"
echo '$NAME'
```

### User Input
```bash
read -p "Enter name: " NAME
```

### Arguments
```bash
$0  # script
$1  # first arg
$2  # second arg
$#  # count
$@  # all args
$?  # exit code
```

# 2. Operators & Conditionals

## String
`= != -z -n`

## Integer
`-eq -ne -lt -gt -le -ge`

## File Tests
`-f -d -e -r -w -x -s`

```bash
if [ -f file.txt ]; then
  echo "Exists"
elif [ -d test ]; then
  echo "Directory"
else
  echo "Missing"
fi
```

Logical: `&& || !`

```bash
case $1 in
start) echo "Start";;
stop) echo "Stop";;
*) echo "Invalid";;
esac
```

# 3. Loops

```bash
for fruit in Apple Mango Orange; do
 echo $fruit
done
```

```bash
for ((i=1;i<=5;i++)); do
 echo $i
done
```

```bash
while [ $n -gt 0 ]; do
 echo $n
 n=$((n-1))
done
```

```bash
until [ $n -eq 0 ]; do
 n=$((n-1))
done
```

`break` • `continue`

```bash
for file in *.log; do
 echo $file
done
```

```bash
cat users.txt | while read line; do
 echo $line
done
```

# 4. Functions

```bash
greet(){
 echo "Hello $1"
}

greet Ankit
```

```bash
demo(){
 local NAME="DevOps"
 echo $NAME
}
```

`return` returns exit status. `echo` returns output.

# 5. Text Processing

```bash
grep -i error app.log
grep -r error .
grep -n error file
grep -c error file
grep -v error file
grep -E "error|warning"
```

```bash
awk '{print $1}' file
awk -F: '{print $1}' /etc/passwd
```

```bash
sed -i 's/foo/bar/g' file
sed '2d' file
```

```bash
cut -d: -f1 /etc/passwd
sort -n file
sort -r file
sort -u file
uniq -c file
tr a-z A-Z
wc -l file
head -5 file
tail -f app.log
```

# 6. Useful One-Liners

```bash
find /tmp -mtime +30 -delete
wc -l *.log
sed -i 's/old/new/g' *.txt
systemctl is-active nginx
df -h
tail -f app.log | grep ERROR
```

# 7. Error Handling

```bash
echo $?
exit 0
exit 1
```

```bash
set -e
set -u
set -o pipefail
set -x
trap 'echo Cleanup Complete' EXIT
```

# Key Takeaways

- Use functions for reusable code.
- Use `set -euo pipefail` for safer scripts.
- Master grep, awk and sed.
- Automate repetitive tasks.
- Always validate inputs and handle errors.
