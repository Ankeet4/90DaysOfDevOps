# Day 09 – Linux User & Group Management Challenge

Today I practiced Linux user management, group management, permissions, and shared directory setup.

---

# Users & Groups Created

## Users
- tokyo
- berlin
- professor
- nairobi

## Groups
- developers
- admins
- project-team

---

# User Creation Commands

## Create Users

```bash
sudo useradd -m tokyo
sudo useradd -m berlin
sudo useradd -m professor
sudo useradd -m nairobi
```

### Use
Creates users with home directories.

---

## Set Passwords

```bash
sudo passwd tokyo
sudo passwd berlin
sudo passwd professor
sudo passwd nairobi
```

### Use
Sets password for users.

---

## Verify Users

```bash
cat /etc/passwd
```

### Use
Displays all system users.

---

## Check Home Directories

```bash
ls -l /home
```

### Use
Displays user home directories.

---

# Group Creation Commands

## Create Groups

```bash
sudo groupadd developers
sudo groupadd admins
sudo groupadd project-team
```

### Use
Creates Linux groups.

---

## Verify Groups

```bash
cat /etc/group
```

### Use
Displays all groups in the system.

---

# Group Assignment Commands

## Add Users to Groups

```bash
sudo usermod -aG developers tokyo
sudo usermod -aG developers,admins berlin
sudo usermod -aG admins professor
sudo usermod -aG project-team nairobi
sudo usermod -aG project-team tokyo
```

### Use
Adds users to one or multiple groups.

---

## Verify Group Membership

```bash
groups tokyo
groups berlin
groups professor
groups nairobi
```

### Use
Displays groups assigned to users.

---

# Shared Directory Setup

## Create Shared Directory

```bash
sudo mkdir -p /opt/dev-project
```

### Use
Creates shared project directory.

---

## Change Group Ownership

```bash
sudo chgrp developers /opt/dev-project
```

### Use
Assigns developers group ownership to directory.

---

## Set Permissions

```bash
sudo chmod 775 /opt/dev-project
```

### Use
Gives read/write/execute access to owner and group.

---

## Verify Permissions

```bash
ls -ld /opt/dev-project
```

### Use
Checks directory permissions and ownership.

---

## Test File Creation

```bash
sudo -u tokyo touch /opt/dev-project/tokyo-file.txt
sudo -u berlin touch /opt/dev-project/berlin-file.txt
```

### Use
Tests whether users can create files inside shared directory.

---

# Team Workspace Setup

## Create Team Workspace Directory

```bash
sudo mkdir -p /opt/team-workspace
```

### Use
Creates team collaboration directory.

---

## Assign Group Ownership

```bash
sudo chgrp project-team /opt/team-workspace
```

### Use
Assigns project-team group ownership.

---

## Set Permissions

```bash
sudo chmod 775 /opt/team-workspace
```

### Use
Allows group members to access and modify files.

---

## Test Workspace Access

```bash
sudo -u nairobi touch /opt/team-workspace/nairobi-test.txt
```

### Use
Tests file creation inside workspace directory.

---

# Group Assignments

| User | Groups |
|---|---|
| tokyo | developers, project-team |
| berlin | developers, admins |
| professor | admins |
| nairobi | project-team |

---

# Directories Created

| Directory | Group | Permissions |
|---|---|---|
| /opt/dev-project | developers | 775 |
| /opt/team-workspace | project-team | 775 |

---

# What I Learned

- How to create Linux users and groups
- How to assign users to multiple groups
- How Linux permissions work
- How to create shared directories
- How group ownership controls access
- Basic Linux user and permission management workflow
