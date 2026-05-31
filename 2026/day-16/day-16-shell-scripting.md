# Day 16 – Shell Scripting Basics

## Task 1: My First Script

### hello.sh

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

### What Happens if the Shebang is Removed?

The shebang (`#!/bin/bash`) tells Linux which interpreter should execute the script. Without it, the script may not run correctly when executed directly.

---

## Task 2: Variables

### variables.sh

```bash
#!/bin/bash

NAME="Ankit"
ROLE="DevOps Engineer"

echo "Hello, I am $NAME and I am a $ROLE"
```

### Output

```text
Hello, I am Ankit and I am a DevOps Engineer
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
Ankit
```

Single quotes print the text exactly as written, while double quotes expand variables.

---

## Task 3: User Input with read

### greet.sh

```bash
#!/bin/bash

read -p "Enter your name: " NAME
read -p "Enter your favourite tool: " TOOL

echo "Hello $NAME, your favourite tool is $TOOL"
```

### Sample Output

```text
Enter your name: Ankit
Enter your favourite tool: Docker
Hello Ankit, your favourite tool is Docker
```

---

## Task 4: If-Else Conditions

### check_number.sh

```bash
#!/bin/bash

read -p "Enter a number: " NUM

if [ $NUM -gt 0 ]; then
    echo "Positive Number"
elif [ $NUM -lt 0 ]; then
    echo "Negative Number"
else
    echo "Zero"
fi
```

### Sample Output

```text
Enter a number: 10
Positive Number
```

---

### file_check.sh

```bash
#!/bin/bash

read -p "Enter filename: " FILE

if [ -f "$FILE" ]; then
    echo "File exists"
else
    echo "File does not exist"
fi
```

### Sample Output

```text
Enter filename: notes.txt
File exists
```

---

## Task 5: Combine It All

### server_check.sh

```bash
#!/bin/bash

SERVICE="ssh"

read -p "Do you want to check the status? (y/n): " CHOICE

if [ "$CHOICE" = "y" ]; then
    systemctl is-active $SERVICE
else
    echo "Skipped."
fi
```

### Sample Output

```text
Do you want to check the status? (y/n): y
active
```

---

## Commands Used

```bash
chmod +x hello.sh
./hello.sh

chmod +x variables.sh
./variables.sh

chmod +x greet.sh
./greet.sh

chmod +x check_number.sh
./check_number.sh

chmod +x file_check.sh
./file_check.sh

chmod +x server_check.sh
./server_check.sh
```

---

## What I Learned

1. The shebang line (`#!/bin/bash`) tells Linux which shell should execute the script.
2. Variables and the `read` command allow scripts to take user input.
3. If-else conditions help automate decision-making inside shell scripts.
