# 🎄 **Understanding NULL, FIN, and Xmas Scans with Nmap**  
**Discover stealthy and uncommon TCP port scan techniques that bypass firewalls and reveal hidden services.**

---

## 🧩 **Overview**  
NULL, FIN, and Xmas scans are unconventional TCP scan methods primarily designed for **stealth**. These scans exploit specific TCP behaviors defined by **RFC 9293 (RFC 793)** to identify open, closed, and filtered ports.  

| **Scan Type**  | **Flags Set**                          | **Purpose**                                     |
|----------------|----------------------------------------|-------------------------------------------------|
| 🔘 **NULL**    | No flags set                           | Sends a completely empty TCP packet.           |
| 🚪 **FIN**     | FIN flag                               | Mimics a graceful connection closure.          |
| 🎄 **Xmas**    | FIN, PSH, URG (blinking like Xmas 🎅) | Sends a malformed packet resembling a lit tree. |

---

## 🔍 **How They Work**

### **NULL Scans (`-sN`)**  
- Sends a **TCP packet with no flags** set.  
- **Expected behavior**:  
  - **Closed Ports**: Respond with `RST`.  
  - **Open Ports**: No response (or ICMP unreachable).  
  - **Filtered Ports**: No response or ICMP unreachable.  

---

### **FIN Scans (`-sF`)**  
- Sends a **TCP packet with only the FIN flag** set.  
- **Expected behavior**:  
  - **Closed Ports**: Respond with `RST`.  
  - **Open Ports**: No response.  
  - **Filtered Ports**: No response or ICMP unreachable.  

---

### **Xmas Scans (`-sX`)**  
- Sends a **TCP packet with FIN, PSH, and URG flags** set.  
- **Expected behavior**:  
  - **Closed Ports**: Respond with `RST`.  
  - **Open Ports**: No response.  
  - **Filtered Ports**: No response or ICMP unreachable.  

**Why the Name "Xmas"?**  
The flags make the packet look like a **blinking Christmas tree 🎄** in tools like Wireshark.  

---

## ⚠️ **Challenges with These Scans**
1. **Platform-Specific Behavior**:  
   - **Microsoft Windows** and some **Cisco devices** respond with `RST` to all malformed packets, showing all ports as `closed`.  

2. **IDS Awareness**:  
   - Modern **Intrusion Detection Systems (IDS)** can detect and block these scans.  

3. **Ambiguity**:  
   - Like **UDP scans**, open ports are marked as `open|filtered`, making definitive identification tricky.  

---

## 🎯 **Practical Example**

### **Command**  
```
sudo nmap -sN -sF -sX -p 1-1000 <target_ip>
```

### **Output**
```
Starting Nmap 7.93 ( https://nmap.org ) at 2024-11-29 16:00 UTC
Nmap scan report for <target_ip>
PORT      STATE           SERVICE
22/tcp    open|filtered   ssh
80/tcp    closed          http
443/tcp   open|filtered   https
```

---

## 🔓 Why Use These Scans?

1. Firewall Evasion:
Many firewalls drop packets with the SYN flag set. These scans avoid using SYN.

2. Stealth:
Applications monitoring for connections often ignore packets without a full handshake.

3. Quick Identification:
Useful for environments where stealth is crucial.

---

## 🧑‍💻 Advanced Tips

1. Combine with Other Scans:
Pair with TCP or SYN scans for thorough enumeration.
```
sudo nmap -sS -sX -p 1-1000 <target_ip>
```

2. Optimize Scan Speed:
Use `--top-ports` to focus on the most commonly used ports.
```
nmap -sN --top-ports 100 <target_ip>
```

3. Use `--packet-trace` for Debugging:
Analyze how packets are being sent and responded to.
```
nmap -sF --packet-trace <target_ip>
```

---

## 📘 Further Reading

[RFC 793 (TCP Protocol)](https://datatracker.ietf.org/doc/html/rfc793#section-1.1)
[Wireshark Packet Analysis](https://www.wireshark.org/docs/wsug_html_chunked/ChapterWork.html)

---

🔑 Master these scan techniques to uncover hidden services, bypass firewalls, and improve your network enumeration skills. Happy scanning! 🌟
