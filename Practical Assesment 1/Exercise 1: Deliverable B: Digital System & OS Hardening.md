### Deliverable B: Digital System & OS Hardening

**The Goal:** Build, test, and debug a digital system to a specification, configuring an Operating System in accordance with a defined security policy, identifying threats, and leveraging security features.

**Required Tools:** Hyper-V, Windows Server (or target OS), Security Compliance Toolkit, Best Practice Analyser (BPA), Windows Defender Firewall.

#### Phase 1: Build & Specification (Targeting the "Pass" Grade)
You need to provision and assemble the digital system components to meet the exact specification of the scenario.
*   **Action:** Open Hyper-V on your Windows host machine and provision a new virtual machine running the target operating system (e.g., Windows Server). Allocate appropriate virtual processors, memory, and virtual switch connectivity to link it with your Packet Tracer network.
*   **Initial Setup:** Install the base operating system, establish proper administrative account boundaries, and ensure system updates are configured.

#### Phase 2: Security Policy Implementation & Hardening
To satisfy Technical Competency 5, you must configure the operating system according to a strict security policy and integrate it into the system development.
*   **Action:** Run the Best Practice Analyser (BPA) against your system to identify any default configuration vulnerabilities or unoptimized features.
*   **Configuration via Toolkit:** Import Microsoft's official security baseline templates using the Security Compliance Toolkit to enforce strict password complexity, lock-out policies, and audit logging.

**PowerShell Hardening & Firewall Snippets:**

*1. Enforcing Firewall Default Deny and Restricting Access:*
```powershell
# Set default inbound actions to block across all profiles
Set-NetFirewallProfile -Profile Domain,Public,Private -DefaultInboundAction Block

# Allow only necessary inbound management or service ports (e.g., HTTPS)
New-NetFirewallRule -DisplayName "Allow HTTPS Web Traffic" -Direction Inbound -LocalPort 443 -Protocol TCP -Action Allow
```

*2. Auditing and Account Policy Enforcement:*
```powershell
# Configure account lockout threshold via local policy security settings
net accounts /lockoutthreshold:5
net accounts /lockoutduration:30
net accounts /lockoutwindow:30
```

#### Phase 3: Threat Identification & Feature Configuration
Identify potential threats that could compromise the operating system (such as unauthorized access or malware) and configure built-in OS security features.
*   **Threat Identification:** Document threats like privilege escalation, brute-force attacks against administrative logins, and unpatched kernel vulnerabilities.
*   **Security Features Configuration:** Enable features such as User Account Control (UAC) at maximum setting, BitLocker drive encryption for data-at-rest protection, and Windows Defender Real-Time Protection.

#### Phase 4: Testing & Debugging the Digital System
A Pass requires you to build, test, and debug a digital system employing a number of different components to work together seamlessly.
*   **Action:** Verify that the system meets performance, scalability, and security requirements. Test that your firewall rules successfully block unauthorized traffic while allowing legitimate application requests.
*   **Debugging:** If services fail to start or network connectivity is blocked unexpectedly, inspect the Windows Event Viewer logs (specifically Security and Application logs) to troubleshoot and adjust your hardening policies without compromising security.
*   **Evidence Collection:** Capture screenshots of the BPA scan results showing zero critical warnings, output logs from `Get-NetFirewallRule`, and event log validation entries.
