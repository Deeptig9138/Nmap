# 🔥 Bypassing Firewalls with Nmap 🚀
Welcome to the **Firewall Evasion Toolkit**! In this guide, we'll explore techniques to bypass firewalls using **Nmap**, with a focus on **ICMP blocking** and **evasion switches**. Let’s get started! 🎯

---

## 🛡️ The ICMP Blocking Problem
Windows hosts often block **ICMP packets** by default. This causes two major issues:

1. **Manual Detection Fails**: You can't use `ping` to check if a host is alive.
2. **Nmap Scans Fail**: By default, Nmap assumes the host is dead if it can't ping it.

### ⚡ The Solution: `-Pn`
The **`-Pn` switch** in Nmap forces it to skip the ping check, treating the host as alive.  

**Example Command**:  
```
nmap -Pn <target>
```
**💡 Pro Tip: While -Pn bypasses ICMP blocking, it might significantly increase scan time if the target is genuinely offline.**

---

## 🌐 Local Network Scans
If you're on the local network, Nmap can use **ARP** requests to detect host activity without relying on ICMP.

**Command Example**:
```
nmap -PR <target>
```

---

## 🚨 Firewall Evasion Techniques
Nmap offers several switches to bypass firewalls and Intrusion Detection Systems (IDS). Here are some notable options:

### 🧩 Fragmentation: -f
Breaks packets into smaller fragments to evade detection.

**Example Command**:
```
nmap -f <target>
```

### 🔢 Custom Packet Size: --mtu
Control packet size (must be a multiple of 8).

**Example Command**:
```
nmap --mtu 16 <target>
```

### ⏱️ Scan Delay: --scan-delay
Adds a delay between packets to avoid time-based IDS triggers.

**Example Command**:
```
nmap --scan-delay 200ms <target>
```

### 🛠️ Checksum Tampering: --badsum
Generates packets with invalid checksums to identify firewalls.

**Example Command**:
```
nmap --badsum <target>
```

---

## 🌟 Quick Reference Table
| **Switch**     |	**Description**                                 |
|----------------|-------------------------------------------------|
| `-Pn`	         | Skip ICMP ping to treat hosts as alive.         |
| `-f`	          | Fragment packets to bypass detection.           |
| `--mtu <size>`	| Set packet size (multiple of 8).                |
| `--scan-delay`	| Add delay between packets.                      |
| `--badsum`	    | Generate invalid checksums to detect firewalls. |

---

## 🧩 Interactive Section: Test Your Knowledge

🔍 Question:
What Nmap switch would you use to bypass ICMP blocking?
 -f
 -Pn (correct answer)
 --badsum

---

## 🌟 Visual Aid: Packet Fragmentation

![Result](https://packetpushers.net/wp-content/uploads/2019/11/IPv4-Headers-Standard-Fragmentation-Highlighted-1024x431.png)

---

🚀 Let's Bypass Those Firewalls!
Get hands-on with these commands and start mastering firewall evasion. Whether you’re scanning a local network or testing a hardened host, Nmap has the tools you need.

🔥 Hack the Stack, Stay on Track! 🔥
