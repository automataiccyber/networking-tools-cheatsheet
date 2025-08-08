# Networking Tools Cheat Sheet

A detailed reference for common networking command-line tools used for diagnostics, troubleshooting, and information gathering.

---

## 1. ping — Test connectivity and measure latency

**Purpose:** Send ICMP echo requests to check if a host is reachable and measure round-trip time.

### Common options:
- `-c <count>` — Number of echo requests to send.
- `-i <interval>` — Interval between packets (seconds).
- `-s <size>` — Payload size in bytes.
- `-t <ttl>` — Set Time To Live.

### Example:
```bash
ping -c 4 google.com
````

### Output:

<img width="742" height="172" alt="image" src="https://github.com/user-attachments/assets/1578216e-b42b-4e1a-a761-953f6282d527" />

---

## 2. traceroute — Trace network path to a host

**Purpose:** Displays the route packets take to reach a destination host.

### Common options:

* `-m <max_ttl>` — Max hops to trace (default 30).
* `-n` — Show numeric IPs only (no hostname resolution).
* `-w <timeout>` — Timeout per probe in seconds.

### Example:

```bash
traceroute -n google.com
```

### Output:

<img width="677" height="215" alt="image" src="https://github.com/user-attachments/assets/c7a4831d-32ee-4181-a157-a63198f69572" />

---

## 3. whois — Domain registration information

**Purpose:** Retrieves domain ownership and registration details.

### Usage:

```bash
whois google.com
```

### Output:

<img width="733" height="388" alt="image" src="https://github.com/user-attachments/assets/a3cf1d19-52b2-4d2b-a41d-af23c10911f5" />

### Key fields:

* Registrar information
* Creation & expiration dates
* Registrant organization
* Name servers
* Domain status codes

---

## 4. nmap — Port scanning and host discovery

**Purpose:** Scan hosts for open ports and services.

### Common options:

* `-sS` — TCP SYN scan (stealth).
* `-sU` — UDP scan.
* `-p <port(s)>` — Specify port or range.
* `-O` — OS detection.
* `-A` — Aggressive scan (includes version & script scanning).

### Example:

```bash
sudo nmap -sS -p 80,443 google.com
```

### Output:

<img width="581" height="213" alt="image" src="https://github.com/user-attachments/assets/4bccc61c-6e10-4168-8f94-96eaa69dc9a6" />

---

## 5. netstat / ss — View active network connections

**Purpose:** Lists active TCP/UDP connections and listening ports.

### netstat common options:

* `-t` — TCP only.
* `-u` — UDP only.
* `-n` — Numeric output (no DNS).
* `-l` — Listening sockets.
* `-p` — Show owning processes.

### Example:

```bash
netstat -tunp
```

### Output:

<img width="787" height="103" alt="image" src="https://github.com/user-attachments/assets/704c5ee8-f7a7-417c-bca9-771ef12ed6f0" />

---

### ss common options:

* `-t` — TCP sockets.
* `-u` — UDP sockets.
* `-n` — Numeric output.
* `-p` — Show processes.

### Example:

```bash
ss -tunp
```

### Output:

<img width="1757" height="54" alt="image" src="https://github.com/user-attachments/assets/e8b42e7e-9548-4a67-9265-9ac2bcc88f30" />

---

## 6. dig / host — DNS lookups

**Purpose:** Query DNS servers for domain info.

### dig common options:

* `+short` — Show only answers.
* `ANY` — All records.
* `MX` — Mail servers.
* `NS` — Name servers.

### Examples:

```bash
dig +short google.com
```
### Output:

<img width="214" height="51" alt="image" src="https://github.com/user-attachments/assets/c8e9de40-3e99-4884-a70d-f0f972859068" />

---

### host usage:

```bash
host google.com
```

### Output:

<img width="432" height="77" alt="image" src="https://github.com/user-attachments/assets/6c2f1336-4a61-4d85-856b-d407db1aa90f" />

---

## 7. ip / ifconfig — View and configure IP addresses and interfaces

**Purpose:** Show or modify network interfaces and IP settings.

### ip commands:

* `ip a` or `ip addr` — Show interfaces and IPs.
* `ip link` — Show/manage network devices.
* `ip route` — Show routing table.

### Example:

```bash
ip a
```

### Output:

<img width="813" height="220" alt="image" src="https://github.com/user-attachments/assets/9cce2889-7a0d-47ca-993e-965bb213d0da" />

---

### ifconfig (older, deprecated tool):

```bash
ifconfig
```

### Output:

<img width="606" height="301" alt="image" src="https://github.com/user-attachments/assets/14798b31-4be8-470d-b169-be358d33b408" />

---

## 8. tcpdump — Packet capture and analysis

**Purpose:** Capture network packets for troubleshooting.

### Common options:

* `-i <interface>` — Specify network interface.
* `-nn` — Don’t resolve names.
* `-c <count>` — Capture limited packets.
* `-v`, `-vv`, `-vvv` — Verbosity levels.
* Filters — e.g., `port 80`, `host 1.2.3.4`.

### Example:

```bash
sudo tcpdump -i eth0 -nn -c 5 port 80
```
### Output:

<img width="1593" height="198" alt="image" src="https://github.com/user-attachments/assets/37b7ccb4-a5bf-4006-a297-19981f019482" />

---

## 9. curl — HTTP requests and inspection

**Purpose:** Transfer data or inspect HTTP headers and responses.

### Common options:

* `-I` — Fetch HTTP headers only.
* `-X` — Specify HTTP method (GET, POST, etc.).
* `-d` — Data to send (for POST).
* `-H` — Add custom headers.

### Examples:

```bash
curl -I https://google.com
```

### Output:

<img width="1898" height="234" alt="image" src="https://github.com/user-attachments/assets/2b9f00e1-7f65-40ed-b592-ea5a9b63491a" />

---

## 10. lsof — List open network files and connections

**Purpose:** List open files including network sockets and associated processes.

### Common options:

* `-i` — Show internet/network connections.
* `-i :<port>` — Show connections on specific port.
* `-n` — No DNS lookups.
* `-P` — Show port numbers numerically.

### Examples:

```bash
lsof -i -n -P
```

### Output:

<img width="878" height="346" alt="image" src="https://github.com/user-attachments/assets/4b4faccc-57aa-4484-865d-5300f570ec0a" />

---

# Summary Table

| Tool        | Purpose                             | Example Command              |
| ----------- | ----------------------------------- | ---------------------------- |
| ping        | Connectivity & latency test         | `ping -c 4 google.com`       |
| traceroute  | Trace network path                  | `traceroute google.com`      |
| whois       | Domain registration info            | `whois google.com`           |
| nmap        | Port scan & host discovery          | `sudo nmap -sS google.com`   |
| netstat/ss  | View active connections             | `netstat -tunp` / `ss -tunp` |
| dig/host    | DNS lookup                          | `dig +short google.com`      |
| ip/ifconfig | View/configure interfaces           | `ip a` / `ifconfig`          |
| tcpdump     | Packet capture & analysis           | `sudo tcpdump -i eth0 -c 5`  |
| curl        | HTTP header and response inspection | `curl -I https://google.com` |
| lsof        | List open network connections       | `lsof -i -n -P`              |

---

Created By: Liel Darren F. Fajutagana

