## Exercise 1: Secure Network & System Build

### Deliverable A: Network Design & Build
*   **Cisco Packet Tracer:** The primary simulation environment for configuring hubs, switches, routers, and testing static/dynamic routes (OSPF).
*   **Draw.io / Lucidchart:** Web-based diagramming tools for drafting the initial "Hub and Spoke" vs. "Segmented DMZ" architectural designs before building in Packet Tracer.

### Deliverable B: Digital System & OS Hardening
*   **Hyper-V / VirtualBox:** The hypervisor platform for provisioning the Windows Server target environment.
*   **Microsoft Security Compliance Toolkit (SCT):** Used to download and apply official security baseline templates.
*   **Windows Best Practice Analyzer (BPA):** A built-in server management tool to scan for default configuration vulnerabilities.
*   **Microsoft Learn (Website):** Reference for PowerShell firewall configuration syntaxes (`Set-NetFirewallProfile`).

### Deliverable C: Secure Web Application Construction
*   **XAMPP:** The all-in-one local development stack containing Apache, MariaDB (MySQL), and PHP.
*   **Kali Linux VM:** The attacker environment.
*   **Burp Suite Community Edition:** For intercepting HTTP requests, fuzzing file uploads, and testing session token behaviors.
*   **SQLMAP:** The automated tool inside Kali for testing the web app's resilience against database extraction attacks.
*   **OWASP Top 10 (Website):** For referencing secure coding standards and input validation methodologies.

### Deliverable D: Security Components & Key Management
*   **Snort:** The open-source Intrusion Detection and Prevention System (IDPS) for monitoring network traffic hitting the web server.
*   **OpenSSL:** The command-line toolkit used to generate the RSA private keys and self-signed TLS certificates for the Apache server.
*   **Wireshark:** To capture packets on the local loopback or VM interface to mathematically prove that HTTP traffic has transitioned to encrypted HTTPS.
