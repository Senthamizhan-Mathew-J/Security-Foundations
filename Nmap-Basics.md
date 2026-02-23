
# Nmap Scanning Analysis

This document contains various Nmap scanning techniques performed in a controlled lab environment. The objective was to understand host discovery, port scanning methods, service enumeration, and script-based scanning.

Target systems scanned were local lab machines and virtual machines within a private network range.

---

## 1. Host Discovery Techniques

### TCP SYN Ping (-PS)

Command used:

```bash
nmap -PS 192.168.X.X
```

Description:

This scan sends TCP SYN packets to discover whether a host is alive. If the target responds with SYN-ACK or RST, the host is considered active.

Purpose:

Used before full port scanning to identify live systems in a network.

---

### UDP Ping (-PU)

Command used:

```bash
nmap -PU 192.168.X.X
```

Description:

Sends UDP packets to check if a host responds. If a response is received, the host is considered active.

Purpose:

Useful when ICMP is blocked and TCP-based discovery does not provide results.

---

### CIDR Network Scan

Command used:

```bash
nmap 192.168.X.0/24
```

Description:

Scans an entire subnet to identify active hosts and open ports within the specified network range.

Purpose:

Used for internal network enumeration.

---

## 2. TCP Scanning Techniques

### TCP Connect Scan (-sT)

Command used:

```bash
sudo nmap -sT 192.168.X.X
```

Description:

Performs a full TCP three-way handshake using the operating system’s connect() system call.

Characteristics:

* Reliable
* Slower than SYN scan
* Easily logged by target systems

Use Case:

Used when raw packet privileges are unavailable.

---

### SYN Scan (-sS)

Command used:

```bash
sudo nmap -sS 192.168.X.X
```

Description:

Performs a half-open scan by sending a SYN packet and analyzing the response without completing the full handshake.

Characteristics:

* Faster
* Stealthier than -sT
* Common in security assessments

---

## 3. UDP Scan (-sU)

Command used:

```bash
sudo nmap -sU 192.168.X.X
```

Description:

Scans UDP ports to detect services such as DNS (53), SNMP (161), and others.

Characteristics:

* Slower than TCP scanning
* No handshake process
* Important for discovering non-TCP services

---

## 4. Service and Version Detection (-sV)

Command used:

```bash
sudo nmap -sV 192.168.X.X
```

Description:

Attempts to determine service versions running on open ports.

Purpose:

Helps identify outdated or vulnerable software.

---

## 5. OS Detection (-O)

Command used:

```bash
sudo nmap -O 192.168.X.X
```

Description:

Uses TCP/IP stack fingerprinting to estimate the operating system of the target host.

Note:

Results are probabilistic and may not be 100% accurate.

---

## 6. Aggressive Scan (-A)

Command used:

```bash
sudo nmap -A 192.168.X.X
```

Description:

Enables:

* OS detection
* Version detection
* Script scanning
* Traceroute

Observation:

This scan is comprehensive but noisy and easily detectable by intrusion detection systems.

---

## 7. Nmap Scripting Engine (NSE)

### Default Scripts (-sC)

Command used:

```bash
sudo nmap -sC 192.168.X.X
```

Description:

Runs a set of safe default scripts to check for common vulnerabilities and misconfigurations.

---

### Specific Script Usage

Command used:

```bash
sudo nmap --script=http-default 192.168.X.X
```

Description:

Executes specific NSE scripts to gather detailed information about services such as HTTP.

Purpose:

Used for deeper enumeration of services and identifying potential weaknesses.

---

## Security Analysis

The scans revealed open ports and running services on the target systems. Each open port represents a potential attack surface.

Key observations:

* Unnecessary open ports increase exposure.
* Outdated service versions may contain vulnerabilities.
* UDP services are often overlooked but can be exploited.
* Aggressive scans generate detectable traffic patterns.

Understanding different scanning techniques allows proper identification of live hosts, exposed services, and possible misconfigurations in a network environment.

---

