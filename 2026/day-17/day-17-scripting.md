# Day 17 – Shell Scripting: Loops, Arguments & Error Handling

## Task 1: For Loop

### for_loop.sh

```bash
#!/bin/bash

for fruit in Apple Banana Mango Orange Grapes
do
    echo $fruit
done
```

### Output

```text
Apple
Banana
Mango
Orange
Grapes
```

---

### count.sh

```bash
#!/bin/bash

for i in {1..10}
do
    echo $i
done
```

### Output

```text
1
2
3
4
5
6
7
8
9
10
```

---

## Task 2: While Loop

### countdown.sh

```bash
#!/bin/bash

read -p "Enter a number: " num

while [ $num -ge 0 ]
do
    echo $num
    num=$((num-1))
done

echo "Done!"
```

### Sample Output

```text
Enter a number: 5
5
4
3
2
1
0
Done!
```

---

## Task 3: Command-Line Arguments

### greet.sh

```bash
#!/bin/bash

if [ $# -eq 0 ]
then
    echo "Usage: ./greet.sh <name>"
else
    echo "Hello, $1!"
fi
```

### Sample Output

```text
$ ./greet.sh Ankit
Hello, Ankit!
```

---

### args_demo.sh

```bash
#!/bin/bash

echo "Script Name: $0"
echo "Total Arguments: $#"
echo "Arguments: $@"
```

### Sample Output

```text
$ ./args_demo.sh hello devops linux

Script Name: ./args_demo.sh
Total Arguments: 3
Arguments: hello devops linux
```

---

## Task 4: Install Packages via Script

### install_packages.sh

```bash
#!/bin/bash

if [ "$EUID" -ne 0 ]
then
    echo "Please run as root"
    exit 1
fi

packages=("nginx" "curl" "wget")

for pkg in "${packages[@]}"
do
    if dpkg -s "$pkg" &>/dev/null
    then
        echo "$pkg is already installed"
    else
        echo "Installing $pkg..."
        apt-get update
        apt-get install -y "$pkg"
    fi
done
```

### Sample Output

```text
nginx is already installed
curl is already installed
wget is already installed
```

---

## Task 5: Error Handling

### safe_script.sh

```bash
#!/bin/bash

set -e

mkdir /tmp/devops-test || echo "Directory already exists"

cd /tmp/devops-test || {
    echo "Failed to enter directory"
    exit 1
}

touch demo.txt

echo "File created successfully"
```

### Sample Output

```text
Directory already exists
File created successfully
```

---

## Commands Used

```bash
chmod +x for_loop.sh
./for_loop.sh

chmod +x count.sh
./count.sh

chmod +x countdown.sh
./countdown.sh

chmod +x greet.sh
./greet.sh Ankit

chmod +x args_demo.sh
./args_demo.sh hello devops linux

sudo chmod +x install_packages.sh
sudo ./install_packages.sh

chmod +x safe_script.sh
./safe_script.sh
```

---

## What I Learned

1. For loops and while loops help automate repetitive tasks.
2. Command-line arguments make scripts reusable and flexible.
3. Error handling using set -e and conditional checks improves script reliability.
