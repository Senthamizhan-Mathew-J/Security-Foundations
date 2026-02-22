#  Networking Basics

## Transport Layer Protocols

The Transport Layer is responsible for communication between devices.
It ensures data is delivered properly between applications.

Two main transport protocols:

- TCP (Transmission Control Protocol)
- UDP (User Datagram Protocol)

Data at this layer is sent in the form of **segments** (TCP) or **datagrams** (UDP).

---

##  TCP (Transmission Control Protocol)

TCP is a reliable, connection-oriented protocol.

### TCP Three-Way Handshake

Before data transmission, TCP establishes a connection:

1. SYN – Client sends request to server
2. SYN-ACK – Server acknowledges the request
3. ACK – Client confirms connection

After this, data transmission begins.

### Features of TCP

- Reliable communication
- Resends lost packets
- Ordered data delivery
- Error checking
- Connection-oriented

### Common Protocols Using TCP

- HTTP (Port 80)
- HTTPS (Port 443)
- SSH (Port 22)
- FTP (Port 21)
- SMTP (Port 25)
- IMAP (Port 143)

---

##  UDP (User Datagram Protocol)

UDP is a faster, connectionless protocol.

It does not guarantee delivery, ordering, or error correction.

### Features of UDP

- Faster than TCP
- No handshake required
- No retransmission of lost packets
- Used when speed is more important than reliability

### Common Protocols Using UDP

- DNS (Port 53 – mostly UDP)
- VoIP
- Online gaming
- Streaming services

---

## Key Differences Between TCP and UDP

| Feature        | TCP | UDP |
|---------------|------|------|
| Connection    | Yes  | No   |
| Reliability   | High | Low  |
| Speed         | Slower | Faster |
| Packet Order  | Maintained | Not Guaranteed |

---

## Why This Matters in Cybersecurity

Understanding TCP and UDP is important because:
- Many attacks target open ports
- Packet analysis requires knowing protocol behavior
- Firewalls and intrusion detection systems analyze transport layer traffic