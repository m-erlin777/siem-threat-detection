# SIEM-Based Threat Detection Using Centralized Log Analysis

This project implements a lightweight SOC-style telemetry pipeline designed to simulate enterprise detection workflows.

## Architecture Overview

### Environment Components

• **Windows Endpoint**
  - Generates Windows Event Logs and Sysmon telemetry
  - NXLog forwards events via TCP syslog

• **Aggregation Node (Raspberry Pi)**
  - Receives endpoint logs
  - Forwards structured events to SIEM
  - 
• **SIEM Platform (Ubuntu VM)**
  - Elasticsearch for storage and search
  - Kibana for investigation and dashboards

• **Analyst Interface**
  - Kibana used to investigate authentication abuse, host reconnaissance, and command execution

### Log Flow Summary

![Diagram](https://i.ibb.co/m5HBZKsd/Log-Flow-Diagram.png)


## Detection Scenarios

### Authentication Abuse
- Multiple failed logons within short timeframes
- Identified via Windows Security logs
- Investigated using KQL filters against message field

### Registry-Based Persistence
- Unauthorized HKLM key creation
- Configuration changes following suspicious user activity
- Registry actions correlated with command execution events

### Host Reconnaissance
- Execution of reconnaissance commands (whoami, ipconfig, nslookup)
- Detected via Sysmon process creation telemetry

### DNS Enumeration
- Suspicious query patterns following logon failures
- Correlated with host activity timelines
