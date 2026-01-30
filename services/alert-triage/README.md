# Alert Triage Service

**AI-Augmented SOC - LLM-Powered Security Alert Analysis**

> Intelligent alert triage using Foundation-Sec-8B (Cisco's security-optimized LLM) to reduce analyst workload and accelerate threat detection.

---

## Overview

The Alert Triage Service is the core AI component of the AI-Augmented SOC platform. It receives security alerts from Wazuh (via Shuffle webhooks) and uses LLMs to:

- **Classify severity** (Critical/High/Medium/Low/Informational)
- **Identify attack categories** (Malware, Intrusion, Exfiltration, etc.)
- **Determine true/false positives** (Reduce alert fatigue)
- **Extract IOCs** (IPs, domains, file hashes)
- **Map to MITRE ATT&CK** (Techniques and tactics)
- **Generate recommendations** (Prioritized response actions)

**Performance Targets:**
- **Accuracy:** F1 Score >0.90
- **Confidence Threshold:** >0.80 for auto-escalation
- **Latency:** <10 seconds per alert
- **Throughput:** 250 alerts/day

---

## Architecture

```
+-------------+        +-------------+        +--------------+
|   Wazuh     |------> |   Shuffle   |------> | Alert Triage |
|   Manager   | Alert  |    SOAR     | Webhook|   Service    |
+-------------+        +-------------+        +-------+------+
