# Day 08 – Cloud Server Setup: Docker, Nginx & Web Deployment

## Objective

Today I learned how to deploy and manage a real cloud server using AWS EC2.  
I connected to the server using SSH, installed Docker and Nginx, configured security groups for web access, monitored logs, and verified the website from the internet.

---

# Part 1 – Launch Cloud Instance & SSH Access

## Step 1: Create EC2 Instance

- Logged into AWS Console
- Opened EC2 Dashboard
- Launched Ubuntu EC2 instance
- Selected `t2.micro`
- Created/downloaded SSH key pair
- Allowed:
  - SSH (Port 22)
  - HTTP (Port 80)

---

## Step 2: Connect via SSH

### Command Used

```bash
ssh -i "myinstance.pem" ubuntu@ec2-54-90-216-107.compute-1.amazonaws.com
```

### Successful SSH Connection

```text
Welcome to Ubuntu 24.04 LTS
```

📸 Screenshot Added:
- SSH connection to EC2 instance

---

# Part 2 – Install Docker & Nginx

## Step 1: Update System

```bash
sudo apt update && sudo apt upgrade -y
```

---

## Step 2: Install Docker

### Install Docker

```bash
sudo apt install docker.io -y
```

### Start Docker

```bash
sudo systemctl start docker
```

### Enable Docker at Boot

```bash
sudo systemctl enable docker
```

### Verify Docker

```bash
docker --version
```

---

## Step 3: Install Nginx

### Install Nginx

```bash
sudo apt install nginx -y
```

### Start Nginx

```bash
sudo systemctl start nginx
```

### Enable Nginx at Boot

```bash
sudo systemctl enable nginx
```

### Verify Nginx Status

```bash
sudo systemctl status nginx
```

Output:

```text
active (running)
```

---

# Part 3 – Security Group Configuration

Configured EC2 Security Group Rules:

| Type | Port |
|------|------|
| SSH | 22 |
| HTTP | 80 |

---

# Test Web Access

Opened browser and visited:

```text
http://54.90.216.107
```

Successfully viewed the default Nginx welcome page from the internet.

📸 Screenshot Added:
- Nginx welcome page in browser

---

# Part 4 – Extract Nginx Logs

## Step 1: View Nginx Logs

### Command Used

```bash
sudo tail -f /var/log/nginx/access.log
```

### Output

```text
113.21.79.13 - - [23/May/2026:16:56:28 +0000] "GET / HTTP/1.1" 200 409 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/147.0.0.0 Safari/537.36"

113.21.79.13 - - [23/May/2026:16:56:29 +0000] "GET /favicon.ico HTTP/1.1" 404 197 "http://54.90.216.107/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/147.0.0.0 Safari/537.36"
```

### Log Explanation

- `200` = successful HTTP request
- `404` = favicon not found (normal for default Nginx page)
- Logs confirm public access to the web server

📸 Screenshot Added:
- Nginx log monitoring in terminal

---

## Step 2: Save Logs to File

```bash
sudo cp /var/log/nginx/access.log ~/nginx-logs.txt
```

### Verify Log File

```bash
cat ~/nginx-logs.txt
```

---

## Step 3: Download Logs to Local Machine

### Command Used

```bash
scp -i myinstance.pem ubuntu@54.90.216.107:~/nginx-logs.txt .
```

Successfully downloaded the log file to local system.

---

# Commands Used

```bash
ssh -i "myinstance.pem" ubuntu@ec2-54-90-216-107.compute-1.amazonaws.com

sudo apt update && sudo apt upgrade -y

sudo apt install docker.io -y

sudo systemctl start docker

sudo systemctl enable docker

docker --version

sudo apt install nginx -y

sudo systemctl start nginx

sudo systemctl enable nginx

sudo systemctl status nginx

sudo tail -f /var/log/nginx/access.log

sudo cp /var/log/nginx/access.log ~/nginx-logs.txt

cat ~/nginx-logs.txt

scp -i myinstance.pem ubuntu@54.90.216.107:~/nginx-logs.txt .
```

---

# Challenges Faced

## 1. SSH Authentication Errors

Issue:

```text
Permission denied (publickey)
```

Solution:

```bash
chmod 400 myinstance.pem
```

---

## 2. Website Not Accessible

Issue:
- Nginx page not opening in browser

Solution:
- Allowed HTTP Port 80 in AWS Security Group

---

## 3. Understanding Public vs Private IP

Learned:
- Public IP is accessible from internet
- Private IP is used inside AWS internal network

---

# What I Learned

- How to launch and connect to AWS EC2 instances
- How SSH authentication works using `.pem` keys
- How to install and manage Docker and Nginx
- How to configure Security Groups for web access
- How to monitor Nginx logs in real-time
- How to extract and download server log files
- Difference between public and private IP addresses
- Basic real-world cloud server administration workflow



