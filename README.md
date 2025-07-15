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



