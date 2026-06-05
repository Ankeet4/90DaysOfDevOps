# Day 19 – Shell Scripting Project: Log Rotation, Backup & Crontab

## Task 1: Log Rotation Script

### log_rotate.sh

```bash
#!/bin/bash

LOG_DIR=$1

if [ ! -d "$LOG_DIR" ]; then
    echo "Error: Directory does not exist"
    exit 1
fi

compressed=$(find "$LOG_DIR" -name "*.log" -mtime +7 | wc -l)
find "$LOG_DIR" -name "*.log" -mtime +7 -exec gzip {} \;

deleted=$(find "$LOG_DIR" -name "*.gz" -mtime +30 | wc -l)
find "$LOG_DIR" -name "*.gz" -mtime +30 -delete

echo "Compressed files: $compressed"
echo "Deleted files: $deleted"
```

### Sample Output

```text
Compressed files: 5
Deleted files: 2
```

---

## Task 2: Server Backup Script

### backup.sh

```bash
#!/bin/bash

SOURCE=$1
DEST=$2

if [ ! -d "$SOURCE" ]; then
    echo "Source directory does not exist"
    exit 1
fi

mkdir -p "$DEST"

DATE=$(date +%Y-%m-%d)
ARCHIVE="$DEST/backup-$DATE.tar.gz"

tar -czf "$ARCHIVE" "$SOURCE"

if [ -f "$ARCHIVE" ]; then
    echo "Backup created successfully"
    ls -lh "$ARCHIVE"
else
    echo "Backup failed"
    exit 1
fi

find "$DEST" -name "*.tar.gz" -mtime +14 -delete
```

### Sample Output

```text
Backup created successfully
-rw-r--r-- 1 root root 25M Jun 5 backup-2026-06-05.tar.gz
```

---

## Task 3: Crontab

### Current Scheduled Jobs

```bash
crontab -l
```

### Cron Entries

Run log rotation every day at 2 AM:

```cron
0 2 * * * /home/ankit/log_rotate.sh /var/log/myapp
```

Run backup every Sunday at 3 AM:

```cron
0 3 * * 0 /home/ankit/backup.sh /home/ankit/data /backup
```

Run health check every 5 minutes:

```cron
*/5 * * * * /home/ankit/health_check.sh
```

---

## Task 4: Scheduled Maintenance Script

### maintenance.sh

```bash
#!/bin/bash

LOGFILE="/var/log/maintenance.log"

echo "$(date): Maintenance Started" >> $LOGFILE

/home/ankit/log_rotate.sh /var/log/myapp >> $LOGFILE 2>&1

/home/ankit/backup.sh /home/ankit/data /backup >> $LOGFILE 2>&1

echo "$(date): Maintenance Completed" >> $LOGFILE
```

### Cron Entry

Run daily at 1 AM:

```cron
0 1 * * * /home/ankit/maintenance.sh
```

### Sample Log Output

```text
Thu Jun 05 01:00:00 UTC 2026: Maintenance Started
Compressed files: 3
Deleted files: 1
Backup created successfully
Thu Jun 05 01:01:10 UTC 2026: Maintenance Completed
```

---

## Commands Used

```bash
chmod +x log_rotate.sh
./log_rotate.sh /var/log

chmod +x backup.sh
./backup.sh /home/ankit/data /backup

crontab -l

chmod +x maintenance.sh
./maintenance.sh
```

---

## What I Learned

1. Log rotation helps manage disk space by compressing and removing old logs.
2. Automated backups protect important data and can be scheduled using cron.
3. Cron jobs allow regular maintenance tasks to run automatically without manual intervention.
