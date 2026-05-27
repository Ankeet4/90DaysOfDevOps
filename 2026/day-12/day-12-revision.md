# Day 12 – Breather & Revision (Days 01–11)

Today I revised Linux fundamentals from Days 01–11 and practiced a few important commands again to improve retention and confidence.

---

# Revision Notes

## Day 01 – DevOps Learning Plan
I reviewed my DevOps roadmap and confirmed that my goal is still to become a Cloud/DevOps Engineer by building strong Linux, Cloud, and automation fundamentals.

---

# Processes & Services Revision

## Check Running Processes

```bash
ps aux | head
```

### What I Observed
Displayed running processes and their CPU/memory usage.

---

## Check SSH Service Status

```bash
systemctl status ssh
```

### What I Observed
SSH service was active and running normally.

---

## View SSH Logs

```bash
journalctl -u ssh -n 20
```

### What I Observed
Viewed recent SSH login and service logs.

---

# File Skills Revision

## Append Text into File

```bash
echo "Revision practice" >> notes.txt
```

### Use
Appends text into an existing file.

---

## Change File Permission

```bash
chmod 640 notes.txt
```

### Use
Sets custom read/write permissions.

---

## Check File Ownership

```bash
ls -l notes.txt
```

### Use
Displays file permissions, owner, and group.

---

## Change File Ownership

```bash
sudo chown tokyo:developers notes.txt
```

### Use
Changes both owner and group of a file.

---

## Create Directory

```bash
mkdir revision-practice
```

### Use
Creates a new directory.

---

# Top 5 Commands I Would Use During an Incident

## top
Used for live CPU and memory monitoring.

## journalctl -u ssh -f
Used for monitoring service logs in real time.

## systemctl status ssh
Used to check service health.

## ls -l
Used to verify permissions and ownership.

## df -h
Used to check disk space usage.

---

# User & Group Revision

## Create Test User

```bash
sudo useradd -m testuser
```

### Use
Creates a user with home directory.

---

## Verify User Information

```bash
id testuser
```

### Use
Displays user ID and group information.

---

## Verify Ownership

```bash
ls -l
```

### Use
Checks ownership and permissions of files.

---

# Mini Self-Check

## 1. Which 3 commands save you the most time right now, and why?

### top
Quickly checks system performance and CPU usage.

### systemctl status
Helps verify whether a service is running correctly.

### ls -l
Useful for checking permissions and ownership issues.

---

## 2. How do you check if a service is healthy?

Commands I would run first:

```bash
systemctl status ssh
journalctl -u ssh -n 20
ps aux | grep ssh
```

---

## 3. How do you safely change ownership and permissions?

Example command:

```bash
sudo chown tokyo:developers notes.txt
chmod 640 notes.txt
```

Used to safely manage ownership and access permissions.

---

## 4. What will you focus on improving in the next 3 days?

- More Linux troubleshooting practice
- Better understanding of permissions and ownership
- Learning shell scripting basics
- Improving command-line confidence

