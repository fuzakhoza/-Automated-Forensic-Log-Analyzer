# 🚨 Automated Forensic Log-Analyzer (SIEM Engine Logic Simulation)

## 📌 Project Overview
This project is an automated, text-parsing security tool engineered in Python. It simulates the core parsing and alerting logic used by modern Security Information and Event Management (SIEM) systems. The script processes multi-line authentication logs, extracts critical variables using regular expressions (Regex), counts authentication failures, and dynamically flags automated brute-force intrusion patterns.

This tool bridges the gap between raw file-system digital forensics and real-time incident detection automation.

---

## 🛠️ Core Features & Capabilities
* **Regex Data Extraction:** Targets and tokenizes multi-line unstructured server logs to pull clean attributes such as Timestamp, Source IP Address, Target Username, and Access Status.
* **Stateful Intrusion Logic:** Tracks the state of consecutive authentication attempts to isolate standard user typos from programmatic, high-velocity intrusion scripts.
* **Dynamic Threshold Alerting:** Generates immediate indicator-of-compromise (IoC) flags when authentication failures exceed a user-defined security threshold (e.g., more than 5 failed attempts from a single IP address).
* **Forensic Analytics Output:** Compiles parsed log data into a structured summary report detailing the total volume of events, top target usernames, and a prioritized list of high-risk IP addresses for firewall blacklisting.

---

## 💻 Technical Toolkit
* **Language:** Python 3
* **Libraries Used:** `re` (Regular Expressions Engine), `os` (File System I/O Processing), `collections` (High-Performance Data Storage Optimization)
* **Environment:** Compatible with Linux Command Line Interface (CLI) and Windows Terminal environments.

---

## 🚀 How It Works (The Logic Breakdown)
1. **File Ingestion:** The script opens the target authentication log folder and reads log structures step-by-step.
2. **Regex Parsing:** It checks each entry against a customized regular expression pattern:
   `(?P<timestamp>\d{4}-\d{2}-\d{2}\s\d{2}:\d{2}:\d{2}).*?Failed password for (?P<user>\S+) from (?P<ip>\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})`
3. **Tracking & Aggregation:** If a "Failed Password" string matches the query parameters, the internal counter tracks the event against that specific source IP.
4. **Trigger Threshold:** If an IP breaks the threshold rule, an immediate alert string is logged:
   `[CRITICAL ALERT] Potential Brute Force Intrusion Block Triggered from IP: 192.168.X.X targeting User: admin`

---

## 📊 Sample Output Representation
```text
[+] Analysis Complete. System Overview:
--------------------------------------------
Total Log Lines Scanned: 12,450
Total Authentication Failures Detected: 342
--------------------------------------------
[🚨 FIREWALL ACTION REQUIRED - THRESHOLD EXCEEDED]:
* IP: 192.168.43.77  | Failed Attempts: 45 | Target: root
* IP: 10.0.0.12      | Failed Attempts: 12 | Target: admin
```

---

## 🔬 Use-Case Alignment (Digital Forensics & Corporate Security)
Within environments handling high-stakes corporate compliance networks (such as the Road Accident Fund account), monitoring authentication logs manually is impossible due to sheer data volume. This automated utility provides the foundational automated scanning scripts required to identify initial access vectors, trace rogue credentials, and accelerate the response phase of Incident Response (IR) life cycles.
