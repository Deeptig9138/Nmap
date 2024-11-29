# 🌐 **Understanding TCP Connect Scans (`-sT`) with Nmap**  
**Explore the fundamentals of TCP Connect scans and how they interact with the TCP three-way handshake.** 🚀

---

## 🔑 **What is a TCP Connect Scan?**
A **TCP Connect Scan** works by performing the **TCP three-way handshake** on each target port. This method determines the port's state (open, closed, or filtered) based on the server's response.

---

## 📖 **The TCP Three-Way Handshake**
1. **SYN (Synchronize)**:  
   Our machine sends a **TCP SYN packet** to the target port.

2. **SYN-ACK (Synchronize-Acknowledge)**:  
   If the port is open, the target responds with a **SYN-ACK packet**.

3. **ACK (Acknowledge)**:  
   Our machine acknowledges the target's response, completing the handshake.

---

## 💡 **How Does Nmap Use the Handshake?**
- **Open Port**:  
  The target responds with a **SYN-ACK packet** → Nmap marks the port as open.  
- **Closed Port**:  
  The target responds with a **RST (Reset)** packet → Nmap marks the port as closed.  
- **Filtered Port**:  
  No response or a firewall drops the packet → Nmap marks the port as filtered.

---

## 🖼️ **Visual Representation of TCP Connect Scan**

### 🔍 **Open Port & Closed Port**
![Open & Closed Port](https://www.techtarget.com/rms/onlineImages/networking-tcp_port_scanning_mobile.png)

### 🔒 **Filtered Port**
![Filtered Port](https://www.keysight.com/blogs/en/tech/nwvs/2020/06/17/media_178367e973c1c575418e451f2904824393631c258.png?width=750&format=png&optimize=medium)

---

## 🔥 **Dealing with Firewalls**

Firewalls can complicate TCP scans by altering the responses:  
- Some firewalls drop packets silently, making the port appear **filtered**.  
- Others send back **RST packets**, mimicking a closed port.  

### 🛠️ Example: Configure a Firewall to Send RST  
```
iptables -I INPUT -p tcp --dport <port> -j REJECT --reject-with tcp-reset
```

---

## 📝 Interactive Example

### 🎮 Try the TCP Connect Scan Command:

```
nmap -sT <target_ip>
```

**Output Example**:
```
Starting Nmap 7.93 ( https://nmap.org ) at 2024-11-29 12:00 UTC
Nmap scan report for <target_ip>
PORT     STATE    SERVICE
22/tcp   open     ssh
80/tcp   closed   http
443/tcp  filtered https
```

---

## 📘 Learn More

[TCP/IP Explained](https://www.fortinet.com/resources/cyberglossary/tcp-ip)

---

💡 Understanding TCP Connect Scans equips you with the knowledge to perform effective network enumeration and identify open ports, filtered connections, and firewall defenses. Keep exploring! 🔒🌐
