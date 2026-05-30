# Day 15 – Networking Concepts: DNS, IP, Subnets & Ports

Today I learned the core networking concepts that every DevOps engineer should understand, including DNS, IP addressing, subnetting, CIDR notation, and common network ports.

---

# Task 1 – DNS: How Names Become IPs

When I type `google.com` into a browser, my computer sends a DNS query to a DNS server. The DNS server returns the IP address associated with the domain name. The browser then connects to that IP address and loads the website.

## DNS Record Types

### A Record

Maps a domain name to an IPv4 address.

### AAAA Record

Maps a domain name to an IPv6 address.

### CNAME Record

Creates an alias from one domain name to another.

### MX Record

Specifies mail servers for receiving emails.

### NS Record

Specifies the authoritative name servers for a domain.

## Command Used

```bash
dig google.com
```

### Observation

The A record returned Google's public IP address along with TTL information.

---

# Task 2 – IP Addressing

## What is an IPv4 Address?

An IPv4 address is a 32-bit address used to identify devices on a network.

Example:

```text
192.168.1.10
```

## Public vs Private IP

### Public IP

Accessible from the internet.

Example:

```text
8.8.8.8
```

### Private IP

Used inside local networks.

Example:

```text
192.168.1.10
```

## Private IP Ranges

```text
10.0.0.0 – 10.255.255.255
172.16.0.0 – 172.31.255.255
192.168.0.0 – 192.168.255.255
```

## Command Used

```bash
ip addr show
```

### Observation

My system IP belongs to a private IP range.

---

# Task 3 – CIDR & Subnetting

## What Does /24 Mean?

A /24 means the first 24 bits represent the network portion and the remaining 8 bits represent hosts.

## Why Do We Subnet?

Subnetting helps organize networks, improve security, and efficiently use IP addresses.

## CIDR Table

| CIDR | Subnet Mask     | Total IPs | Usable Hosts |
| ---- | --------------- | --------- | ------------ |
| /24  | 255.255.255.0   | 256       | 254          |
| /16  | 255.255.0.0     | 65,536    | 65,534       |
| /28  | 255.255.255.240 | 16        | 14           |

---

# Task 4 – Ports: The Doors to Services

A port is a logical communication endpoint that allows multiple services to run on the same IP address.

## Common Ports

| Port  | Service |
| ----- | ------- |
| 22    | SSH     |
| 80    | HTTP    |
| 443   | HTTPS   |
| 53    | DNS     |
| 3306  | MySQL   |
| 6379  | Redis   |
| 27017 | MongoDB |

## Command Used

```bash
ss -tulpn
```

### Observation

Found listening services and the ports they use.

Example:

```text
22 → SSH
53 → DNS
```

---

# Task 5 – Putting It Together

## curl http://myapp.com:8080

DNS resolves the domain name to an IP address. The browser connects using TCP/IP and communicates with the service running on port 8080.

## App Cannot Reach Database at 10.0.1.50:3306

First I would check:

* Network connectivity using ping
* Whether MySQL is listening on port 3306
* Firewall or security group rules
* Database service status

---

# Commands Practiced

```bash
dig google.com
ip addr show
ss -tulpn
```

---

# What I Learned

* How DNS converts domain names into IP addresses
* Difference between public and private IP addresses
* Basics of CIDR notation and subnetting
* Importance of ports in networking
* How networking concepts work together in real applications
