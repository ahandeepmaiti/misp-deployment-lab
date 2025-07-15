# 🛡️ MISP Deployment with PyMISP Integration on Ubuntu 18.04

> **Project Phase:** ✅ Phase 1: MISP Deployment | ⏳ Phase 2: WAJUH Integration  
> **Author:** Ahandeep Maiti 
> **Tags:** `MISP`, `Threat Intelligence`, `IOC`, `OSINT`, `Cybersecurity`, `PyMISP`

---

## 📌 Overview

This project covers a full deployment of **MISP (Malware Information Sharing Platform)** on **Ubuntu 18.04**, followed by basic automation using **PyMISP**—a Python library to push and pull Indicators of Compromise (IOCs). This serves as a foundational module for future integrations with alerting tools like Wazuh.

---

## 🏗️ Architecture Flow

![MISP Flow Diagram](./assets/misp-flowchart.svg)

---

## 🚀 Deployment Status Chart

### ✅ Phase 1: MISP Deployment
| Task                | Progress        |
|---------------------|-----------------|
| VM Setup            | ██████████ 100% |
| MISP Installation   | ██████████ 100% |
| Firewall Config     | ██████████ 100% |
| Org/User Setup      | ██████████ 100% |
| Threat Feeds        | ██████████ 100% |
| PyMISP Setup        | ██████████ 100% |
| IOC Automation      | ██████████ 100% |

### ⏳ Phase 2: WAJUH Integration
| Task                  | Progress        |
|-----------------------|-----------------|
| Feed Format           | █████░░░░░░ 50% |
| Parser Script         | ██░░░░░░░░ 20%  |
| MISP Sync             | ░░░░░░░░░░ 0%   |
| Correlation           | ░░░░░░░░░░ 0%   |
| Alert Automation      | ░░░░░░░░░░ 0%   |

---

## 🔍 Understanding MISP Architecture

### 📘 MISP Event  
Structured container holding contextually linked IOCs (e.g., IPs, hashes, URIs).

### 🧩 MISP Object  
Collection of attributes bundled into real-world use-case templates (e.g., malware file or phishing domain).

### 🧬 MISP Attribute  
Atomic pieces of threat intel like `ip-src`, `md5`, `url`, categorized and IDS-export ready.

### 🌐 MISP Feed  
Pre-configured OSINT feeds like **Feodo Tracker**, **MalwareBazaar** for IOC enrichment and correlation.

---

## 🧠 Skills Gained
- Threat Intelligence Lifecycle
- Python-based Automation via PyMISP
- IOC Enrichment and Visualization
- VM Setup, Linux Hardening, and UFW Configuration
- Multi-org Role and API Access Configuration

---

## 📎 Resources & Credits
- [MISP Official Documentation](https://misp.github.io/MISP/)
- [PyMISP Library](https://github.com/MISP/PyMISP)
- Inspired by: [HoldMyBeerSecurity Blog](https://holdmybeersecurity.com/2020/01/28/install-setup-misp-on-ubuntu-18-04-with-an-intro-to-pymisp/)

---
# 🚀 Setting Up MISP on Ubuntu 18.04 & Quick Intro to PyMISP

> **Focus Areas:** MISP Installation | PyMISP Integration | IOC Automation  
> **Tags:** `MISP`, `Ubuntu 18.04`, `Threat Intelligence`, `PyMISP`, `Cybersecurity`, `IOC`


---

## 🔍 Why This Guide?

This tutorial walks you through installing the **Malware Information Sharing Platform (MISP)** on **Ubuntu 18.04**, followed by a short demo of integrating the **PyMISP** Python library. You'll gain a fully functional IOC-sharing platform ready for future integrations with detection tools, SIEMs, or alert frameworks.

---

## 🛠️ Step 1: Prepare the Ubuntu VM

- Launch Ubuntu 18.04 (64-bit) in VirtualBox or any virtualization tech.
- Ensure at least **2 GB RAM**, **25 GB disk space**, and internet connectivity.
- Update your system:
  ```bash
  sudo apt-get update -y && sudo apt-get upgrade -y
  ```

---

## 🧬 Step 2: Install MISP via Official Script

1. Fetch and run the installer:
   ```bash
   wget https://raw.githubusercontent.com/MISP/MISP/2.4/INSTALL/INSTALL.sh
   chmod +x INSTALL.sh
   sudo ./INSTALL.sh -A
   ```
2. During the install you'll be prompted to:
   - Set the base URL (FQDN) for your MISP instance
   - Create a dedicated `misp` system user
3. Open firewall ports:
   ```bash
   sudo ufw allow 80/tcp
   sudo ufw allow 443/tcp
   ```

---

## 🧹 Step 3: Configure MISP

- Log in at `https://<YOUR_FQDN>/users/login` with:
  - Username: `admin@admin.test`
  - Initial password: `admin`
- Change your admin password immediately.
- Create an organization and user roles via the Admin menu.

---

## 🌐 Step 4: Enable OSINT Threat Feeds

- Log in as SuperAdmin
- Navigate to **Sync Actions → List Feeds**
- Enable feeds like **Feodo IP Blocklist**, ensure caching is on

This enables fast threat intelligence correlation without full data import.

---

## 🐍 Step 5: Install and Use PyMISP

1. Install the required libraries:
   ```bash
   pip3 install -U pymisp
   ```
2. Load `ipython` or other Python shell.
3. Connect to your MISP using the API:
   ```python
   from pymisp import ExpandedPyMISP

   misp = ExpandedPyMISP(
     url='https://<YOUR_FQDN>',
     key='<YOUR_API_KEY>',
     ssl=False
   )
   ```
4. Create a new MISP event & add IOC attribute:
   ```python
   from pymisp import MISPEvent, MISPAttribute

   # New event
   event = MISPEvent()
   event.info = "Demo Event via PyMISP"
   saved = misp.add_event(event)

   # Add IOC attribute (e.g., “8.8.8.8” as ip-src)
   attr = MISPAttribute()
   attr.type = 'ip-src'
   attr.value = '8.8.8.8'
   attr.category = 'Network activity'
   misp.add_attribute(saved['Event']['id'], attr)

   # Query the IOC to verify
   misp.search(controller='attributes', type_attribute='ip-src', value='8.8.8.8')
   ```

---

## 🎯 What You’ll Learn

By following this guide, you'll:
- Deploy a fully functional **MISP threat intelligence platform**
- Automate IOC insertion and querying with **PyMISP**
- Enable real-time correlation from OSINT feeds
- Lay the foundation for further SOC integrations like Suricata or Wazuh

---





