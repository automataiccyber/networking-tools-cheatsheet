# Networking Tools Cheat Sheet

A reference guide to essential networking tools with real command output and explanations for cybersecurity learners.

---

## 1. `ping` — Test Connectivity & Measure Latency

**✅ Purpose:**  
Sends ICMP echo requests to check if a host is reachable and measures round-trip time.

**🛠️ Basic Syntax:**
```bash
ping [options] <host>
````

**⚙️ Useful Options:**

* `-c <count>` – Number of echo requests to send
* `-i <interval>` – Interval between requests
* `-s <size>` – Packet payload size
* `-t <ttl>` – Set Time To Live

**🧪 Example:**

```bash
ping -c 4 google.com
```

**🖥️ Output:**

![ping output](https://github.com/user-attachments/assets/1578216e-b42b-4e1a-a761-953f6282d527)

---

## 2. `traceroute` — Trace Path to Host

**✅ Purpose:**
Shows the route packets take to reach a host.

**🛠️ Basic Syntax:**

```bash
traceroute [options] <host>
```

**⚙️ Useful Options:**

* `-n` – Do not resolve hostnames
* `-m <max_ttl>` – Max hops (TTL)
* `-w <timeout>` – Timeout per probe

**🧪 Example:**

```bash
traceroute -n google.com
```

**🖥️ Output:**

![traceroute output](https://github.com/user-attachments/assets/c7a4831d-32ee-4181-a157-a63198f69572)

---

## 3. `whois` — Domain Registration Info

**✅ Purpose:**
Retrieves ownership and registration details of domains.

**🛠️ Basic Syntax:**

```bash
whois <domain>
```

**⚙️ Useful Info Returned:**

* Registrar info
* Registration/Expiration dates
* Name servers
* Status (e.g., clientTransferProhibited)

**🧪 Example:**

```bash
whois google.com
```

**🖥️ Output:**

![whois output](https://github.com/user-attachments/assets/a3cf1d19-52b2-4d2b-a41d-af23c10911f5)

---

## 4. `nmap` — Port Scan & Host Discovery

**✅ Purpose:**
Scans hosts for open ports, OS details, and services.

**🛠️ Basic Syntax:**

```bash
nmap [options] <host>
```

**⚙️ Useful Options:**

* `-sS` – Stealth SYN scan
* `-p <ports>` – Specific ports
* `-O` – OS detection
* `-A` – Aggressive scan (OS, version, script)

**🧪 Example:**

```bash
sudo nmap -sS -p 80,443 google.com
```

**🖥️ Output:**

![nmap output](https://github.com/user-attachments/assets/4bccc61c-6e10-4168-8f94-96eaa69dc9a6)

---

## 5. `netstat` / `ss` — View Active Connections

**✅ Purpose:**
Displays active sockets, ports, and their statuses.

**🛠️ Basic Syntax:**

```bash
netstat [options]
ss [options]
```

**⚙️ Useful Options:**

* `-t` – TCP
* `-u` – UDP
* `-n` – Don't resolve names
* `-l` – Listening ports
* `-p` – Show PID/process

**🧪 Example:**

```bash
netstat -tunp
ss -tunp
```

**🖥️ Output (netstat):**

![netstat output](https://github.com/user-attachments/assets/704c5ee8-f7a7-417c-bca9-771ef12ed6f0)

**🖥️ Output (ss):**

![ss output](https://github.com/user-attachments/assets/e8b42e7e-9548-4a67-9265-9ac2bcc88f30)

---

## 6. `dig` / `host` — DNS Lookup

**✅ Purpose:**
Queries DNS servers to resolve domain information.

**🛠️ Basic Syntax:**

```bash
dig [options] <domain>
host <domain>
```

**⚙️ Useful Options (dig):**

* `+short` – Simplified output
* `<record>` – e.g., `A`, `MX`, `NS`, `ANY`

**🧪 Examples:**

```bash
dig +short google.com
host google.com
```

**🖥️ Output (dig):**

![dig output](https://github.com/user-attachments/assets/c8e9de40-3e99-4884-a70d-f0f972859068)

**🖥️ Output (host):**

![host output](https://github.com/user-attachments/assets/6c2f1336-4a61-4d85-856b-d407db1aa90f)

---

## 7. `ip` / `ifconfig` — View IP & Interfaces

**✅ Purpose:**
Displays network interfaces, addresses, and routes.

**🛠️ Basic Syntax:**

```bash
ip [object] [options]
ifconfig
```

**⚙️ Useful Commands (ip):**

* `ip a` – Show IPs/interfaces
* `ip link` – Show interfaces
* `ip route` – Routing table

**🧪 Examples:**

```bash
ip a
ifconfig
```

**🖥️ Output (ip):**

![ip output](https://github.com/user-attachments/assets/9cce2889-7a0d-47ca-993e-965bb213d0da)

**🖥️ Output (ifconfig):**

![ifconfig output](https://github.com/user-attachments/assets/14798b31-4be8-470d-b169-be358d33b408)

---

## 8. `tcpdump` — Packet Capture & Analysis

**✅ Purpose:**
Captures and analyzes packets on a specific network interface.

**🛠️ Basic Syntax:**

```bash
tcpdump [options] [filter]
```

**⚙️ Useful Options:**

* `-i <interface>` – Interface to listen on
* `-c <count>` – Stop after N packets
* `-nn` – Don’t resolve names
* Filters like `port 80`, `host 1.1.1.1`

**🧪 Example:**

```bash
sudo tcpdump -i eth0 -nn -c 5 port 80
```

**🖥️ Output:**

![tcpdump output](https://github.com/user-attachments/assets/37b7ccb4-a5bf-4006-a297-19981f019482)

---

## 9. `curl` — HTTP Requests & Inspection

**✅ Purpose:**
Performs and inspects HTTP(S) requests to web servers.

**🛠️ Basic Syntax:**

```bash
curl [options] <url>
```

**⚙️ Useful Options:**

* `-I` – Fetch headers only
* `-X` – HTTP method
* `-d` – POST data
* `-H` – Custom headers

**🧪 Example:**

```bash
curl -I https://google.com
```

**🖥️ Output:**

![curl output](https://github.com/user-attachments/assets/2b9f00e1-7f65-40ed-b592-ea5a9b63491a)

---

## 10. `lsof` — List Open Files & Network Connections

**✅ Purpose:**
Lists open files, including network sockets and ports used by processes.

**🛠️ Basic Syntax:**

```bash
lsof [options]
```

**⚙️ Useful Options:**

* `-i` – Show internet sockets
* `-n` – Don’t resolve hostnames
* `-P` – Show port numbers
* `-i :<port>` – Filter by port

**🧪 Example:**

```bash
lsof -i -n -P
```

**🖥️ Output:**

![lsof output](https://github.com/user-attachments/assets/4b4faccc-57aa-4484-865d-5300f570ec0a)

---

## 📊 Summary Table

| Tool         | Purpose                      | Example                      |
| ------------ | ---------------------------- | ---------------------------- |
| `ping`       | Connectivity check & latency | `ping -c 4 google.com`       |
| `traceroute` | Trace packet route           | `traceroute -n google.com`   |
| `whois`      | Domain registration info     | `whois google.com`           |
| `nmap`       | Port scan & discovery        | `sudo nmap -sS google.com`   |
| `netstat`    | List active connections      | `netstat -tunp`              |
| `ss`         | Modern socket stats          | `ss -tunp`                   |
| `dig`        | DNS record lookup            | `dig +short google.com`      |
| `host`       | Simple DNS lookup            | `host google.com`            |
| `ip`         | View IP settings             | `ip a`                       |
| `ifconfig`   | Legacy interface info        | `ifconfig`                   |
| `tcpdump`    | Packet capture               | `tcpdump -i eth0 -c 5`       |
| `curl`       | Web requests                 | `curl -I https://google.com` |
| `lsof`       | Open files & ports           | `lsof -i -n -P`              |

---

Created by: Liel Darren F. Fajutagana
