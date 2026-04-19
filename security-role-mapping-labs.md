# Security Role Mapping Labs

This file contains incident scenarios and mapping of security roles based on SOC/CISO decision-making.

---

## Scenario 1: Phishing Attack
- Incident: Employees report suspicious emails with login links
- Impact: Possible credential theft attempts

### Assigned Roles:
- SOC L1 → initial alert triage and validation
- SOC L2 → email header + link analysis
- Threat Intelligence → check known phishing campaigns / IOC matching

### Reasoning:
Fast triage + validation is required to prevent credential compromise and identify known phishing infrastructure.

---

## Scenario 2: Brute Force Attack
- Incident: Multiple failed login attempts detected from external IPs
- Impact: Possible credential stuffing attempt

### Assigned Roles:
- SOC L1 → detect authentication anomaly
- SOC L2 → investigate source IP and pattern frequency
- SOC Engineer → tune detection rules if needed

### Reasoning:
Login anomalies require log analysis and pattern recognition to confirm attack behavior.

---

## Scenario 3: Suspicious Internal Activity
- Incident: Unusual file access patterns from internal user account
- Impact: Possible insider threat or compromised account

### Assigned Roles:
- SOC L2 → deep log investigation
- CIRT → escalation if data exfiltration suspected
- Threat Intelligence → contextual analysis if external indicators exist

### Reasoning:
Internal anomalies require deeper investigation and possible incident escalation due to higher risk impact.

---

## Notes
- SOC L1 handles initial triage
- SOC L2 performs deeper investigation
- SOC Engineers maintain detection systems
- CIRT handles critical incidents and breaches
- Threat Intelligence provides external context and IOC correlation
