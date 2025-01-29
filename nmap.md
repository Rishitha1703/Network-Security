<h1>NMAP</h1>
---

### **Basic and Default Scans**
1. `nmap 192.168.1.7`  
   - Performs a basic scan, checking for **live hosts** and open **TCP ports** using a **SYN scan (if run as root) or a Connect scan (if not root)**.
   
2. `nmap amazom.com` *(Note: Likely a typo for `amazon.com`)*  
   - Tries to scan **Amazon’s public domain** but likely fails or gets blocked due to security policies.

---

### **SYN and TCP Scans**
3. `nmap -sS 192.168.1.7`  
   - **SYN Scan (Stealth Scan)**  
   - Sends **SYN packets** to detect open ports but does not complete the **three-way handshake**, making it stealthier.
   - Requires **root privileges**.

4. `sudo nmap -sS 192.168.1.7`  
   - Same as above, but now executed with **root privileges** for full functionality.

5. `sudo nmap -sT 192.168.1.7`  
   - **TCP Connect Scan**  
   - Completes the full **three-way handshake**, making it **easier to detect by firewalls and logs**.
   - Used when **root privileges are not available**.

---

### **UDP and Firewall Analysis Scans**
6. `sudo nmap -sU 192.168.1.7`  
   - **UDP Scan**  
   - Scans **UDP ports** (e.g., DNS, SNMP, TFTP).  
   - Slower and less reliable than TCP scans because UDP lacks **handshakes**.

7. `sudo nmap -sA 192.168.1.7`  
   - **ACK Scan**  
   - Determines **firewall rules** by checking how the target handles **ACK packets**.
   - Used to detect if ports are **filtered** rather than open/closed.

---

### **Host Discovery and Listing**
8. `sudo nmap -sL 192.168.1.7`  
   - **List Scan**  
   - Does **not** send probes, only **lists IP addresses and DNS names**.

9. `sudo nmap -sn 192.168.1.7`  
   - **Ping Scan**  
   - Checks if the host is **alive** without scanning ports.

10. `sudo nmap -pn 192.168.1.7`  
   - **Disables Ping Check**  
   - Forces Nmap to **scan even if the host does not respond to ping**.

---

### **Port Scanning**
11. `sudo nmap -p 80 192.168.1.7`  
   - Scans only **port 80** (HTTP service).

12. `sudo nmap -p 80-90 192.168.1.7`  
   - Scans **ports 80 to 90**.

13. `sudo nmap -p google.com` *(Incorrect Syntax)*  
   - Should be: `sudo nmap -p 80 google.com`  
   - This scans **port 80** on **Google's server**.

---

### **Service and Version Detection**
14. `sudo nmap -sV 192.168.1.7`  
   - **Service Version Detection**  
   - Attempts to determine **software versions** running on open ports.

---

### **Summary**
- **Basic Scans**: `nmap <target>` (default scan)  
- **Stealth Scans**: `-sS` (SYN scan)  
- **Complete Scans**: `-sT` (TCP connect scan)  
- **UDP Scans**: `-sU`  
- **Firewall Detection**: `-sA`  
- **Host Discovery**: `-sn` (ping scan), `-sL` (list scan)  
- **Port Selection**: `-p <port>`  
- **Service Detection**: `-sV`  

These commands show **various reconnaissance techniques** that help in **penetration testing, network auditing, and security assessments**.
