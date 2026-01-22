# TCP vs UDP

## What is TCP (Transmission Control Protocol)

TCP is a connection oriented protocol designed for reliable data transfer between two endpoints.

### Key Characteristics

* Connection oriented (three way handshake)
* Reliable delivery
* Ordered data transfer
* Error checking and retransmission
* Flow control and congestion control

### How TCP Works (Simplified)

1. Client sends SYN
2. Server replies with SYN-ACK
3. Client responds with ACK
4. Connection established

Data is acknowledged. Lost packets are retransmitted.

### Use Cases

* Web browsing (HTTP/HTTPS)
* SSH
* FTP
* Email (SMTP, IMAP, POP3)
* Databases

### Advantages

* Guaranteed delivery
* Data arrives in correct order
* Suitable for critical data

### Disadvantages

* Higher latency
* More overhead
* Slower than UDP

---

## What is UDP (User Datagram Protocol)

UDP is a connectionless protocol focused on speed rather than reliability.

### Key Characteristics

* Connectionless
* No delivery guarantee
* No ordering
* No retransmission
* Minimal overhead

### How UDP Works

* Sender sends packets without checking if receiver is ready
* Receiver processes packets as they arrive
* Lost packets are ignored

### Use Cases

* Video streaming
* Online gaming
* VoIP
* DNS queries
* DHCP

### Advantages

* Low latency
* Fast transmission
* Efficient for real time communication

### Disadvantages

* Packet loss possible
* Data may arrive out of order
* Application must handle errors

---

## TCP vs UDP Comparison

| Feature     | TCP        | UDP            |
| ----------- | ---------- | -------------- |
| Connection  | Yes        | No             |
| Reliability | Guaranteed | Best effort    |
| Ordering    | Preserved  | Not guaranteed |
| Speed       | Slower     | Faster         |
| Overhead    | High       | Low            |
| Use Case    | Accuracy   | Speed          |

---

# What Is a Port

## Definition

A port is a logical communication endpoint used by the operating system to identify which application should receive network traffic.

An IP address identifies a machine.
A port identifies a specific service on that machine.

---

## Port Range

| Range       | Type                      |
| ----------- | ------------------------- |
| 0–1023      | Well known ports          |
| 1024–49151  | Registered ports          |
| 49152–65535 | Dynamic / Ephemeral ports |

---

## Common Ports

| Port | Protocol | Service |
| ---- | -------- | ------- |
| 22   | TCP      | SSH     |
| 80   | TCP      | HTTP    |
| 443  | TCP      | HTTPS   |
| 53   | UDP/TCP  | DNS     |
| 25   | TCP      | SMTP    |
| 3306 | TCP      | MySQL   |

---

## Why Ports Are Needed

Without ports:

* Only one service could run per IP

With ports:

* Multiple services run simultaneously on the same machine

Example:

* Web server on port 80
* SSH on port 22
* Database on port 3306

---

## How Ports Work with TCP and UDP

* TCP and UDP have separate port spaces
* Port 53 TCP and Port 53 UDP are different
* Firewall rules must specify protocol and port

---

## Linux Commands Related to Ports

```bash
ss -tulnp
```

Shows:

* Listening ports
* Protocol (TCP or UDP)
* Associated process

```bash
lsof -i :80
```

Shows which process is using port 80

---
