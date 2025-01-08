# Wireshark & Nmap  
## Network Traffic Analysis & Vulnerability Scanning

![image](https://github.com/user-attachments/assets/348b9047-bc9d-465b-a37f-e06eebd8b53a)


---

## Introduction

In this project, we explore **Wireshark** and **Nmap** techniques taught by Chris Greer. We perform packet captures with Wireshark, run various Nmap scans against a target lab environment, and gather metrics (e.g., open ports, detected vulnerabilities, suspicious traffic flows) for 24 hours in a baseline “insecure” setting. We then apply best practices—such as system patching, firewall configuration, and network segmentation—to harden the environment and run our scans for another 24 hours. Finally, we compare the before-and-after results.

### Metrics We Will Show

1. **Open Ports Discovered** – Total number of TCP/UDP ports identified by Nmap.  
2. **Vulnerabilities Reported** – Identified vulnerabilities (e.g., from Nmap scripts or integrated vulnerability scanners).  
3. **Suspicious Flows** – Unusual network flows detected via Wireshark (e.g., scanning attempts, repeated connection resets).  
4. **Alert Triggers** – Alerts flagged by Wireshark or other intrusion detection tools (Suricata, Snort) integrated with our setup.  
5. **Security Incidents** – Issues requiring manual investigation or triage in a real-world setting.

---

## Lab Architecture Before Hardening

![image](https://github.com/user-attachments/assets/debb13a8-dcab-4009-b89c-f83082fcff83)


### Description of the Lab (Insecure State)

- **Local Network**:  
  - One **Windows** machine and one **Linux** machine.  
  - Minimal firewall rules or segmentation—both machines exposed to the local network.
- **Wireshark PC**: A separate machine used for packet capture, connected to a mirrored port (SPAN) or hub.  
- **Nmap Scans**: Run from another machine to identify open ports and potential vulnerabilities.  
- **Open Services**: Services like SMB, RDP, SSH, HTTP, and FTP are accessible without proper filtering or hardening.

In this “before” state, the lab is deliberately **insecure**—everything is on the same subnet, with no strict firewall rules or IPS/IDS configured.

---

## Lab Architecture After Hardening

![image](https://github.com/user-attachments/assets/6587348e-037d-48fe-bf4f-975d43c683a0)


### Hardening Changes

- **Firewalls & Segmentation**: Each machine now has host-based firewall rules, plus a network firewall restricting inbound/outbound ports.  
- **Patch Management**: Critical updates installed on both Windows and Linux systems.  
- **Network Segmentation**: Windows and Linux machines moved to separate VLANs, limiting lateral movement.  
- **IDS/IPS Integration**: Suricata installed on the Wireshark PC for real-time packet analysis.  
- **Reduced Attack Surface**: Only necessary ports (e.g., SSH for Linux, RDP for Windows) are allowed, and only from specific management IPs.

---

## Wireshark & Nmap Results Before Hardening

### Network Analysis Charts

#### 1. Open Ports Discovered (Nmap)
