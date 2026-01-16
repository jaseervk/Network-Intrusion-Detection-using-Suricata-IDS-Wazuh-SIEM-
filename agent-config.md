
---

## 📄 `agent-config.md`

```md
# Wazuh Agent – Suricata Log Monitoring Configuration

## Overview

This configuration enables a **Wazuh Agent** to:
- Monitor **Suricata logs locally**
- Forward structured events to the Wazuh Manager
- Support **real-time Nmap scan detection**

---

## 1. Enable Suricata Log Collection

Edit the agent configuration file:

```bash
nano /var/ossec/etc/ossec.conf

<!-- ADD SURICATA LOG MONITORING -->
<localfile>
  <log_format>json</log_format>
  <location>/var/log/suricata/eve.json</location>
</localfile>

<localfile>
  <log_format>json</log_format>
  <location>/var/log/suricata/fast.log</location>
</localfile>
