====================================================================================
SECTION 1: Network Architecture, Optimization & Troubleshooting (~250 words)
====================================================================================
1.1 Subnetting & Topology Rationale
    - Justify the segmentation into Management (VLAN 10), DMZ (VLAN 20), and Internal (VLAN 30)[cite: 2].
    - Explain how Router-on-a-Stick 802.1Q subinterfaces isolate broadcast domains and enforce zero-trust traffic flows[cite: 2].
1.2 Alternative Architecture Comparison (Distinction Target)
    - Compare the implemented Router-on-a-Stick topology against a Layer 3 Core Switch design[cite: 2].
    - Evaluate trade-offs: cost, routing latency, single-point-of-failure risks, and stateful inspection capabilities[cite: 2].
1.3 Routing Protocol Optimization & Complex Troubleshooting
    - Justify selecting OSPF Area 0 dynamic routing over static routes for enterprise resilience[cite: 2].
    - Detail the resolution of a logged complex issue (e.g., fixing an asymmetrical OSPF timer mismatch and ACL drop bug)[cite: 2].
1.4 Standards Alignment
    - Map network boundary controls directly to NIST SP 800-53 SC-7 (Boundary Protection)[cite: 2].

====================================================================================
SECTION 2: OS Hardening & Defensive Software Design (~250 words)
====================================================================================
2.1 OS Configuration & Threat Mitigation
    - Justify Linux OS hardening choices: SSH root lockout (`PermitRootLogin no`), RSA key enforcement, and PAM password policy limits[cite: 2].
    - Detail host-level firewall protection (`UFW default deny incoming`) and automated brute-force mitigation using Fail2ban[cite: 2].
2.2 Application Vulnerability Mitigation
    - Explain defensive coding patterns in the Flask file management application[cite: 2].
    - Justify input sanitization (`werkzeug.secure_filename`) to block path traversal attacks (`../`)[cite: 2].
    - Detail file extension whitelisting to prevent arbitrary code execution (e.g., blocking `.php` / `.sh` uploads)[cite: 2].
    - Justify per-user directory isolation (`/uploads/<user_id>/`) to prevent cross-tenant data exposure[cite: 2].
2.3 Standards Alignment
    - Map application controls to NIST SP 800-53 SI-10 (Information Input Validation) and AC-3 (Access Enforcement)[cite: 2].

====================================================================================
SECTION 3: Cryptographic Systems & Key Management Lifecycle (~250 words)
====================================================================================
3.1 Cryptography in Transit & At Rest
    - Justify TLS 1.3 transport layer encryption to eliminate cleartext sniffing across external networks[cite: 2].
    - Detail symmetric AES-256 Fernet payload encryption prior to writing uploaded files to disk[cite: 2].
    - Explain why password hashing uses key-stretching `bcrypt` (work factor 12) to prevent offline dictionary attacks[cite: 2].
3.2 Comprehensive Key Management Lifecycle Plan
    - Generation: High-entropy Pseudo-Random Number Generation (PRNG)[cite: 2].
    - Storage: Restrict private key permissions (`chmod 600`) owned exclusively by the service user[cite: 2].
    - Distribution & Rotation: Enforce mandatory 90-day key rotation schedules[cite: 2].
    - Revocation & Emergency Procedures: Define process for compromised cert revocation via CRL/OCSP[cite: 2].
3.3 Standards Alignment
    - Map crypto mechanisms to NIST SP 800-53 SC-8 (Transmission Confidentiality) and SC-28 (Protection at Rest)[cite: 2].

====================================================================================
SECTION 4: 3-Layer Security Case, Assurance & Legal Compliance (~250 words)
====================================================================================
4.1 Three-Layer Security Case (Claim-Argument-Evidence)
    - Enterprise Layer: Information Security Policy, identity access governance, and acceptable use mandates[cite: 2].
    - Network Layer: VLAN micro-segmentation, stateful ingress ACLs, TLS 1.3 transport security[cite: 2].
    - Application Layer: `bcrypt` password hashing, input validation, Fernet AES-256 file encryption at rest[cite: 2].
4.2 Legal & Regulatory Framework Alignment
    - UK GDPR / Data Protection Act 2018: Compliance with Article 32 (Security of Processing) via data encryption and strict access control[cite: 2].
    - Computer Misuse Act 1990: Enforcing Section 1 and Section 3 access prohibitions via Fail2ban logging and authentication checks[cite: 2].
    - Non-UK Regulation (EU NIS 2 Directive): Aligning supply chain risk management and mandatory incident reporting protocols[cite: 2].
4.3 System Assurance Framework
    - Relate the complete technical solution to the NCSC Cyber Assessment Framework (CAF) to give the risk owner formal solution confidence[cite: 2].
====================================================================================
