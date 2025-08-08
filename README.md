# Networking Tools Cheatsheet

This cheatsheet provides common networking commands and their typical outputs, along with explanations. It is useful for troubleshooting, network diagnostics, and information gathering.

---

1. Ping

`ping` sends ICMP echo requests to test connectivity and measure round-trip time (RTT) to a host.

Example command:
ping -c 4 google.com

Example output:
PING google.com (142.251.220.174) 56(84) bytes of data.
64 bytes from mnl07s02-in-f14.1e100.net (142.251.220.174): icmp_seq=1 ttl=118 time=7.19 ms
64 bytes from mnl07s02-in-f14.1e100.net (142.251.220.174): icmp_seq=2 ttl=118 time=10.3 ms
64 bytes from mnl07s02-in-f14.1e100.net (142.251.220.174): icmp_seq=3 ttl=118 time=10.4 ms
64 bytes from mnl07s02-in-f14.1e100.net (142.251.220.174): icmp_seq=4 ttl=118 time=10.9 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3022ms
rtt min/avg/max/mdev = 7.188/9.699/10.885/1.465 ms

---

2. Traceroute

`traceroute` shows the route packets take to reach a destination host, including each hop and latency.

Example command:
traceroute google.com

Example output:
traceroute to google.com (142.251.220.174), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  2.727 ms  4.541 ms  4.457 ms
 2  100.84.0.1 (100.84.0.1)  8.769 ms  8.680 ms  8.600 ms
 ...
 9  mnl07s02-in-f14.1e100.net (142.251.220.174)  8.841 ms  8.716 ms  8.600 ms

---

3. WHOIS

`whois` queries the domain registration and ownership details for a domain name.

Example command:
whois google.com

Excerpt from output:
Domain Name: GOOGLE.COM
Registrar: MarkMonitor Inc.
Creation Date: 1997-09-15
Registry Expiry Date: 2028-09-14
Registrant Organization: Google LLC
Name Servers:
    NS1.GOOGLE.COM
    NS2.GOOGLE.COM
    NS3.GOOGLE.COM
    NS4.GOOGLE.COM

---

4. Nmap (TCP SYN Scan)

`nmap` is a network scanner. The SYN scan (`-sS`) checks for open TCP ports stealthily.

Example command:
sudo nmap -sS google.com

Example output:
PORT    STATE SERVICE
80/tcp  open  http
443/tcp open  https

---

5. Netstat & ss

Shows active network connections.

Example commands:
netstat -tun
ss -tun

Example output:
udp 0 0 192.168.1.18:68 192.168.1.1:67 ESTABLISHED

---

6. DNS Lookup

`dig` and `host` resolve domain names to IP addresses.

Example commands:
dig +short google.com
host google.com

Example outputs:
142.251.220.174

google.com has address 142.251.220.174
google.com has IPv6 address 2404:6800:4017:802::200e
google.com mail is handled by 10 smtp.google.com.

---

7. IP Address Information

Check IP addresses and interfaces on your machine.

Example commands:
ip a
ifconfig

Example output snippet:
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500
    inet 192.168.1.18/24 brd 192.168.1.255 scope global dynamic
    inet6 fe80::a00:27ff:fe0f:86ad/64 scope link

---

8. Tcpdump (Packet Capture)

Capture live packets on an interface (limited to 5 packets).

Example command:
sudo tcpdump -nn -c 5

Sample output:
08:11:35.734530 IP 192.168.1.18.44671 > 192.168.1.1.53: 41741+ A? contile.services.mozilla.com. (46)
...
5 packets captured

---

9. Curl (HTTP Header Request)

Fetch HTTP headers from a URL.

Example command:
curl -I https://google.com

Sample output:
HTTP/2 301 
location: https://www.google.com/
content-type: text/html; charset=UTF-8
date: Fri, 08 Aug 2025 00:12:10 GMT

---

10. lsof (List Open Files and Network Connections)

List all open internet connections by processes.

Example command:
lsof -i

Output example:
firefox-e 11592 code01 83u IPv4 34965 0t0 TCP 192.168.1.18:33136->203.137.36.34.bc.googleusercontent.com:https (ESTABLISHED)

---

Summary:

| Tool       | Purpose                                      |
|------------|----------------------------------------------|
| ping       | Test connectivity and measure latency       |
| traceroute | Trace network path to a host                  |
| whois      | Domain registration info                      |
| nmap       | Port scanning and host discovery              |
| netstat/ss | View active network connections                |
| dig/host   | DNS lookups                                   |
| ip/ifconfig| View IP addresses and interfaces              |
| tcpdump    | Packet capture and analysis                    |
| curl       | HTTP header and response inspection            |
| lsof       | List open network files and connections       |

---

Created by Liel Darren F. Fajutagana
Date: 2025-08-08
