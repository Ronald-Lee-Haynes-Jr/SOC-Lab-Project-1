
# 🛡️ Endpoint Detection & Logging Lab  
**Author:** Ronald Haynes  
**Tools:** Sysmon, Windows Event Logs, PowerShell Logging  
**Techniques Simulated:** Suspicious PowerShell, LOLBins, Failed Logons

---

## 📘 Overview
This project demonstrates how a Windows 10 endpoint can be configured for enterprise-grade threat detection using Sysmon, PowerShell Script Block Logging, and Security Auditing. The environment was used to simulate attacker-like behavior and analyze captured telemetry.

---

## 🖥️ Environment Setup
- Windows 10 Virtual Machine  
- Sysmon (SwiftOnSecurity config)  
- PowerShell Script Block + Module logging  
- Security event auditing  

---

## 🔥 Simulated Attacks
- Hidden PowerShell execution using `-NoP -NonI -W Hidden`
- LOLBin file download attempt using `bitsadmin`
- Process spawning via `cmd.exe /c calc.exe`
- Multiple failed login attempts to trigger Event ID 4625

---

## 📊 Key Logs Collected
| Log Source | Event IDs | Purpose |
|-----------|-----------|---------|
| Sysmon | 1, 3, 11 | Process, network, and file creation |
| PowerShell | 4103, 4104 | Script block + module logging |
| Security Logs | 4625, 4688 | Login failures + process creation |

Screenshots located in `/screenshots` folder.

---

## 🧠 Findings
- Sysmon captured suspicious PowerShell execution with full command line.
- Network connections to external resources were logged (Event ID 3).
- Password brute force simulation triggered Event ID 4625.
- LOLBin activity (bitsadmin) was captured as abnormal behavior.

---

## 🗂️ Full SOC Report
See: `./report/SOC_Report_Project1.pdf`

---

## 🧩 MITRE ATT&CK Mapping
- **T1059.001 – PowerShell**
- **T1105 – Ingress Tool Transfer**
- **T1110 – Brute Force**
- **T1106 – Execution via Windows utilities**
