POWERSHELL OBFUSCATION DETECTION

Project Overview
This project demonstrates how attackers use obfuscation techniques like Base64 encoding to hide malicious PowerShell commands, and how SOC analysts can detect them using PowerShell Script Block Logging (Event ID 4104).

Lab Setup
Machine          OS              IP Address        Role
Victim / Analyst Windows 11      Local Machine     PowerShell execution and log analysis

Tools Used
- Windows 11
- PowerShell
- Event Viewer
- Base64 Encoding

Attack Simulation – Obfuscated Script Creation

1. Enable PowerShell Script Block Logging
New-Item -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\PowerShell" -Name "ScriptBlockLogging" -Force
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\PowerShell\ScriptBlockLogging" -Name "EnableScriptBlockLogging" -Value 1

2. Verify Logging is Enabled
Get-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\PowerShell\ScriptBlockLogging"

3. Create Plain Script
@"
Write-Host "Hello from PowerShell"
Start-Process notepad.exe
"@ | Out-File -FilePath C:\Users\Public\plain-script.ps1

4. Base64 Encode the Script
$command = 'Write-Host "Hello from PowerShell"; Start-Process notepad.exe'
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encoded = [Convert]::ToBase64String($bytes)
Write-Host $encoded

5. Execute Obfuscated Script
powershell.exe -EncodedCommand <Base64 String>

Detection – Event Log Analysis

6. View Decoded Script in Event Viewer
- Open Event Viewer (eventvwr.msc)
- Navigate to: Applications and Services Logs → Microsoft → Windows → PowerShell → Operational
- Filter Event ID: 4104
- Message section shows original decoded script

What I Learned
- Script Block Logging (Event ID 4104) captures all PowerShell commands
- Base64 encoding does NOT bypass logging – decoded script appears in log
- Attackers use obfuscation to hide malicious intent, but logging reveals it
- Registry keys control PowerShell logging settings
- Process execution (Start-Process notepad.exe) can be tracked
- SOC analysts can detect obfuscated attacks using Event ID 4104

Repository Contents
- Project-5-Report.pdf – Full project documentation
- commands.txt – All commands used in the project
- README.md – This file
- Screenshots – All captured screenshots

Project Links
GitHub Repository: https://github.com/Mubashir-soc-01/Project-01-Reverse-Shell/tree/main/Project-05-PowerShell-Obfuscation
LinkedIn Profile: https://www.linkedin.com/in/mohammad-mubashir-b729643b7/

Project by: Mohammad Mubashir
Date: 24 March 2026