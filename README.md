# Elevate-Labs-Task-3
Performed a basic vulnerability scan on my PC using Greenbone OpenVAS. Identified and documented DNS cache snooping and TCP timestamp disclosure vulnerabilities. Analyzed severity, researched fixes, and included screenshots and remediation steps in the report.

# 🛡️ Vulnerability Assessment Report - Task 3

## 📌 Objective
Perform a basic vulnerability scan on my PC using OpenVAS (Greenbone Community Edition) to identify common vulnerabilities and learn how to mitigate them.

---

## 🛠️ Tools Used

- **Scanner**: Greenbone Security Assistant (OpenVAS)
- **Scan Date**: May 30, 2025
- **System**: Kali Linux
- **Target IPs**: 
  - `192.168.190.2`
  - `192.168.190.1`

---

## 🎯 Scan Configuration

- **Scan Type**: Full and Fast
- **Scope**: Local network
- **Ports**: All available TCP/UDP
- **Duration**: ~18 minutes
- **Status**: ✅ Completed (99%)

---

## 📊 Vulnerability Findings

| Vulnerability                                             | IP Address      | Port/Protocol | Severity | CVSS Score |
|-----------------------------------------------------------|------------------|----------------|----------|------------|
| DNS Cache Snooping Vulnerability (UDP) - Active Check     | 192.168.190.2    | 53/udp         | Medium   | 5.0        |
| TCP Timestamps Information Disclosure                     | 192.168.190.1    | General/tcp    | Low      | 2.6        |

---

## 🩺 Vulnerability Details

### 1. DNS Cache Snooping (UDP)
- **Description**: Allows an attacker to determine if certain domains have been resolved recently — useful for reconnaissance.
- **Impact**: Privacy and information disclosure.
- **Recommendation**:
  - Disable recursion for external queries on DNS servers.
  - Restrict access to DNS services via firewall rules.

---

### 2. TCP Timestamps Disclosure
- **Description**: TCP timestamps can reveal system uptime, which may help attackers in fingerprinting and exploitation timing.
- **Impact**: Low-risk but contributes to broader attack vectors.
- **Recommendation**:
  - Disable TCP timestamps via:
    ```bash
    sudo sysctl -w net.ipv4.tcp_timestamps=0
    ```
  - To make permanent, add this to `/etc/sysctl.conf`:
    ```bash
    net.ipv4.tcp_timestamps = 0
    ```
  - Apply with: `sudo sysctl -p`

---

## 📖 Key Concepts Learned

- Basics of vulnerability scanning and its importance.
- Difference between information disclosure and exploitation vulnerabilities.
- Introduction to CVSS scoring and threat prioritization.
- Practical remediation techniques for common PC vulnerabilities.

---
