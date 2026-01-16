# Wazuh Manager – Suricata Integration & Custom Rules

## Overview

This configuration enables the **Wazuh Manager** to:
- Ingest **Suricata EVE JSON logs**
- Detect **Nmap scans**
- Correlate Suricata alerts with **MITRE ATT&CK (T1046 – Network Service Scanning)**
- Raise high-severity alerts using **custom Wazuh rules**

---

## 1. Add Custom Detection Rules

Edit the local rules file on the **Wazuh Manager**:

```bash
nano /var/ossec/etc/rules/local_rules.xml
```

Add Following Rules:

```bash

<!-- Suricata: Nmap scan detection -->
<rule id="100200" level="12">
  <if_group>suricata</if_group>
  <field name="alert.signature">^ET SCAN.*Nmap</field>
  <description>Nmap scan detected by Suricata: $(alert.signature)</description>
  <group>attack,network_scan,mitre_t1046</group>
</rule>

<rule id="100600" level="10">
  <if_matched_sid>86601</if_matched_sid>
  <field name="path">src_ip:$(data.srcip)</field>
  <description>Nmap scan detected</description>
  <mitre>T1046</mitre>
  <options>no_full_log</options>
</rule>
