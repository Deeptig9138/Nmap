# 🌐 **Network Mapping with Nmap Ping Sweeps**  

🚀 **Objective**: When connecting to a new network during a **black-box assignment**, the first step is to create a **"map" of the network structure**. This involves identifying which IPs are active hosts and which are not.

---

## 🧭 **What is a Ping Sweep?**  
A **ping sweep** sends ICMP packets to all potential IP addresses within a range. If an address responds, it’s marked as **alive**. Although not 100% accurate due to potential network restrictions, a ping sweep provides a useful **baseline** for mapping a network.

---

## 🛠️ **Performing a Ping Sweep**  

### **Basic Syntax**  
```bash
nmap -sn <target_ip_range>
```
`-sn`: Skip port scanning, relying on ICMP (or ARP on local networks) for host discovery.

Target Range: Can be specified using either a hyphen (-) or CIDR notation.

### Examples
1. Ping Sweep with a Range
```
nmap -sn 192.168.0.1-254
```
📌 Scans all IPs between 192.168.0.1 and 192.168.0.254.

2. Ping Sweep with CIDR Notation
```
nmap -sn 192.168.0.0/24
```
📌 Scans the entire 192.168.0.x network (subnet mask /24).

3. Specifying Multiple Ranges
```
nmap -sn 192.168.1.1-50,192.168.2.0/24
```
📌 Scans both a specific range and a subnet in a single command.

---

## 🔍 What Happens During a Ping Sweep?

The `-sn` flag triggers host discovery without port scanning:
- Sends ICMP Echo Requests to identify responsive IPs.
- Sends TCP SYN packet to port 443 (HTTPS).
- Sends TCP ACK (or SYN if not root) packet to port 80 (HTTP).
- Uses ARP requests instead of ICMP on local networks (requires sudo).

---

## 🎯 Command Output Example

**Command**:
```
sudo nmap -sn 192.168.0.0/24
```

**Output**:
```
Starting Nmap 7.93 ( https://nmap.org ) at 2024-11-29 16:30 UTC
Nmap scan report for 192.168.0.1
Host is up (0.0050s latency).
Nmap scan report for 192.168.0.5
Host is up (0.0023s latency).
Nmap scan report for 192.168.0.15
Host is up (0.0078s latency).
Nmap done: 256 IP addresses (3 hosts up) scanned in 2.05 seconds
```

---

📊 Visual Overview

![Result](https://www.oreilly.com/api/v2/epubs/9781789611809/files/assets/3266d5e1-d6ed-4c09-9512-3859e5c59b7a.png)

---

## 🔑 Key Insights
- Live Hosts: IPs that responded to ICMP, TCP SYN, or ACK probes.
- Silent Hosts: IPs that did not respond (could be inactive or firewalled).
- Faster Discovery: On local networks, ARP-based sweeps are faster than ICMP.

---

## ⚠️ Limitations of Ping Sweeps
1. Blocked ICMP Packets:
Many firewalls block ICMP echo requests, causing false negatives.

2. Silent Hosts:
Hosts may be active but configured to ignore ping and TCP probes.

3. Accuracy:
Results are a baseline and should be combined with other scanning techniques for full coverage.

---

## 🌟 Enhance Your Scans
1. Verbose Mode:
Show detailed scan progress and diagnostics.
```
nmap -sn -v 192.168.0.0/24
```

2. Output to File:
Save results in different formats (e.g., plain text, XML, or JSON).
```
nmap -sn -oN ping_sweep.txt 192.168.0.0/24
```

3. Custom Port Probes:
Specify different ports for TCP SYN/ACK tests.
```
nmap -sn --top-ports 20 192.168.0.0/24
```

4. Scan Across Subnets:
Map multiple networks with a single command.
```
nmap -sn 192.168.0.0/24,10.0.0.0/24
```

---

## 📘 Further Reading

[ICMP Protocol Overview](https://www.fortinet.com/resources/cyberglossary/internet-control-message-protocol-icmp#:~:text=The%20Internet%20Control%20Message%20Protocol,and%20at%20the%20right%20time.)

---

🔐 Use ping sweeps to lay the foundation for your network reconnaissance. Combine with port scans for detailed insights. 🕵️‍♂️
