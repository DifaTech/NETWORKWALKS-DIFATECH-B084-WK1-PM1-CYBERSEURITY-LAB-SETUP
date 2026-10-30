# 🔐Cybersecurity & Penetration Testing Lab Environment Setup

Building a secure, isolated virtual lab for ethical hacking and threat analysis practice.

---

## 📌 Project Overview

This documentation outlines the step-by-step process I followed to build a private, controlled virtual cybersecurity and penetration-testing laboratory using Oracle VirtualBox and Kali Linux. 

The primary goal of this project is to establish a safe sandbox environment where security tools can be deployed, network traffic analyzed, and reconnaissance techniques tested without impacting external networks or live production systems.

---
## 🎯 Objectives

* Install and configure the VirtualBox hypervisor.
* Set up a dedicated private NAT Network for multi-machine isolation.
* Deploy and import Kali Linux as the primary security operating system.
* Configure static IPv4 addressing and DNS resolution for consistent mapping.
* Perform network verification tests (gateway pings, DNS lookups, and tool verification).
* Capture a clean baseline VirtualBox snapshot for reliable recovery.
* Document troubleshooting steps and technical takeaways.

---
## 🛡️ Purpose of the Lab

This lab environment acts as an isolated sandbox for hands-on cybersecurity learning, including:
* Network mapping and port scanning
* Vulnerability scanning and reconnaissance
* Packet capture and traffic analysis
* Security tool experimentation and threat intelligence labs

> **⚠️ Important:** This laboratory is strictly intended for educational purposes and authorized security testing on systems you own or have explicit legal permission to test.

---
## ⚙️ Lab Configuration Summary

| 🧩 Component | ⚙️ Specification / Setting |
| :--- | :--- |
| 🖥️ Host OS | Windows 11 | 
| 🧠 Host RAM | 8GB |
| ⚡ Processor | Intel Core i5 |
| 🧰 Hypervisor | Oracle VirtualBox 7.2 |
| 🐉 Security OS | Kali Linux 2026.3 |
| 🌐 Virtual Network Type | NAT Network |
| 📡 Network Range | 10.0.0.0/24 |
| 🐧 Kali Static IP | 10.0.0.2 |
| 🚪 Default Gateway | 10.0.0.1 |
| 🌍 DNS Configuration | 8.8.8.8 |

---
## 🪜 Lab Setup & Execution Steps

### Step 1. Hypervisor Setup

Installed Oracle VirtualBox to manage local virtual machines.

### Step 2. Create and Configure the Private NAT Network

A dedicated NAT Network was created within VirtualBox preferences to handle internal routing and external connectivity.

Configuration: 
```
* Network Name: `NatNetwork` 
* IPv4 Prefix: `10.0.0.0/24` 
* DHCP: Enabled 
* IPv6: Disabled
  ```

### Step 3. Kali Linux Network Adapter Configuration

The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.
The VM network adapter was configured as follows:
```
* **Adapter 1:** Enabled
* **Attached to:** NAT Network (NatNetwork)
* **Adapter Type:** Intel PRO/1000 MT Desktop
  ```

### Step 4. Detailed IP Configuration in Kali Linux

To maintain a consistent network footprint and make referencing the machine reliable for future security exercises, a consistent IPv4 address was configured.

Configuration Details:
```
* **IP Address:** `10.0.0.2`
* **Netmask / Subnet:** `255.255.255.0` (CIDR `/24`)
* **Default Gateway:** `10.0.0.1`
* **DNS Server:** `8.8.8.8`
```

The configuration was applied via the network connection manager (setting method to Manual) and refreshed using NetworkManager (`nmcli`) to ensure smooth routing without duplicate address detection conflicts.

### Step 5. Create a Clean VM Snapshot

Immediately after successful network configuration and connectivity checks, a baseline snapshot was captured.

* **Snapshot Name:** `Clean Kali - Network Setup`

**Purpose of the Snapshot:** 
This snapshot serves as a known-good recovery point. If a future penetration testing or misconfiguration exercise breaks the system, the virtual machine can be cleanly restored to this baseline within seconds.

---

## 🔎 Verification & Testing

* **IP Verification:** Executed `ip a` to confirm the correct static IP assignment.
* **Gateway Connectivity:** Tested communication using `ping 10.0.0.1`.
* **Internet Reachability:** Verified external connection via `ping 8.8.8.8`.
* **DNS Resolution:** Confirmed domain resolution using `nslookup`.
* **Tool Validation:** Checked security utility readiness (e.g., `nmap --version`).

---
## 🐞 Challenges Faced & Troubleshooting

* **Network Manager Timeout:** Resolved potential DHCP/static configuration delays on Kali by adjusting the NetworkManager DAD timeout parameter via terminal commands when necessary.
* **Virtualization Support:** Ensured hardware-assisted virtualization (Intel VT-x / AMD-V) was enabled in the system BIOS to allow the 64-bit virtual machines to boot correctly.

---
## 💡 Key Takeaways

* **Network Segmentation:** Gained practical understanding of how NAT Networks differ from standard NAT by permitting inter-VM communication.
* **IP Consistency:** Learned the value of static addressing for reliable documentation and multi-node attack simulations.
* **Snapshot Management:** Recognized how vital clean recovery states are before executing complex or risky security procedures.

---
## 🔗 Tools & Resources
* 7-Zip: https://7-zip.org/download.html
* VirtualBox: https://virtualbox.org/wiki/Downloads
* Kali Linux: https://kali.org/get-kali

---
## 👤 Author 
Favour Ogbah  
Cybersecurity Intern

LinkedIn: [https://www.linkedin.com/in/favour-ogbah-a4b1762b9](https://www.linkedin.com/in/favour-ogbah-a4b1762b9/)

---
## 📌 Project Context 
Program Name: Cybersecurity at Networkwalks | Week: 01 | Project: Cybersecurity & Pentesting Lab Setup | Repository: GitHub
