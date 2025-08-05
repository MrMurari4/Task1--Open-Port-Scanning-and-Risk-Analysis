# 🔍 Task 1 – Open Port Scanning and Risk Analysis

[![Internship](https://img.shields.io/badge/Internship-Cybersecurity-blue)]()
[![Tools](https://img.shields.io/badge/Tools-Nmap%20%7C%20Wireshark-green)]()
[![Status](https://img.shields.io/badge/Status-Completed-brightgreen)]()

---

## 📌 Overview

This repository contains my work for **Cybersecurity Internship Task 1**.

### 🎯 Objectives:
- Perform a local network scan using **Nmap** to discover devices and open ports
- Use **Wireshark** to capture packets during the scan
- Research services on open ports and identify associated risks
- Summarize and document findings

---

## 🧪 Tools Used

- 🔍 **Nmap** – for port scanning
- 📡 **Wireshark** – for packet capture
- 🐧 **Kali Linux VM** – scanning machine
- 🪟 **Windows Host** - Local Machine

---

## 📖 What I Did In This Task
So for this task, I connected my system to the internet using my mobile hotspot and used Kali Linux as a virtual machine inside my Windows laptop.
The first thing I did was check my IP address on both my Windows host and my Kali VM — just to make sure both were on the same network.
After that, I ran an Nmap scan from Kali, expecting to see just two devices on the network — my host machine (Windows) and my Kali VM.
But to my surprise, three IPs showed up in the scan.At first, I was confused. 
I even checked my mobile hotspot and it showed only one connected device, which was obviously my laptop. I started looking into that third IP and realized it was actually my DNS interface — turns out I had AdGuard DNS configured on my phone and completely forgot about it. That DNS service was showing up as a separate device, and port 53 (DNS) was open.Also, from Kali, my Windows system didn't show any open ports — which seemed odd. But then I realized it’s because I was scanning from outside (from the VM), and Windows Firewall was blocking the requests.
To confirm that, I ran the same Nmap scan directly from Windows, and this time I could actually see open ports like 135, 139, 445, etc. Since it was a local scan, the firewall didn’t block it.
I also used Wireshark to capture packets during the scan, applied some basic filters to see how the SYN/SYN-ACK responses looked, and then went on google and speedguide.net to research what each open port does and the risks they might pose.
In the end, this task helped me understand how network scanning, firewalls, and DNS behavior all play out in real environments.

---

## 🔍 Key Activities

- Scanned network: `192.168.156.0/24`
- Captured scan packets using Wireshark
- Analyzed responses: SYN-ACK (open), RST (closed), filtered ports
- Discovered internal DNS via AdGuard proxy on port 53
- Identified high-risk ports like **445 (SMB)** and **139 (NetBIOS)**

---

## 📚 Key Takeaways

- How to enumerate network devices and ports using Nmap
- Difference between TCP scan states (open, closed, filtered)
- Using Wireshark filters to view packet-level port scan behavior
- Risks of exposed services like SMB, NetBIOS, and RPC
- How DNS filtering (AdGuard) can appear in scans as an open DNS port

---

> ✅ *Internship Task 1: Port scanning, service discovery, and risk analysis on a local network*
