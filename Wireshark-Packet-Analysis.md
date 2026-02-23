
# Wireshark Traffic Analysis

This document contains packet captures and analysis performed using Wireshark during basic network monitoring.
Traffic was captured while accessing torbrowser.org. Multiple packets were observed, and the following were analyzed:

1. TCP Three-Way Handshake
2. HTTP
3. DNS
4. ARP

---

## 1. TCP Three-Way Handshake

Filter used:

```
ip.src==192.168.X.X && ip.dst==116.202.120.165 && tcp && !tls
```

Observed Packets:

1. SYN – Client initiates connection
2. SYN-ACK – Server acknowledges request
3. ACK – Client confirms connection

Explanation:

This handshake establishes a reliable communication session between the client and the server before data transfer begins.

The source IP (192.168.X.X) used an ephemeral (temporary) source port (e.g., 35740).
The destination IP (116.202.120.165) responded on its service port.

The client first sends a SYN packet to request a connection.
The server replies with SYN-ACK.
The client then sends ACK to complete the connection.

Some packets were marked as RST (Reset), which indicates that a connection was forcefully closed or rejected.

Technical Corrections:

* Port 143 is IMAP, not HTTPS. HTTPS uses port 443.
* TTL value 64 is commonly seen in Linux systems, but TTL alone does not fully confirm the OS.
* 116.202.120.165 is a public IP address, not a “Class A IP”. Class-based addressing is no longer commonly used.

Security Insight:
Abnormal SYN patterns may indicate port scanning or SYN flood attacks.

---

## 2. HTTP Request

Filter used:

```
ip.src==192.168.X.X && ip.dst==34.107.221.82 && http
```

Observation:

Captured an HTTP GET request sent from the client to the server IP 34.107.221.82.

Explanation:

HTTP is used to request web content from a server.
The client sends a GET request, and the server responds with the requested data.

If HTTPS is used, the HTTP payload will not be visible because it is encrypted inside TLS.

Security Insight:

Sensitive data transmitted over HTTP (not HTTPS) can be intercepted.
Modern websites, including torbrowser.org, use HTTPS for secure communication.

---

## 3. DNS

Filter used:

```
dns
```

Observation:

A DNS query was sent from my machine to a DNS server to resolve the domain name into an IP address.

Explanation:

Before establishing a TCP connection, the system resolves the domain name using DNS.
DNS typically uses UDP port 53 for faster communication.
In some cases (large responses or zone transfers), DNS uses TCP port 53.

Security Insight:

DNS traffic can reveal browsing behavior and is commonly monitored during security investigations.

---

## 4. ARP

Filter used:

```
arp
```

Observation:

Before communicating with the external server, the system sent an ARP request to discover the MAC address of the gateway.

Explanation:

ARP resolves an IP address to a MAC address within a local network.
The ARP request is sent as a broadcast to:

ff:ff:ff:ff:ff:ff

The device that owns the requested IP responds with its MAC address.
After this, communication continues through the gateway.

Security Insight:

ARP spoofing attacks exploit this process by sending fake ARP responses to intercept traffic.

---

## Why This Analysis Is Important

Understanding packet-level communication helps in:

* Detecting scanning behavior
* Identifying abnormal traffic patterns
* Investigating connection attempts
* Understanding how web communication is established

---
