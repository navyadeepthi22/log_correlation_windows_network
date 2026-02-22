# Log Correlation: Windows Authentication and Network Activity

## Objective
To demonstrate how SOC analysts correlate endpoint authentication logs with network activity to assess whether observed behavior is normal or suspicious in an enterprise environment.

---

## Background
In enterprise environments, centralized logging allows SOC analysts to monitor endpoint and network telemetry through SIEM platforms. This enables correlation of multiple log sources without directly accessing individual systems, helping analysts investigate incidents efficiently and legally.

---

## Problem Statement
Security incidents rarely appear in a single log source. SOC analysts must correlate endpoint and network logs to understand user behavior, identify suspicious activity, and determine the legitimacy of security alerts.

This project demonstrates correlating Windows authentication logs with network activity to simulate a real-world SOC investigation scenario.

---

## Scenario Overview
A user logs into a Windows system and shortly afterward accesses an external website. The SOC must determine whether this behavior is legitimate or indicative of suspicious activity by correlating authentication and network events.

---

## Data Sources

### Windows Security Event Logs
Used to monitor user authentication and session activity on the endpoint.

### Network Activity (Simulated)
Browser history was used as a simulated network log source to represent outbound web access from the endpoint. This simulates proxy or secure web gateway logs commonly used in enterprise SOC environments.

---

## Observed Events

### Authentication Event
- **Log Source:** Windows Security Event Log  
- **Event ID:** 4634  
- **Description:** User logoff event indicating the termination of a user session  

### Network Access Event
- **Log Source:** Browser History (Simulated Network Log)  
- **Accessed URL:** https://github.com  
- **Description:** Outbound web access to an external destination  

---

## Correlated Observation
The authentication and network access events occurred within a close time window. This correlation suggests that the external web access was initiated during an active user session rather than by an automated process or background service.

---

## Timeline Correlation
- At **12:11:57**, a Windows logoff event (Event ID 4634) was recorded for the user account, indicating the end of an authenticated session.
- Around **12:57**, outbound network activity was observed when the same system accessed the external website **github.com**.

The close proximity of these timestamps indicates that the network activity occurred during or immediately surrounding a legitimate user session.

---

## Analysis
The correlated events show that the user accessed an external website shortly before or after an authenticated Windows session. The destination domain, **github.com**, is a trusted and commonly used platform for developers to access source code and documentation.

The activity originated from the same endpoint and occurred within a valid user session timeframe. No abnormal behavior such as repeated access attempts, access to unknown domains, or suspicious downloads was observed.

Based on the available evidence, the activity is consistent with normal user behavior rather than malicious intent.

---

## MITRE ATT&CK Mapping
- **Tactic:** Discovery  
- **Technique:** Application Layer Protocol (T1071)  

### Explanation
The observed activity involved outbound web access over standard application-layer protocols (HTTPS). While such techniques can be abused by attackers for communication or reconnaissance, no malicious indicators were identified in this scenario.

---

## Decision
**False Positive**

The correlated authentication and network activity aligns with normal user behavior and does not indicate malicious intent.

---

## Recommended Actions
1. Close the alert as a false positive after validation through log correlation.
2. Continue monitoring outbound web activity for access to unknown or suspicious domains.
3. Implement proxy or firewall logging in enterprise environments to enhance network visibility.
4. Educate users on safe browsing and secure downloading practices.

---

## Conclusion
This project demonstrates practical SOC log correlation techniques by combining Windows authentication logs and network activity to accurately assess security alerts and reduce false positives.