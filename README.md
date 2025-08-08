Certainly! Here's a **complete detailed cheat sheet** for all those networking tools, formatted as a **README.md** file for easy copy-pasting:

````markdown
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

Shows reply times and packet loss statistics.

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

Lists each hop’s IP and response times.

---

## 3. whois — Domain registration information

**Purpose:** Retrieves domain ownership and registration details.

### Usage:

```bash
whois google.com
```

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

Open ports with services and status.

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
dig google.com MX
```

---

### host usage:

```bash
host google.com
host -t MX google.com
```

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
ip route show
```

---

### ifconfig (older, deprecated tool):

```bash
ifconfig
ifconfig eth0 up
ifconfig eth0 192.168.1.10 netmask 255.255.255.0
```

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
curl -X POST -d "param=value" https://example.com/api
```

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
lsof -i :80
```

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

Feel free to copy, save, or modify this cheat sheet as needed!

```

Let me know if you want it as a file saved on disk or anything else!
```
