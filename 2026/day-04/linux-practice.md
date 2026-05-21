# Day 04 – Linux Practice: Processes and Services

Today I practiced some Linux fundamentals related to processes, services, and logs. I used different commands to monitor running processes, inspect systemd services, and check logs for troubleshooting.

---

# Process Checks

## ps aux | head
This command shows currently running processes in the system along with CPU and memory usage.

## top
This command is used for live monitoring of system processes, CPU usage, memory usage, and load average.

---

# Service Checks

## systemctl status ssh
I used this command to check the status of the SSH service. It showed whether the service was active and running correctly.

## systemctl list-units --type=service
This command displayed all active services managed by systemd.

---

# Log Checks

## journalctl -u ssh -n 20
This command displayed the latest logs related to the SSH service. It is useful for troubleshooting login or service issues.

## tail -n 50 /var/log/syslog
This command showed the latest 50 lines from the system log file.

---

# Mini Troubleshooting Steps

First, I checked running processes using:
```bash
ps aux


Then I checked whether the SSH service was running properly:
systemctl status ssh

After that, I checked SSH logs for any errors:
journalctl -u ssh -n 20

The service was active and running without issues.
