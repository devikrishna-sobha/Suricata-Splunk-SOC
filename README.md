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



## 📡 Splunk Integration

The Splunk Universal Forwarder was configured to collect Suricata logs and forward them to Splunk.

Suricata events were stored in the dedicated Splunk index:

```spl
index=Suricata


### 6. Detection Queries

```markdown
## 🔎 Detection Queries

### Suricata Alerts

```spl
index=Suricata event_type=alert


index=Suricata event_type=alert
| stats count by src_ip
| sort - count
| head 10

index=Suricata event_type=alert
| stats count by dest_ip
| sort - count
| head 10

index=Suricata event_type=alert
| timechart count


### 7. Dashboard

```markdown
## 📊 SOC Monitoring Dashboard

A custom **Suricata IDS Monitoring Dashboard** was created in Splunk.

The dashboard contains:

- Suricata Event Types
- Suricata Alerts Over Time
- Top Source IPs
- Top Destination IPs
- Recent Suricata Alerts


## 🚨 Alerting

A scheduled Splunk alert named **Suricata IDS Alert Detection** was configured to monitor Suricata detection events.

The alert uses:

```spl
index=Suricata event_type=alert


### 9. Results

```markdown
## 🧪 Results

The project successfully demonstrated:

- Suricata generating security events
- Suricata logs being forwarded to Splunk
- Suricata events being indexed in Splunk
- Security events being analyzed using SPL
- A SOC monitoring dashboard displaying Suricata activity
- Automated Splunk alerting for Suricata detections

## 📸 Screenshots

Project screenshots are available in the `Screenshots` folder.

Key screenshots include the Splunk Suricata index, monitoring dashboard, recent alerts, and alert configuration.

## 🚀 Future Improvements

- Add more Suricata detection rules
- Add threat-intelligence integration
- Create severity-based dashboards
- Add email/webhook notifications
- Implement automated incident response
