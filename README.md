# Suricata IDS Integration with Splunk for Network Threat Detection and SOC Monitoring

## 📌 Project Overview

This project demonstrates the integration of Suricata IDS with Splunk to build a network security monitoring and threat detection environment.

Suricata analyzes network traffic and generates security events and alerts. The Splunk Forwarder collects these logs and sends them to Splunk, where they are indexed, searched, visualized, and used to generate security alerts.

The project simulates a basic SOC monitoring workflow:

Suricata IDS → Splunk Forwarder → Splunk Index → Detection → Dashboard → Alert

---

## 🎯 Objectives

- Deploy and configure Suricata IDS
- Generate and collect network security events
- Forward Suricata logs to Splunk
- Create a dedicated Suricata index in Splunk
- Develop SPL queries for security monitoring
- Build a Suricata SOC monitoring dashboard
- Configure automated detection alerts
- Analyze source and destination IP activity
- Demonstrate a basic SIEM-based SOC workflow

---

## 🛠️ Technologies Used

- Suricata IDS
- Splunk Enterprise
- Splunk Universal Forwarder
- Kali Linux
- Windows
- SPL (Search Processing Language)

---

## 🏗️ Architecture

```text
                 Network Traffic
                       │
                       ▼
                ┌─────────────┐
                │  Suricata   │
                │     IDS     │
                └──────┬──────┘
                       │
                  eve.json logs
                       │
                       ▼
             ┌───────────────────┐
             │ Splunk Universal  │
             │    Forwarder     │
             └─────────┬─────────┘
                       │
                       ▼
                ┌─────────────┐
                │    Splunk   │
                │   Index     │
                │  Suricata   │
                └──────┬──────┘
                       │
             ┌─────────┴──────────┐
             ▼                    ▼
       SOC Dashboard          Detection Alert
