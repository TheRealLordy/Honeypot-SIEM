# Honeypot SIEM Project

This project demonstrates the setup and implementation of a honeypot using Azure Virtual Machines (VMs) and Microsoft Sentinel for monitoring and visualizing attacks.

---

## 🚀 Project Overview

This project focuses on:

- Setting up a VM to attract potential attackers.
- Collecting logs from failed login attempts (Event ID 4625).
- Visualizing attacker data using geolocation mapping in Microsoft Sentinel.

---

## 📜 Step-by-Step Implementation

### 1. **Creation of the VM**

#### Networking Configuration:
- A Virtual Machine (VM) was created in Azure and exposed to the internet.
- The **NIC Network Security Group** (NSG) was configured to **allow all traffic** from any source, ensuring accessibility for potential threats.

---

### 2. **Log Analytics Workspace Setup**

#### Purpose:
- A **Log Analytics Workspace** was created to ingest logs from the VM.

#### Integration:
- Enabled log collection from the VM via **Azure Security Center**.
- Linked the VM to the Log Analytics Workspace to ensure the logs were ingested.

---

### 3. **Microsoft Sentinel Setup**

#### Configuration:
- Microsoft Sentinel was connected to the Log Analytics Workspace.
- Sentinel was used to **visualize and analyze attack data**.

---

### 4. **VM Configuration for Honeypot Behavior**

#### Remote Desktop Protocol (RDP):
- Accessed the VM via **RDP** for setup.

#### Firewall Adjustment:
- Disabled the machine's firewall to make it respond to **ICMP (ping)** requests, making it easier for attackers to find and interact with the honeypot.

#### Event Logging:
- Configured the **Windows Event Viewer** to track **Event ID 4625** (failed logon attempts) to capture attacker information, such as IP addresses.

---

### 5. **Data Collection and Processing**

#### PowerShell Script:
- A **PowerShell script** was used to:
  - Scan the VM’s event logs.
  - Extract logs with **Event ID 4625**.
  - Save extracted data into a `.log` file.
> **Disclaimer**: The PowerShell script used in this project was sourced from [joshmadakor1). Credit goes to the original creator for their work.
#### Sample Log File:
- A sample log file matching the format of the generated logs was created to **train the Log Analytics Workspace** for consistent data extraction.

---

### 6. **Visualizing Attack Data in Sentinel**

#### Data Querying:
- A **KQL (Kusto Query Language)** query was developed to extract data from the log files.

#### Geolocation of Attackers:
- Used "IP Geolocalization" to determine the geographical origin of IPs attempting to log in.
- Visualized the geolocation data on a **map in Sentinel**.
--
- ##### Map Sample :
- ![MainMap](https://github.com/user-attachments/assets/fd3f34a1-907f-4802-a8dd-3c15afe42fd2)
