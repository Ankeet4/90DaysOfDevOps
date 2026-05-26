# Day 11 – File Ownership Challenge

Today I practiced Linux file ownership and group ownership management using `chown` and `chgrp`.

---

# Task 1 – Understanding Ownership

## Check File Ownership

```bash
ls -l
```

Example output:

```bash
-rw-r--r-- 1 user user 0 May 25 10:30 devops-file.txt
```

### What I Learned

Format:
```bash
-rw-r--r-- 1 owner group size date filename
```

- Owner → User who owns the file
- Group → Group associated with the file

The owner has primary control over the file, while group permissions allow shared access between users.

---

# Task 2 – Basic chown Operations

## Create File

```bash
touch devops-file.txt
```

---

## Check Current Ownership

```bash
ls -l devops-file.txt
```

---

## Change Owner to tokyo

```bash
sudo chown tokyo devops-file.txt
```

Used to change the file owner.

---

## Change Owner to berlin

```bash
sudo chown berlin devops-file.txt
```

Used to transfer ownership to another user.

---

## Verify Changes

```bash
ls -l devops-file.txt
```

---

# Task 3 – Basic chgrp Operations

## Create File

```bash
touch team-notes.txt
```

---

## Create Group

```bash
sudo groupadd heist-team
```

Used to create a Linux group.

---

## Check Current Group

```bash
ls -l team-notes.txt
```

---

## Change Group Ownership

```bash
sudo chgrp heist-team team-notes.txt
```

Used to change group ownership of a file.

---

## Verify Group Change

```bash
ls -l team-notes.txt
```

---

# Task 4 – Combined Owner & Group Change

## Create File

```bash
touch project-config.yaml
```

---

## Change Owner and Group Together

```bash
sudo chown professor:heist-team project-config.yaml
```

Used to change both owner and group together.

---

## Create Directory

```bash
mkdir app-logs
```

---

## Change Directory Ownership

```bash
sudo chown berlin:heist-team app-logs
```

Used to change directory ownership.

---

# Task 5 – Recursive Ownership

## Create Directory Structure

```bash
mkdir -p heist-project/vault
mkdir -p heist-project/plans

touch heist-project/vault/gold.txt
touch heist-project/plans/strategy.conf
```

---

## Create Group

```bash
sudo groupadd planners
```

---

## Change Ownership Recursively

```bash
sudo chown -R professor:planners heist-project/
```

Used to recursively change ownership of files and folders.

---

## Verify Ownership

```bash
ls -lR heist-project/
```

---

# Task 6 – Practice Challenge

## Create Groups

```bash
sudo groupadd vault-team
sudo groupadd tech-team
```

---

## Create Directory

```bash
mkdir bank-heist
```

---

## Create Files

```bash
touch bank-heist/access-codes.txt
touch bank-heist/blueprints.pdf
touch bank-heist/escape-plan.txt
```

---

## Set Different Ownership

### access-codes.txt

```bash
sudo chown tokyo:vault-team bank-heist/access-codes.txt
```

---

### blueprints.pdf

```bash
sudo chown berlin:tech-team bank-heist/blueprints.pdf
```

---

### escape-plan.txt

```bash
sudo chown nairobi:vault-team bank-heist/escape-plan.txt
```

---

## Verify Ownership

```bash
ls -l bank-heist/
```

---

# Files & Directories Created

## Files
- devops-file.txt
- team-notes.txt
- project-config.yaml
- access-codes.txt
- blueprints.pdf
- escape-plan.txt

## Directories
- app-logs
- heist-project
- bank-heist

---

# Ownership Changes

- devops-file.txt → user:user → tokyo:user → berlin:user
- team-notes.txt → user:user → user:heist-team
- project-config.yaml → user:user → professor:heist-team
- app-logs → user:user → berlin:heist-team
- heist-project → user:user → professor:planners
- access-codes.txt → tokyo:vault-team
- blueprints.pdf → berlin:tech-team
- escape-plan.txt → nairobi:vault-team

---

# Commands Used

```bash
ls -l
chown
chgrp
groupadd
mkdir
touch
ls -lR
```

---

# What I Learned

- Difference between file owner and group
- How to change ownership using `chown`
- How to change group ownership using `chgrp`
- How recursive ownership works with `-R`
- Importance of ownership in Linux security and access control
