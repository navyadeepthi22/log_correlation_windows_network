# Log Correlation – Windows Authentication & Network Activity

## Overview
This project demonstrates how a SOC analyst correlates Windows authentication logs with network activity to determine whether observed behavior is legitimate or suspicious.

The investigation focuses on correlating endpoint log events with outbound network access to reduce false positives and improve alert accuracy.

---

## Project Objective
To practice SOC log correlation techniques by analyzing Windows Security Event logs alongside simulated network activity and making an informed incident response decision.

---

## Skills Demonstrated
- Log correlation across multiple data sources
- Windows Security Event Log analysis
- Understanding of authentication events
- Timeline-based investigation
- False positive validation
- MITRE ATT&CK mapping
- SOC decision-making and alert triage

---

## Data Sources Used
- Windows Security Event Logs
- Simulated Network Activity (Browser History)

---

## Key Windows Event IDs
- **4634** – User logoff
- **4624** – Successful logon (contextual reference)

---

## Investigation Summary
Authentication events were correlated with outbound web activity from the same endpoint. The accessed domain was identified as a trusted and commonly used platform.

Timeline correlation and domain reputation analysis confirmed the activity as normal user behavior rather than malicious activity.

---

## MITRE ATT&CK Reference
- **Tactic:** Discovery  
- **Technique:** Application Layer Protocol (T1071)

---

## Final Decision
**False Positive** – Alert closed after validation through log correlation.

