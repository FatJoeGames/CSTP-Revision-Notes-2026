# CSTP Level 6 EPA: Exercise 1 Master Operational Plan

## Assessment Strategy & Rubric Targets

* **Execution Window:** 12 Hours (+/- 10%) within a 48-hour practical exam completed over two weeks.
* **Practical Deliverable:** A fully configured, multi-subnet network topology, a hardened Linux server VM, and a functional Python web application supporting authenticated file management[cite: 1, 2].
* **Written Deliverable:** A 1,000-word (+/- 10%) technical justification report (900–1,100 words)[cite: 1, 2].
* **Distinction Strategy:** Encompass all three security case layers (Enterprise, Network, Applicati

---
## Dedicated KSB & Competency Mapping Table

| Competency & Knowledge Area | Assessment Standard Requirement | Practical Implementation (Exercise 1) | Distinction Evidence & Alignment |
| :--- | :--- | :--- | :--- |
| **TC2 & TK2: Network Engineering** | Design, build, configure, optimize, test, and troubleshoot complex multi-subnet networks. | Build 3-subnet Packet Tracer topology (Management, DMZ, Internal) with OSPF routing and subinterfaces. | Compare Layer 3 Router vs. Core Switch topologies; log complex OSPF troubleshooting resolution. |
| **TC4 & TK4: Digital System Building** | Build, test, and debug a digital system to specification employing multiple components. | Deploy a Linux OS VM in Hyper-V integrated with web application services and local network controls. | Validate end-to-end telemetry and inter-component communication between client, network gateway, and VM. |
| **TC5 & TK5: OS Hardening & Security** | Configure OS in accordance with security policy, identify threats, and apply security features. | Enforce SSH key-based login, lock root access, configure `pam_pwquality`, deploy UFW firewall, and Fail2ban. | Document residual OS vulnerability risks and map kernel/system hardening policies to organizational policy. |
| **TC8: Software Interfacing & Exploit Analysis** | Construct software interacting with the real world; analyze for buffer overflows, brute force, or SQLi. | Build a Python Flask web app handling authenticated file uploads, file management, and per-user directory isolation. | Execute and capture proof of blocked file upload attacks (`.php` whitelist block) and path traversal (`../` sanitization). |
| **TC18 & TK18: Security Components & Crypto** | Configure $\ge 2$ security components, design crypto system, and implement key management. | Deploy dual-layer firewalls (ACLs + UFW), Fail2ban, TLS 1.3 transport security, and AES-256 file encryption. | Document a full Key Management Lifecycle (generation, secure storage, 90-day rotation, and revocation). |
| **TC19 & TK19: Security Case Design** | Design and evaluate a system in accordance with a justified security case. | Develop a Claim-Argument-Evidence (CAE) matrix covering system threats and implemented mitigations. | Encompass all 3 layers: Enterprise (Policy/IAM), Network (VLANs/TLS), and Application (Validation/AES-256). |
| **TC20 & TK20: Secure Architecture & Assurance** | Architect, analyze, and justify a secure system to achieve security assurance. | Map implemented security controls to legal mandates, business risk appetite, and threat profiles. | Relate all architectural measures to NIST SP 800-53 Rev. 5 and NCSC CAF principles for formal risk owner confidence. |
| **TC26 & TK26: InfoSec Policy & Legislation** | Apply information security policy implementing legal and regulatory requirements. | Draft an InfoSec policy governing file storage, user credentials, and acceptable system usage. | Align controls with UK GDPR / DPA 2018, Computer Misuse Act 1990, and an international standard (e.g., EU NIS 2). |

---
## 12-Hour Step-by-Step Execution Schedule

| Phase | Time Window | Operational Tasks & Deliverables | KSB Mapping Focus |
| :--- | :--- | :--- | :--- |
| **Phase 1: Network Infrastructure** | Hours 01.0–02.5 | Build 3-subnet Packet Tracer topology, configure OSPF routing, set up router subinterfaces (802.1Q), apply ingress ACLs, and document a complex routing troubleshooting scenario. | TC2, TK2 |
| **Phase 2: OS Hardening & Policies** | Hours 02.5–04.5 | Provision Ubuntu/Debian VM in Hyper-V, enforce `pam_pwquality` password rules, lock SSH root access, configure UFW (`default deny`), and install Fail2ban. | TC4, TC5, TK4, TK5 |
| **Phase 3: Application & Cryptography** | Hours 04.5–07.0 | Issue OpenSSL TLS 1.3 certificates, deploy Python Flask web app with `bcrypt` authentication, secure file upload/management, and Fernet AES-256 storage encryption. | TC8, TC18, TK18 |
| **Phase 4: Security Exploit Analysis** | Hours 07.0–08.5 | Execute and record exploit tests using `curl` and Wireshark: malicious file upload block, path traversal block, and cleartext vs. TLS packet captures. | TC8, TC18 |
| **Phase 5: Justification Drafting** | Hours 08.5–11.0 | Draft the 1,000-word (+/- 10%) justification report structured around the 3-layer security case, key management plan, and legal/regulatory standards[cite: 1, 2]. | TC19, TC20, TC26 |
| **Phase 6: Verification & Export** | Hours 11.0–12.0 | Audit word count (900–1,100 words), verify all code/network artifacts, and export `.pkt`, `.pcapng`, and `.py` files into the submission directory[cite: 1, 2]. | Quality Control |

---
