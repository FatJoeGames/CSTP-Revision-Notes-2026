1. System Assurance Strategy (TC21 & TKU21)
Document Location: Justification Document (Section: System Assurance) & Appendix C (Information Security Management)
1.1 Assurance Philosophy: Trusted vs. Trustworthy House Tech differentiates between "trusted" and "trustworthy" components across its Head Office, Distribution Centres, and Retail Stores: 
	Trusted Components: Systems that are relied upon by default to enforce security boundaries (e.g., store Point-of-Sale (POS) terminals, perimeter firewalls, and domain controllers). If a trusted component fails or is compromised, the security of the entire network segment is lost. 
	Trustworthy Components: Systems that provide verifiable, repeatable, and objective evidence (audit logs, cryptographically signed binaries, passed penetration test reports) proving they operate securely under adversarial conditions. The House Tech goal is to transition critical infrastructure from merely "trusted" to demonstrably "trustworthy". 
1.2 Assurance Framework & Lifecycle Implementation House Tech applies a hybrid assurance model combining intrinsic and extrinsic controls across the software and infrastructure lifecycle: 
Assurance Category	Implementation Mechanics	Applied House Tech Context
Intrinsic Assurance (Built-in)	Secure software development lifecycle (SSDLC), automated SAST/DAST, static configuration baselining, and least-privilege access control. 	Hardened Debian 13 server baselines, parameterized SQL queries in custom inventory tools, UFW strict default-deny rules. 
Extrinsic Assurance (External Verification)	Third-party penetration testing, red team simulation, vulnerability disclosure programs, and independent ISO/IEC 27001 audits. 	Annual CREST-accredited penetration testing of the external DMZ file portal and internal POS network isolation. 
Operational Assurance (Continuous)	Automated patch management, SIEM log correlation, host integrity monitoring (AIDE/Wazuh), and vulnerability scanning. 	Unattended-upgrades on Linux hosts, daily Lynis auditing, and centralized Syslog export from edge routers. 

2. Legal, Ethical, & Incident Investigation Framework (TC25 & TKU25)
Document Location: Appendix C (Section: Compliance, Legal, & Forensic Protocols)
2.1 UK Legal Jurisdiction & Statutory Compliance All testing, threat analysis, and incident investigations conducted within House Tech operate strictly under English Jurisdiction and adhere to the following statutory frameworks: 
	Computer Misuse Act (CMA) 1990:
	Section 1 (Unauthorized Access): All internal security testing and vulnerability scanning must be explicitly pre-authorized via formal Written Rules of Engagement signed by the CISO.
	Section 2 (Unauthorized Access with Intent to Commit Further Offences): Prohibits pivot testing outside of approved lab boundaries during malware containment.
	Section 3 (Unauthorized Acts Impairing Operation): Mandatory safeguards (e.g., non-destructive exploit payloads, isolated VLAN execution) to prevent denial-of-service on live POS systems or warehouse management tools.
	Data Protection Act (DPA) 2018 / UK GDPR:
	Mandates that forensic memory dumps or log captures containing employee or customer PII are strictly pseudonymized, encrypted at rest using AES-256, and restricted to authorized incident responders under Lawful Basis (Article 6(1)(f) Legitimate Interests). 
	Human Rights Act 1998 (Article 8 - Right to Privacy):
	Ensures workplace monitoring during incident response is targeted exclusively at corporate assets and proportioned directly to the security risk.
2.2 Forensic Evidence Handling Procedure (ISO/IEC 27037 Standard) When investigating suspected malware or network breaches across retail stores or distribution centres, the technical team adheres to a strict four-stage chain of custody: 
	Identification & Volatility Preservation: Follow the order of volatility (RAM → Network State → Swap/Page Files → Disk Images → Archival Backups).
	Collection & Acquisition:
	Capture volatile memory using LiME or FTK Imager prior to host shutdown.
	Perform bit-stream disk imaging using a hardware write-blocker (e.g., Tableau T8u) to prevent write contamination.
	Integrity Verification:
	Generate dual cryptographic checksums (SHA-256 and SHA-512) immediately upon image completion.
	Document checksums in the master Master Evidence Register. Any hash mismatch invalidates the evidence for legal proceedings. 
	Chain of Custody Documentation: Every item seized must be accompanied by an Evidence Custody Form detailing: Unique Evidence ID, Date/Time, Seizing Officer, Source Hostname/MAC, Cryptographic Hash, Storage Location, and Transfer Log.
2.3 Professional Ethical Standards
All technical staff must adhere to the BCS Code of Conduct and CIISEC Ethical Principles:
	Maintain professional competence and refrain from executing diagnostic tools beyond verified capabilities.
	Ensure absolute confidentiality of proprietary House Tech inventory datasets and vulnerability records.
	Disclose all identified security weaknesses immediately to system owners without suppression or unauthorized external exposure.

3. Threat & Vulnerability Analysis Methodology (TC12 & TKU12)
Document Location: Justification Document (Section: Threat Intelligence & Vulnerability Management)
3.1 Threat Intelligence Integration & Adversarial Modeling House Tech faces specific threat vectors targeting retail store networks (POS scraping) and logistics operations (Ransomware targeting Distribution Centre Warehouse Management Systems). Threat analysis synthesizes multiple authoritative intelligence feeds: 
	OWASP Top 10 (2021/2026): Addresses web application attack vectors on public portals (A01: Broken Access Control, A03: Injection). 
	MITRE ATT&CK Framework (Enterprise): Maps adversary Tactics, Techniques, and Procedures (TTPs) across the retail environment (e.g., T1078 Valid Accounts, T1059 Command and Scripting Interpreter, T1046 Network Service Discovery). 
	NIST National Vulnerability Database (NVD) & CISA KEV: Real-time tracking of Common Vulnerabilities and Exposures (CVEs) affecting deployed infrastructure (Debian Linux, Apache2, MariaDB). 
3.2 Laboratory Threat Demonstration & Technical Mitigations
[External Attacker] 
       │
       ▼ (HTTPS / Port 443)
[Edge Router / Firewall (UFW)] ──(Blocked via ACL)──► [Internal POS Segment (VLAN 2)]
       │
       ▼ (Allowed)
[DMZ Segment (VLAN 4)] ──► [Hardened Web/DB Host]
                            │
                            ├─► Input Validation (PDO Prepared Statements)
                            └─► Isolated Storage Directory (/var/www/uploads)
Discovered Threat Vector	Attack Mechanism (Lab Execution)	Business Impact	Technical Mitigation Strategy
SQL Injection (SQLi)	Automated query manipulation via SQLMap against web application authentication endpoints. 	Complete compromise of backend ht_db_sec database and PII exfiltration. 	Enforce PDO parameterized queries, strict input type-casting, and database user isolation (ht_db_usr restricted to localhost). 
Unauthenticated SSH Brute-Force	Rapid dictionary login attempts targeting Port 22/TCP. 	Unauthorized remote terminal access and privilege escalation. 	Disable root SSH login (PermitRootLogin no), enforce libpam-pwquality complexity rules, deploy Fail2ban, and restrict SSH access to admin jump hosts. 
Inter-VLAN Lateral Movement	Network pivoting from compromised store workstation to POS subnet. 	Exposure of payment transaction processing and PCI-DSS compliance failure. 	Implement hardware layer-3 router Access Control Lists (ACLs) enforcing strict deny ip rules between disparate VLAN subnets. 

4. Malware Analysis Workflow & Investigation Protocol (TC9 & TKU9)
Document Location: Appendix A (Section: Malware Analysis & Technical Reverse Engineering) & Appendix B (Execution Logs)
4.1 Tri-Stage Malware Analysis Methodology When an suspicious binary or web shell is identified within the House Tech file upload portal or endpoint systems, it undergoes a structured analysis workflow in an air-gapped sandbox environment: 
+-----------------------------------------------------------------------------------+
|                            1. STATIC ANALYSIS                                     |
|  - Cryptographic Hashing (SHA-256)        - String Extraction (`strings -a`)       |
|  - File Header Identification (`file`)    - Packer Detection (UPX / PEiD)          |
+-----------------------------------------------------------------------------------+
                                         │
                                         ▼
+-----------------------------------------------------------------------------------+
|                            2. DYNAMIC ANALYSIS                                    |
|  - Sandbox Execution (Cuckoo / REMnux)   - Process Monitoring (`sysmon` / `strace`)|
|  - Network Traffic Capture (`wireshark`)  - File/Registry Change Tracking          |
+-----------------------------------------------------------------------------------+
                                         │
                                         ▼
+-----------------------------------------------------------------------------------+
|                        3. REVERSE ENGINEERING / CODE ANALYSIS                     |
|  - Disassembly (Ghidra / IDA Pro)         - Anti-Debugging Bypass (x64dbg)        |
|  - Assembly Instruction Tracing           - De-obfuscation (XOR / Base64 Decoding) |
+-----------------------------------------------------------------------------------+

4.2 Obfuscation Handling & Analysis Techniques Modern malware targeting retail infrastructure frequently employs anti-analysis techniques: 
	Packed Binaries (e.g., UPX): Identified via anomalous section headers (UPX0, UPX1) and disproportionate file-size-to-string ratios. Mitigated by performing manual or automated unpacking (upx -d) prior to disassembly.
	XOR & Base64 Payload Encryption: Obfuscated strings designed to bypass signature-based AV/YARA checks. Analyzed using Cybershef recipes or custom Python scripts to iterate through 1-byte XOR keys (0x00-0xEF).
	Anti-Debugging & Evasion: Malware checking for debugger presence via API calls (IsDebuggerPresent, CheckRemoteDebuggerPresent) or timing checks (RDTSC). Defeated by setting breakpoint hooks or utilizing debugger plugins (e.g., ScyllaHide) to patch return values in real-time.

5. Master KSB Mapping & Appendix File Structure
Use this mapping schema to organize content across your Word documents and ensure full coverage: 
Primary Document	Document Section	Target KSBs / Rubric Modules	Content Focus
Justification Document	Section 1: System Architecture	TC12, TKU12, TC20 	Network design justification, Threat landscape analysis, OWASP/MITRE mapping. 
Justification Document	Section 2: System Assurance Strategy	TC21, TKU21, TC20 	Trusted vs. Trustworthy, Intrinsic/Extrinsic/Lifecycle assurance models. 
Justification Document	Section 3: Legal & Regulatory Compliance	TC25, TC26, TKU25, TKU26 	Statutory compliance (CMA 1990, DPA 2018, UK GDPR, PCI-DSS). 
Appendix A	Section 1: Practical Test Execution & Screenshots	TC9, TC12 	Terminal logs, lab setup diagrams, sandbox execution captures. 
Appendix A	Section 2: Malware Reverse Engineering Logs	TC9, TKU9 	Static/Dynamic analysis output, string dumps, assembly disassembly snippets. 
Appendix B	Raw Log Output Files	TC9, TC12 	Full Wireshark .pcap summaries, YARA rule definitions, automated scan reports. 
Appendix C	Corporate Security Policies & Frameworks	TC21, TC25, TC26 	Information Security Policy, Forensic Evidence Handling Protocol, ISO 27037 Policy.

7. Academic & Professional References
Include these references in the references section of your main document: 
	British Computer Society (BCS) (2022) BCS Code of Conduct for Members. Swindon: BCS.
	CISA (2026) Known Exploited Vulnerabilities Catalog. Cybersecurity and Infrastructure Security Agency. Available at: https://www.cisa.gov/known-exploited-vulnerabilities-catalog (Accessed: 9 September 2026).
	ISO/IEC (2012) ISO/IEC 27037:2012 Information technology — Security techniques — Guidelines for identification, collection, acquisition and preservation of digital evidence. Geneva: International Organization for Standardization.
	MITRE (2026) MITRE ATT&CK Framework: Enterprise Matrix. Available at: https://attack.mitre.org/ (Accessed: 9 September 2026).
	National Institute of Standards and Technology (2020) Security and Privacy Controls for Information Systems and Organizations (NIST Special Publication 800-53, Revision 5). Gaithersburg: NIST.
	OWASP (2021) OWASP Top Ten Web Application Security Risks. Open Web Application Security Project. Available at: https://owasp.org/Top10/ (Accessed: 9 September 2026).
	UK Governance (1990) Computer Misuse Act 1990. London: The Stationery Office. Available at: https://www.legislation.gov.uk/ukpga/1990/18/contents (Accessed: 9 September 2026). 
	UK Governance (2018) Data Protection Act 2018. London: The Stationery Office. Available at: https://www.legislation.gov.uk/ukpga/2018/12/contents (Accessed: 9 September 2026). 

