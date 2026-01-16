# Project Architecture

## Flow Overview
- Network traffic is monitored by Suricata IDS
- Alerts are written to JSON log files
- Wazuh Agent collects and forwards logs
- Wazuh Manager correlates events
- Alerts are visualized in Wazuh Dashboard

## Architecture Type
- Host-based + Network-based detection
- Centralized SIEM correlation
