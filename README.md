# SOC ANALYST L1 – HANDS-ON PROJECTS
This repository contains my SOC L1 projects. Each project includes attack simulation, detection, log analysis, and documentation.

## LAB SETUP
- VirtualBox for VMs
- Kali Linux (attacker)
- Windows 11 (victim + SIEM)
- Ubuntu Server (logs source)
- Splunk (SIEM)
- Wireshark (network capture)

## PROJECT 1 – REVERSE SHELL ATTACK
**What I did:**
- Created payload with MSFvenom on Kali
- Downloaded and executed on Windows 11
- Got Meterpreter reverse shell
- Captured port 4444 traffic in Wireshark
- Found process creation in Windows Event Log (Event ID 4688)

**Tools:** Kali, Metasploit, MSFvenom, Wireshark, Windows 11, Event Viewer

## PROJECT 2 – RDP BRUTE FORCE
**What I did:**
- Run RDP brute force from Kali using Hydra and Crowbar
- Checked failed logins in Windows Event Log (Event ID 4625)
- Found successful login (Event ID 4624, Logon Type 10)

**Tools:** Kali, Hydra, Crowbar, Windows 11, Event Viewer

## PROJECT 3 – POWERSHELL OBFUSCATION DETECTION
**What I did:**
- Enabled PowerShell Script Block Logging
- Wrote a plain PowerShell script
- Converted it to Base64
- Ran the obfuscated script
- Found decoded script in Event ID 4104

**Tools:** Windows 11, PowerShell, Event Viewer

## PROJECT 4 – PHISHING EMAIL ANALYSIS
**What I did:**
- Created a fake phishing email (.eml file)
- Opened it in Notepad to see raw headers
- Analyzed headers with MxToolbox
- Found malicious IP: 103.212.145.221
- Checked IP on VirusTotal (1/96 flagged)

**Tools:** Windows 11, Notepad, MxToolbox, VirusTotal

## PROJECT 5 – SIEM ALERT TRIAGE
**What I did:**
- Attacked Windows 11 with Hydra and Crowbar from Kali (RDP brute force)
- Generated failed login events (Event ID 4625)
- Added Windows Security Logs to Splunk
- Searched for Event ID 4625 in Splunk
- Created an alert rule (5 failed logins in 15 minutes)
- Made an incident response workflow

**Tools:** Kali, Hydra, Crowbar, Windows 11, Splunk, Event Viewer

## SKILLS I LEARNED
- Attack simulation (reverse shell, RDP brute force, obfuscation)
- Log analysis (Windows Event Logs, Linux auth.log, syslog)
- Network traffic analysis with Wireshark
- SIEM operations with Splunk
- Phishing email analysis and header inspection
- IOC extraction and documentation
- Technical report writing

## PROJECT FILES
- commands.txt (all commands I used)
- Project-Report.pdf (full documentation)
- screenshots/ (all screenshots)

## GITHUB
https://github.com/mubashir-acc-01/SOC-Project

## LINKEDIN
https://www.linkedin.com/in/mohammad-mubashir

**Project by:** Mohammad Mubashir  
**Date:** 6 May 2026
