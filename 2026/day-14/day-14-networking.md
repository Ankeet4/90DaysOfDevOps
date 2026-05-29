Today I practiced Linux networking commands and learned basic networking troubleshooting concepts.

---

# Quick Concepts

## OSI Model
- Physical → Data Link → Network → Transport → Session → Presentation → Application
- Explains how data travels through a network.

## TCP/IP Model
- Link → Internet → Transport → Application
- Practical networking model used on the internet.

## Protocols and Layers
- IP → Network Layer
- TCP/UDP → Transport Layer
- HTTP/HTTPS → Application Layer
- DNS → Application Layer

## Real Example

```bash
curl https://example.com
```

Application Layer (HTTP/HTTPS) → TCP → IP

---

# Hands-on Networking Checks

## Check IP Address

```bash
hostname -I
```

Use: Shows system IP address.

---

## Detailed Network Information

```bash
ip addr show
```

Use: Displays network interface details.

---

## Reachability Test

```bash
ping google.com
```

Use: Tests connectivity and latency.

### Observation
Packets were received successfully with low latency.

---

## Trace Network Path

```bash
traceroute google.com
```

Use: Shows route packets take to destination.

---

## Check Listening Ports

```bash
ss -tulpn
```

Use: Displays listening services and ports.

### Observation
Found services listening on local ports.

---

## DNS Lookup

```bash
dig google.com
```

Use: Resolves domain to IP address.

---

## HTTP Header Check

```bash
curl -I https://google.com
```

Use: Checks HTTP response status and headers.

### Observation
Received HTTP 200 response.

---

## Connections Snapshot

```bash
netstat -an | head
```

Use: Displays active network connections.

---

# Mini Task – Port Probe

## Check Local Port

```bash
nc -zv localhost 22
```

Use: Tests whether port is reachable.

### Observation
Port 22 was reachable.

### If Not Reachable
Next checks:
```bash
systemctl status ssh
journalctl -u ssh
```

---

# Reflection

## Fastest Troubleshooting Command

```bash
ping
```

Quickly checks basic network connectivity.

---

## If DNS Fails
Check DNS/Application Layer.

---

## If HTTP 500 Error Appears
Check Application Layer and service logs.

---

## Follow-up Checks During Incident

```bash
systemctl status <service>
journalctl -u <service>
```

Used for service troubleshooting.

---

# Commands Practiced

```bash
hostname -I
ip addr show
ping
traceroute
ss -tulpn
dig
curl -I
netstat -an
nc -zv
```

---

# What I Learned

- Basic Linux networking troubleshooting
- Difference between OSI and TCP/IP models
- How to test connectivity and DNS
- How to check listening ports and HTTP responses
- Importance of networking fundamentals in DevOps

