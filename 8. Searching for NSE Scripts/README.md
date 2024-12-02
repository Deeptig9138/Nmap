# 🛠️ Nmap NSE Scripts: Finding, Managing, and Installing 🚀
The **Nmap Scripting Engine (NSE)** is a powerful tool that extends Nmap's functionality, enabling tasks from vulnerability scanning to exploitation. Understanding how to find and manage these scripts is essential for efficient use. Here's a guide on finding, searching, and installing NSE scripts.

---

## 📂 Finding NSE Scripts

### 1️⃣ **Official Script List**
Nmap maintains a comprehensive list of scripts on its website. Visit it for:
- A complete directory of **official scripts**.
- Categories and descriptions for each script.  

🌐 [Nmap Official Scripts](https://nmap.org/nsedoc/)

### 2️⃣ **Local Storage**
On Linux, NSE scripts are stored at:  
```
/usr/share/nmap/scripts
```

---

## 🔎 Searching for Scripts

### 📜 Method 1: Using script.db
Nmap uses `/usr/share/nmap/scripts/script.db` to track available scripts. This formatted text file maps scripts to categories.

**Search Example**:
```
grep "ftp" /usr/share/nmap/scripts/script.db
```
This searches for all scripts related to FTP.

### 🧹 Method 2: Using ls
Use the ls command with wildcards (*) to find scripts.

**Search Example**:
```
ls -l /usr/share/nmap/scripts/*ftp*
```
Finds all scripts with "ftp" in their names.

### 🔍 Search for Categories:
For instance, finding all safe scripts:

```
grep "safe" /usr/share/nmap/scripts/script.db
```

---

## 🛠️ Installing New Scripts

### 🖥️ Using apt
Keep your scripts updated with:

```
sudo apt update && sudo apt install nmap
```

---

## 📥 Manual Installation
To install a script manually:

1. Download the Script:
```
sudo wget -O /usr/share/nmap/scripts/<script-name>.nse https://svn.nmap.org/nmap/scripts/<script-name>.nse
```

2. Update the script.db File:
```
nmap --script-updatedb
```

**🎨 Make Your Own Scripts**:
Want to write your custom NSE scripts? Basic Lua knowledge is enough!

---

## 📋 Quick Reference

| **Command**             |	**Description**                                |
|-------------------------|------------------------------------------------|
| grep "<term>" script.db	| Search for a term in the script.db file.       |
| ls -l /scripts/*<term>*	| Search for scripts containing a specific term. |
| wget <URL>	            | Download a new script.                         |
| nmap --script-updatedb	| Update the script database.                    |

---

## 🧩 Interactive Element: Test Your Knowledge
Q1: Where are NSE scripts stored by default on Linux?
Q2: What command updates the script database after adding a new script?

---

## 🚀 Next Steps
Start exploring NSE scripts locally and online, search for relevant ones, and even try creating your custom scripts! 🌐
