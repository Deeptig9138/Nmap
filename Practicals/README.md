# 🚀 Nmap Quickstart Guide 🕵️‍♂️
Welcome to your interactive Nmap guide! Whether you're a pentester or just getting started with network scanning, this document will help you master the essentials of **Nmap**, one of the most powerful tools in your toolkit. 🛠️

---

## 🌟 About Nmap
Nmap (Network Mapper) is a versatile tool used to discover hosts and services on a network. It supports multiple platforms and comes pre-installed on **Kali Linux** and the **TryHackMe Attack Box**.  

Access Nmap with:  
```
nmap <options> <target>
```

To get help:
- Help Menu: nmap -h
- Man Page: man nmap

---

## 🛠️ Essential Commands

### 🔍 Basic Scans
| **Command** |	**Description**                                |
|-------------|------------------------------------------------|
| `-sS`	      | Perform a Syn Scan (stealth scan).             |
| `-sU`	      | Perform a UDP scan.                            |
| `-O`	      | Detect the target's operating system.          |
| `-sV`	      | Detect service versions running on open ports. |

### 📊 Output Options
| **Command**  |	**Description**                                     |
|--------------|------------------------------------------------------|
| `-oA <name>` |	Save output in all formats (normal, XML, grepable). |
| `-oN <file>` |	Save output in normal format.                       |
| `-oG <file>` |	Save output in grepable format.                     |

### 🗣️ Verbosity and Timing
| **Command** |	**Description**                                   |
|-------------|---------------------------------------------------|
| `-v`	      | Increase verbosity.                               |
| `-vv`	      | Set verbosity to level 2.                         |
| `-T5`       |	Set the timing template to the fastest level (5). |

### 🎯 Port Scanning
| **Command**     |	**Description**       |
|-----------------|-----------------------|
| `-p 80`	        | Scan only port 80.    |
| `-p 1000-1500`	| Scan ports 1000-1500. |
| `-p-`	          | Scan all ports.       |

### 🤖 Scripts and Aggressive Mode
| **Command**       |	**Description**                                       |
|-------------------|-------------------------------------------------------|
| `--script=<name>`	| Run a specific script from the NSE library.           |
| `--script=vuln`	  | Run all scripts in the "vuln" category.               |
| `-A`	            | Enable aggressive mode (OS detection, scripts, etc.). |

---

## 🧩 Interactive Questions

### 🎮 Quick Questions

1. What is the first switch listed in the help menu for a Syn Scan?
✅ Answer: -sS

2. Which switch enables a UDP scan?
✅ Answer: -sU

3. How would you save the Nmap results in all formats?
✅ Answer: -oA <filename>

### 🚦 Challenge Questions

1. Does the target respond to ICMP echo (ping) requests?
✅ Answer: N

2. Perform an Xmas scan on the first 999 ports of the target. How many ports are shown as open or filtered?
✅ Answer: 999

3. Why are all ports marked open/filtered in the Xmas scan?
✅ Answer: No Response

---

🚀 Get Scanning!

Unleash the power of Nmap and start exploring networks like a pro. Happy scanning! 🔎✨
