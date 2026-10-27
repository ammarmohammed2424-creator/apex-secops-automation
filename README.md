# apex-secops-automation
Automated Cloud Threat Detection &amp; Incident Response Pipeline using Python, Linux system tools, and custom SIEM guardrails.

# Apex-SecOps: Automated Threat Detection & Cloud Remediation Pipeline

An automated Security Orchestration, Automation, and Response (SOAR) prototype designed to bridge the gap between offensive reconnaissance and defensive cloud isolation.

---

## 🏗️ Project Architecture & Workflow
This project simulates a complete security incident lifecycle:
1. **Offensive Reconnaissance (`apex_attacker.py`):** Targets cloud infrastructure to probe open ports and simulate an active threat[cite: 13, 18].
2. **SIEM Alert Ingestion:** Captures high-severity threat intelligence.
3. **Automated Remediation (`remediate_cloud.py`):** Programmatically processes incident payloads and executes host-level network containment via `iptables`[cite: 19].

---

## 🚀 Step-by-Step Execution Workflow

### Step 1: Initialize Offensive Reconnaissance
We start by executing our custom Python attacker module against the target cloud asset to verify connectivity and scan for exposed services[cite: 13, 18]:

<img width="679" height="98" alt="working of apex attacker" src="https://github.com/user-attachments/assets/246dbd48-4e70-4bd3-8668-29d649083b94" />


### Step 2: Nmap Scan Telemetry
The reconnaissance script runs an Nmap port scan against the target AWS EC2 instance, identifying active open ports (such as SSH on Port 22)[cite: 13]:

<img width="913" height="609" alt="Screenshot 2026-10-23 152710" src="https://github.com/user-attachments/assets/b8387743-52f2-4146-ab95-90cf8c66189b" />

### Step 3: Automated Incident Response & Guardrail Enforcement
Once the threat is flagged, the defense script (`remediate_cloud.py`) ingests the payload, triggers a high-severity alert, and automatically applies host firewall isolation (`iptables -j DROP`) to block the attacker IP[cite: 19]:

<img width="647" height="312" alt="working or remediate cloud py" src="https://github.com/user-attachments/assets/ac993be5-5c3e-486b-9166-e3aa52d6168e" />


---

## 📁 Repository Structure

```text
apex-secops-automation/
├── scripts/
│   ├── apex_attacker.py      # Offensive reconnaissance script
│   └── remediate_cloud.py    # Automated defense & iptables guardrail
├── docs/
│   ├── working_of_apex_attacker.png
│   ├── nmap_scan_results.png
│   └── working_or_remediate_cloud.png
└── README.md                 # Project documentation
