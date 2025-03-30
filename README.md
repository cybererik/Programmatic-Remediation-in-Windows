# Programmatic Remediation in Windows


![Introduction_Vulnerability Management Lab Overview](https://github.com/user-attachments/assets/395f93a3-db26-46b4-b8b3-de1d8514e576)


## Overview
This project focuses on programmatic remediation of security vulnerabilities in a Windows 10 virtual machine (VM). By leveraging tools like Microsoft Azure and Tenable, we provisioned a VM, performed authenticated vulnerability scans using the DISA STIG template, and automated the remediation process using PowerShell scripts. This project simulates the actions a cybersecurity analyst would take to resolve vulnerabilities in a enterprise environment.

## Tools & Technologies
- **Microsoft Azure** (Virtual Machine)
- **Tenable Vulnerability Management Platform** (Authenticated Scans)
- **PowerShell** (Automated Remediation Scripts)

## Objective(s)
- Provision a Windows 10 Pro VM on Microsoft Azure.
- Run an authenticated vulnerability scan using Tenable Enterprise with the DISA STIG template.
- Simulate vulnerability creation (e.g., outdated software, insecure protocols).
- Remediate vulnerabilities programmatically using PowerShell scripts.
- Re-run authenticated scans to verify remediation success.

## Setup Instructions

### Step 1: Provision a Windows 10 Pro VM
1. Create a new Virtual Machine (VM) on **Microsoft Azure** with Windows 10 Pro as the OS.
2. Ensure the VM is fully patched and up to date before proceeding.

### Step 2: Create an Authenticated Scan in Tenable
1. Log into **Tenable Enterprise**.
2. Create an **Authenticated Scan** using the **Windows 10 DISA STIG** template to scan the VM for vulnerabilities.
   - **What is DISA STIG?**
     The **Defense Information Systems Agency (DISA)** provides **Security Technical Implementation Guides (STIGs)**, which are cybersecurity configuration guidelines for various technologies. The **Windows 10 DISA STIG** helps ensure Windows operating systems meet security baselines by identifying potential vulnerabilities and enforcing secure configurations. This template is critical for system administrators and cybersecurity analysts to ensure compliance with industry-standard security practices.

### Step 3: Manually Introduce Vulnerabilities
To simulate common vulnerabilities, we manually introduced several issues:
1. **Old Version of Firefox** (Insecure Software)
   - [Vulnerability Link](https://drive.google.com/drive/u/6/folders/1y1pSHgkpWpgDTDkYmV4bZDZtiPP6i-GA)
2. **Enable SMBv1**
3. **Enable Discouraged Cryptographic Protocols** (SSL 2.0, SSL 3.0, TLS 1.0, TLS 1.1)
   - [PowerShell Script for Protocols](https://github.com/joshmadakor1/lognpacific-public/blob/main/automation/toggle-protocols.ps1)

### Step 4: Restart the VM
After introducing the vulnerabilities, restart the VM to apply changes.

### Step 5: Run Authenticated Scan Again
Run another **Authenticated Scan** on the **Azure VM** using Tenable Enterprise to capture the state of the vulnerabilities. This provides a baseline before remediation.

## Implementation

### Step 6: Create PowerShell Scripts for Programmatic Remediation
To simulate real-world remediation in large environments, I wrote PowerShell scripts to automate vulnerability remediation. The goal is to remove bad configurations automatically, without manual intervention, while testing the scripts in a sandbox environment first.

1. **Uninstall Old Version of Firefox**: 
   - [PowerShell Script - Firefox Uninstall](https://github.com/joshmadakor1/lognpacific-public/blob/main/automation/remediation-FireFox-uninstall.ps1)
   
2. **Disable SMBv1**: 
   - [PowerShell Script - SMBv1 Disable](https://github.com/joshmadakor1/lognpacific-public/blob/main/automation/remediation-SMBv1.ps1)
   
3. **Disable Insecure Cryptographic Protocols**:
   - [PowerShell Script - Disable Protocols](https://github.com/joshmadakor1/lognpacific-public/blob/main/automation/toggle-protocols.ps1)

### Step 7: Restart the VM After Remediation
Once the remediation scripts have been executed, restart the VM to apply the fixes.

### Step 8: Run Final Authenticated Scan
Run the **Authenticated Scan** again after remediation to validate the success of the applied fixes and verify that the vulnerabilities have been resolved.

## Testing & Verification
After running the scan post-remediation, compare the results with the previous scan to evaluate the effectiveness of the automated remediation. Successful remediation should show a reduction in the number of critical vulnerabilities, and the system should now meet security compliance standards.

## Conclusion
In this project, we simulated a real-world remediation process by leveraging tools like Tenable Enterprise and PowerShell. By automating the remediation of vulnerabilities, we demonstrated the importance of efficient, scalable solutions for managing system security. Future improvements could include extending the scripts to handle more vulnerabilities or integrating this process into a Continuous Integration/Continuous Deployment (CI/CD) pipeline for automated security compliance checks.

## References
- [DISA STIGs](https://public.cyber.mil/stigs/)
- [Tenable Enterprise](https://www.tenable.com/products/tenable.io)
