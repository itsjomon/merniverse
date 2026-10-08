# Understanding the Internet

The **Internet** is a global network of interconnected networks. At its most fundamental level, a network starts whenever two or more devices connect to share data.

## 1. What Is a Network?

- **Point-to-Point:** Two computers linked directly via an Ethernet cable or wireless signal.
- **LAN (Local Area Network):** Multiple local devices (laptops, phones, printers) connected within a home, office, or building.
- **WAN (Wide Area Network):** A network connecting multiple LANs across large geographical distances, such as cities, countries, or continents.
- **The Internet:** The ultimate global WAN, connecting millions of private and public networks globally through shared infrastructure.

## 2. Physical Infrastructure

- **Modem:** Translates signals from external lines (fiber, coaxial, DSL) into digital binary data (`0`s and `1`s).
- **Router:** Directs traffic between local devices on your LAN and routes outbound traffic to the modem.
- **ISP (Internet Service Provider):** The telecommunications provider connecting your local setup to national and global network backbones.
- **IXPs and Global Backbone:** Physical exchange hubs and transoceanic subsea fiber-optic cables that carry high-speed data across regions and continents.

## 3. Addressing and Identification

- **MAC Address:** A permanent, physical hardware identifier assigned to a network card, used for local device delivery within a LAN.
- **IP Address:** A logical, routable network address assigned to a machine:
  - **IPv4:** 32-bit format (e.g., `192.168.1.1`).
  - **IPv6:** 128-bit hexadecimal format (e.g., `2001:db8::1`).
- **DNS (Domain Name System):** The internet's directory service; converts human-readable domain names (like `github.com`) into computer-readable IP addresses.

## 4. How Data Travels: Packets and Protocols

Data does not travel as single solid files. It uses **packet switching**:

1. **Chunking:** Data is broken into small, standardized chunks called **packets**.
2. **Addressing:** Each packet receives a header containing source IP, destination IP, and sequence numbers.
3. **Routing:** Routers independently forward packets along the fastest available paths.
4. **Reassembly:** The receiving device reorders the packets and verifies their integrity.

### Key Protocols

| Protocol | Type | Purpose |
| --- | --- | --- |
| **TCP** | Reliable | Guarantees ordered, complete delivery with error checks (browsing, APIs, files). |
| **UDP** | Fast | Sends packets without delivery confirmation (live streaming, gaming, VoIP). |
| **IP** | Routing | Routes packets across network boundaries. |
| **HTTP/HTTPS** | Application | Rules for transferring web content; HTTPS encrypts communication with TLS/SSL. |

## 5. Client-Server Model

- **Client:** The requester (browser, mobile app, or CLI tool).
- **Server:** A remote machine listening for incoming requests, executing business logic, querying databases, and returning responses.

## 6. Request/Response Lifecycle (Navigating to a URL)

```text
Browser                 DNS Server              Target Web Server
   |                        |                           |
   |--- 1. Query Domain --->|                           |
   |<-- 2. Return IP -------|                           |
   |                                                    |
   |--- 3. TCP Handshake (SYN -> SYN-ACK -> ACK) ------>|
   |--- 4. TLS Handshake (Secure Tunnel) -------------->|
   |--- 5. Send HTTP GET Request ---------------------->|
   |<-- 6. HTTP Response (Status 200 + HTML/Assets) ----|
   |                                                    |
[Render UI]
```

1. **DNS Lookup:** Browser resolves the domain name into an IP address.
2. **TCP and TLS Handshake:** Browser establishes a reliable, encrypted connection with the server.
3. **HTTP Request:** Browser transmits a request (e.g., `GET /index.html`).
4. **Server Processing:** Server processes logic, accesses databases if required, and returns a response payload with a status code (`200 OK`).
5. **Client Rendering:** Browser parses the HTML/CSS/JS files and renders the web page.
