# Day 15 – Networking Concepts: DNS, IP, Subnets & Ports

## Objective

Today I focused on learning the networking concepts that are used every day in DevOps. I learned how DNS works, how IP addresses are assigned, what CIDR notation means, why subnetting is important, and how ports help different services communicate.

---

# Task 1 – DNS (How Names Become IP Addresses)

When I type **google.com** in my browser, my computer first sends a DNS request to find the IP address of that domain. After getting the IP address, the browser connects to Google's server and loads the website.

## DNS Record Types

* **A Record** – Maps a domain name to an IPv4 address.
* **AAAA Record** – Maps a domain name to an IPv6 address.
* **CNAME Record** – Points one domain to another domain.
* **MX Record** – Specifies the mail server for a domain.
* **NS Record** – Shows which DNS servers manage the domain.

### Command Used

```bash
dig google.com
```

### Observation

From the output, I found:

* **A Record** – Displays Google's IPv4 address.
* **TTL** – Shows how long the DNS response will be cached before it expires.

---

# Task 2 – IP Addressing

## What is an IPv4 Address?

An IPv4 address is a unique address that identifies a device on a network. It consists of four numbers separated by dots.

Example:

```
192.168.1.10
```

## Public IP vs Private IP

### Public IP

* Used on the internet.
* Accessible from anywhere.

Example:

```
8.8.8.8
```

### Private IP

* Used inside private or local networks.
* Cannot be accessed directly from the internet.

Example:

```
192.168.1.20
```

## Private IP Ranges

* `10.0.0.0 – 10.255.255.255`
* `172.16.0.0 – 172.31.255.255`
* `192.168.0.0 – 192.168.255.255`

### Command Used

```bash
ip addr show
```

### Observation

I checked my system's IP address and confirmed that it belongs to the private IP range.

---

# Task 3 – CIDR & Subnetting

## What does /24 mean?

A **/24** means the first 24 bits are used for the network, and the remaining 8 bits are available for host devices.

## Usable Hosts

| CIDR | Usable Hosts |
| ---- | -----------: |
| /24  |          254 |
| /16  |       65,534 |
| /28  |           14 |

## Why Do We Use Subnetting?

Subnetting divides a large network into smaller networks. It helps reduce unnecessary traffic, improves security, and makes network management easier.

### CIDR Table

| CIDR | Subnet Mask     | Total IPs | Usable Hosts |
| ---- | --------------- | --------: | -----------: |
| /24  | 255.255.255.0   |       256 |          254 |
| /16  | 255.255.0.0     |    65,536 |       65,534 |
| /28  | 255.255.255.240 |        16 |           14 |

---

# Task 4 – Ports

## What is a Port?

A port is a communication endpoint used by applications. It allows multiple services to run on the same machine without interfering with each other.

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

### Command Used

```bash
ss -tulpn
```

### Observation

I found that SSH was listening on **port 22**. I also checked another running service and matched its listening port.

---

# Task 5 – Putting Everything Together

### Scenario 1

When I run:

```bash
curl http://myapp.com:8080
```

First, DNS converts **myapp.com** into an IP address. Then TCP establishes the connection, IP routes the packets, and the request reaches the application running on **port 8080**.

---

### Scenario 2

If my application cannot connect to the database at:

```
10.0.1.50:3306
```

The first things I would check are:

* Is the database service running?
* Is port **3306** open and listening?
* Can I reach the server using `ping`?
* Is the firewall or security group blocking the connection?

---

# Commands Used

```bash
dig google.com

ip addr show

ss -tulpn
```

---

# What I Learned

* I learned how DNS converts domain names into IP addresses.
* I understood the difference between public and private IP addresses.
* I learned how CIDR notation and subnetting help organize networks.
* I revised some common ports used by popular services.
* I understood how DNS, IP addresses, TCP, and ports work together during network communication.

---
