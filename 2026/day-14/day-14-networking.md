# Day 14 – Networking Fundamentals & Hands-on Checks

## Objective

Today I learned the basic networking concepts that every Linux and DevOps engineer should know. I also practiced some networking commands to check connectivity, DNS, ports, and HTTP responses. These commands are very useful while troubleshooting servers and network problems.

---

# OSI Model vs TCP/IP Model

## OSI Model (7 Layers)

* Physical Layer – Transfers data through cables and hardware.
* Data Link Layer – Communicates between devices on the same network.
* Network Layer – Uses IP addresses to send data between networks.
* Transport Layer – Uses TCP or UDP for communication.
* Session Layer – Creates and manages communication sessions.
* Presentation Layer – Handles encryption and data formatting.
* Application Layer – Used by applications like HTTP, HTTPS, DNS, FTP, and SSH.

## TCP/IP Model (4 Layers)

* Link Layer
* Internet Layer
* Transport Layer
* Application Layer

### My Understanding

The OSI model explains networking in detail, while the TCP/IP model is the practical model used on the internet. Both models describe how data travels from one device to another.

---

# Where Different Protocols Work

* **IP** → Internet (Network) Layer
* **TCP / UDP** → Transport Layer
* **HTTP / HTTPS** → Application Layer
* **DNS** → Application Layer

### Real Example

When I run:

```bash
curl https://example.com
```

The request starts at the **Application Layer (HTTP/HTTPS)**, then uses **TCP** to create a connection, and finally **IP** sends the packets to the destination server.

---

# Hands-on Practice

## 1. Check My IP Address

### Command

```bash
hostname -I
```

or

```bash
ip addr show
```

### Observation

This command displayed the IP address assigned to my machine. It helps me identify my system on the network.

---

## 2. Check Network Connectivity

### Command

```bash
ping google.com
```

### Observation

The ping command returned replies with low latency and no packet loss. This confirmed that my internet connection was working properly.

---

## 3. Check the Network Path

### Command

```bash
traceroute google.com
```

or

```bash
tracepath google.com
```

### Observation

The output showed the routers (hops) between my machine and Google. A few hops took slightly longer, but the destination was reached successfully.

---

## 4. Check Listening Ports

### Command

```bash
ss -tulpn
```

### Observation

I found that the SSH service was listening on **port 22**, which means the server is ready to accept SSH connections.

---

## 5. Check DNS Resolution

### Command

```bash
dig google.com
```

or

```bash
nslookup google.com
```

### Observation

The domain name was successfully converted into an IP address. This confirmed that DNS was working correctly.

---

## 6. Check HTTP Response

### Command

```bash
curl -I https://google.com
```

### Observation

The response returned an HTTP status code like **200 OK** or **301 Moved Permanently**, which means the web server responded successfully.

---

## 7. Check Active Connections

### Command

```bash
netstat -an | head
```

### Observation

I saw both **LISTEN** and **ESTABLISHED** connections. LISTEN means a service is waiting for requests, while ESTABLISHED means two systems are actively communicating.

---

# Mini Task – Port Probe

First, I checked which ports were listening.

```bash
ss -tulpn
```

Then I tested the SSH port.

```bash
nc -zv localhost 22
```

### Observation

The port was reachable, which means the SSH service was running correctly.

If the port had not been reachable, I would have checked:

* Whether the service was running using `systemctl status`
* Firewall settings
* Listening ports again using `ss -tulpn`

---

# Reflection

### Which command gives me the fastest signal when something is broken?

I usually use the **ping** command first because it quickly tells me if the destination is reachable.

### What layer would I check if DNS fails?

I would first check the **Application Layer** because DNS works there. Then I would verify the network connection and DNS configuration.

### What if I receive an HTTP 500 error?

An HTTP 500 error usually points to an application or web server problem. I would check the application logs and web server logs first.

### Two follow-up checks I would run during a real incident

* Check the service status using `systemctl status`.
* Check logs using `journalctl` or the application's log files.

---

# Commands Used

```bash
hostname -I

ip addr show

ping google.com

traceroute google.com

tracepath google.com

ss -tulpn

dig google.com

nslookup google.com

curl -I https://google.com

netstat -an | head

nc -zv localhost 22
```

---

# What I Learned

* I understood the difference between the OSI model and the TCP/IP model.
* I practiced important networking commands that are useful in Linux.
* I learned how to check connectivity, DNS, ports, and HTTP responses.
* I understood how these commands help during troubleshooting.
* Networking knowledge is an important skill for every DevOps engineer.

---

