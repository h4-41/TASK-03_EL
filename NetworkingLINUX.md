# Networking Commands in Linux

This document explains commonly used Linux networking commands, what they do, when to use them, and how to interpret their output. The focus is on practical understanding for troubleshooting, interviews, and day to day system administration.

---

## ip a

```bash
ip a
```

### Purpose

Displays all network interfaces and their IP address information. This is the modern replacement for `ifconfig`.

### Example Output (shortened)

```text
1: lo: <LOOPBACK,UP,LOWER_UP>
    inet 127.0.0.1/8 scope host lo
2: enp1s0: <NO-CARRIER,BROADCAST,MULTICAST,UP>
3: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP>
    inet 192.168.0.13/24 scope global dynamic
```

### Explanation

* `lo` (loopback): Used for self communication within the system
* `enp*`: Wired Ethernet interface
* `wlp*`: Wireless interface
* `UP`: Interface is enabled
* `LOWER_UP`: Physical or logical link is active
* Interfaces with an IP address and `LOWER_UP` are actively carrying traffic

### When to use

* Check if an interface is up or down
* Verify assigned IP addresses
* Debug connectivity issues

---

## nmcli

```bash
nmcli device status
```

### Purpose

Command line tool to manage and inspect NetworkManager connections.

### Common Uses

```bash
nmcli device show
nmcli connection show
nmcli device wifi list
```

### When to use

* Enable or disable Wi Fi and Ethernet
* Check connection state
* Script network configuration

---

## nmtui

```bash
nmtui
```

### Purpose

Text based user interface for NetworkManager.

### When to use

* Configure Wi Fi without GUI
* Set static IPs easily
* Useful on servers and minimal installations

---

## route

```bash
route -n
```

### Purpose

Displays the kernel routing table. Shows how packets leave the system.

### Key Fields

* Destination: Network to reach
* Gateway: Next hop router
* Iface: Interface used

### Modern Alternative

```bash
ip route
```

---

## ping

```bash
ping google.com
```

### Purpose

Checks basic network connectivity using ICMP.

### What it tells you

* Host reachable or not
* Network latency
* Packet loss

### Common Checks

```bash
ping 127.0.0.1     # Local stack
ping router_ip     # LAN connectivity
ping 8.8.8.8       # Internet connectivity
```

---

## traceroute

```bash
traceroute google.com
```

### Purpose

Shows the path packets take from your system to a destination.

### When to use

* Identify where packets are getting dropped
* Debug slow or failing connections

---

## ifconfig

```bash
ifconfig
```

### Status

Deprecated. Provided by `net-tools`.

### Notes

* Does not show multiple IPs clearly
* Lacks support for modern networking features

### Recommendation

Use `ip a` instead, especially when multiple IPs are assigned.

---

## nslookup

```bash
nslookup example.com
```

### Purpose

Performs DNS queries to resolve domain names.

### When to use

* Quick DNS checks
* Verify which DNS server responds

---

## dig

```bash
dig google.com
```

### Purpose

Advanced DNS query tool.

### What it shows

* Query time
* DNS records
* Authoritative answers

### When to use

* Debug DNS resolution issues
* Inspect record types like A, AAAA, MX, TXT

---

## netstat

```bash
netstat -tulnp
```

### Purpose

Displays network connections, listening ports, and routing tables.

### Status

Deprecated but still widely encountered.

---

## ss

```bash
ss -tulnp
```

### Purpose

Modern replacement for `netstat`. Faster and more accurate.

### When to use

* Check which service is listening on a port
* Inspect active TCP and UDP connections

---

## Command Comparison Summary

| Task               | Recommended Command |
| ------------------ | ------------------- |
| Show interfaces    | ip a                |
| Manage connections | nmcli / nmtui       |
| View routes        | ip route            |
| Test connectivity  | ping                |
| Trace network path | traceroute          |
| DNS debugging      | dig                 |
| Open ports         | ss                  |

---


