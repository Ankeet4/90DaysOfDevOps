# Day 18 – Shell Scripting: Functions & Intermediate Concepts

## Task 1: Basic Functions

### functions.sh

```bash
#!/bin/bash

greet() {
    echo "Hello, $1!"
}

add() {
    echo "Sum: $(($1 + $2))"
}

greet "Ankit"
add 10 20
```

### Output

```text
Hello, Ankit!
Sum: 30
```

---

## Task 2: Functions with Return Values

### disk_check.sh

```bash
#!/bin/bash

check_disk() {
    echo "Disk Usage:"
    df -h /
}

check_memory() {
    echo "Memory Usage:"
    free -h
}

check_disk
echo
check_memory
```

### Output

```text
Disk Usage:
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        50G   12G   36G  25% /

Memory Usage:
              total   used   free
Mem:           7.6G   2.1G   4.3G
```

---

## Task 3: Strict Mode

### strict_demo.sh

```bash
#!/bin/bash

set -euo pipefail

echo "Strict mode enabled"

NAME="DevOps"
echo $NAME
```

### Explanation

```text
set -e          → Exit immediately if a command fails
set -u          → Exit if an undefined variable is used
set -o pipefail → Fail if any command in a pipeline fails
```

### Example

```bash
echo $UNDEFINED_VAR
```

Output:

```text
unbound variable
```

---

## Task 4: Local Variables

### local_demo.sh

```bash
#!/bin/bash

demo_local() {
    local NAME="Local Variable"
    echo $NAME
}

demo_global() {
    NAME="Global Variable"
}

demo_local
echo "Outside function: ${NAME:-Not Available}"

demo_global
echo "Outside function: $NAME"
```

### Output

```text
Local Variable
Outside function: Not Available
Outside function: Global Variable
```

---

## Task 5: System Information Reporter

### system_info.sh

```bash
#!/bin/bash

set -euo pipefail

system_info() {
    echo "===== SYSTEM INFO ====="
    hostname
    uname -a
}

uptime_info() {
    echo
    echo "===== UPTIME ====="
    uptime
}

disk_info() {
    echo
    echo "===== DISK USAGE ====="
    df -h | head -5
}

memory_info() {
    echo
    echo "===== MEMORY USAGE ====="
    free -h
}

cpu_info() {
    echo
    echo "===== TOP CPU PROCESSES ====="
    ps aux --sort=-%cpu | head -6
}

main() {
    system_info
    uptime_info
    disk_info
    memory_info
    cpu_info
}

main
```

### Sample Output

```text
===== SYSTEM INFO =====
ubuntu-server
Linux ubuntu-server 6.x.x

===== UPTIME =====
up 3 hours, 20 minutes

===== DISK USAGE =====
Filesystem Size Used Avail Use%

===== MEMORY USAGE =====
Mem: 7.6G 2.0G 4.5G

===== TOP CPU PROCESSES =====
USER PID %CPU COMMAND
root 1234 15.0 nginx
```

---

## Commands Used

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

## What I Learned

1. Functions help make shell scripts modular and reusable.
2. Local variables stay inside functions and avoid conflicts.
3. Strict mode (set -euo pipefail) makes scripts safer and easier to debug.
