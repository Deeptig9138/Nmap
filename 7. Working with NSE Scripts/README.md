# 🔍 **Nmap Scripting Engine (NSE)**  

🎉 **Unlock the Power of Nmap** with the **Nmap Scripting Engine (NSE)**!  
The NSE extends Nmap's functionality by enabling the use of **Lua-based scripts** for a wide range of tasks, from **vulnerability scanning** to **exploit automation**.  

---

## 🌟 **Key Features of NSE**  

NSE scripts are grouped into categories for specific use cases:  
   - 🛡️ **`safe`**: Scripts that won't affect the target.  
   - ⚠️ **`intrusive`**: Scripts that may impact the target.  
   - 🔒 **`auth`**: Scripts for bypassing authentication.  
   - 🧱 **`vuln`**: Scans for vulnerabilities.  
   - 💥 **`exploit`**: Attempts to exploit known vulnerabilities.  
   - 🕵️ **`discovery`**: Gathers additional information about services.  
   - 🔐 **`brute`**: Performs brute force attacks on credentials.

---

## 🛠️ **Using NSE Scripts**

### **1. Running Scripts by Category**  
Run all scripts in a specific category:  
```
nmap --script=<category>
```

**Example**:
```
nmap --script=safe <target>
nmap --script=vuln <target>
```

### **2. Running Specific Scripts**
Specify individual scripts to run:
```
nmap --script=<script-name>
```

**Example**:
```
nmap --script=http-fileupload-exploiter <target>
```

### **3. Running Multiple Scripts**
Run multiple scripts by separating them with commas:
```
nmap --script=script1,script2 <target>
```

**Example**:
```
nmap --script=smb-enum-users,smb-enum-shares <target>
```

---

## ⚙️ Using Script Arguments
Some scripts require arguments (e.g., credentials or URLs). Provide these with the --script-args option:

**Example: Uploading a File via HTTP PUT**
```
nmap -p 80 --script http-put --script-args http-put.url='/dav/shell.php',http-put.file='./shell.php'
```
📌 Arguments are connected to the script name using periods (e.g., http-put.url). Separate multiple arguments with commas.

---

## 📖 Built-In Script Help
Get information about any script locally with:
```
nmap --script-help <script-name>
```

Example:
```
nmap --script-help http-fileupload-exploiter
```

---

🌐 Script Library and Documentation
Explore the complete list of scripts, their arguments, and examples:
[Nmap Script Documentation](https://nmap.org/book/nse-usage.html)

---

## 🔥 Practical Examples
1. Safe Scanning
Discover safe scripts to gather non-intrusive information:
```
nmap --script=safe <target>
```

2. Scanning for Vulnerabilities
Perform a vulnerability scan:
```
nmap --script=vuln <target>
```

3. Brute-Forcing Services
Attempt to brute-force credentials for running services:
```
nmap --script=brute <target>
```

4. Advanced Exploitation
Automate exploitation of known vulnerabilities:
```
nmap --script=exploit <target>
```

5. Combined Usage
Perform discovery and enumeration of SMB services:
```
nmap --script=smb-enum-users,smb-enum-shares <target>
```

---

## 🎯 Why Use NSE?
- 🚀 Extended Functionality: From reconnaissance to exploitation.
- 🔎 Granular Control: Run specific scripts or full categories.
- ⚡ Customizable: Use arguments for tailored scanning.
- 💡 Built-In Help: Access script details anytime.

---

## ⚠️ Things to Remember
- Intrusive Scripts: Use with caution—they can alert or affect targets.
- Script Arguments: Ensure correct syntax to avoid errors.
- Firewall Limitations: Some scripts may be blocked by network defenses.

---

💻 Start leveraging the power of NSE today for efficient network reconnaissance and more!
