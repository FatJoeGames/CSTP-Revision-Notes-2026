# Exercise 2: Operational & Implementation Master Plan

## 1. Operational Plan Document

**Assessment Strategy:** 
The objective of this 12-hour practical test is to execute secure testing routines, analyze malware, gather threat intelligence, exploit a previously built web application, and conduct a digital forensics investigation. To achieve Distinction marks, execution must move beyond automated tools to include custom malware analysis scripting (TC9) and the devising of comprehensive, process-level mitigations for discovered vulnerabilities (TC12). All testing and investigations must strictly adhere to English jurisdiction legal frameworks, including data protection laws and ethical standards.

**KSB Competency Mapping Table:**

| KSB Code | KSB Description | Practical Task Alignment |
| :--- | :--- | :--- |
| **TC9** | Analyse malware & identify its mechanisms. | Sourcing from VirusShare, executing Any.run dynamic analysis, and writing custom analysis scripts. |
| **TC12** | Discover, identify, and analyse threats & vulnerabilities. | OSINT gathering, threat modeling, vulnerability assessment, and simulating a real-world attack. |
| **TC21** | Develop an assurance strategy. | Creating a risk assessment plan and defining an assurance strategy that tests implemented controls. |
| **TC25** | Organise testing & investigation within legal reqs. | Configuring Autopsy software and conducting digital forensics compliant with UK privacy laws. |
| **TKU9** | Malware, reverse engineering, obfuscation. | Identifying low-level mechanisms, anti-debugging techniques, and scripting custom toolsets. |
| **TKU12** | Threats, vulnerabilities, impacts and mitigations. | Evaluating the threat landscape, horizon scanning, and devising mitigations for ICT systems. |
| **TKU21** | Assurance concepts and approaches. | Explaining 'trustworthy' vs 'trusted', and integrating 3rd party testing (extrinsic assurance). |
| **TKU25** | Applicability of laws, regulations, and ethical standards. | Justifying intelligence collection and incident response against UK data protection and privacy laws. |

**Hour-by-Hour Implementation Guide:**

| Hour | Action Step | Target KSBs | Output Deliverable |
| :--- | :--- | :--- | :--- |
| **1-2** | Malware sourcing (VirusShare), static analysis scripting, Any.run execution. | TC9, TKU9 | Custom script output, Any.run behavioral report. |
| **3** | OSINT threat intelligence gathering (Dark web, social media). | TC12, TKU12 | Intelligence summary report. |
| **4** | Develop specific Threat Model based on OSINT intelligence. | TC12, TKU12 | Formal Threat Model document. |
| **5-7** | Vulnerability assessment and simulated real-world attack on the web application. | TC12, TKU12 | Penetration test logs and exploitation evidence. |
| **8** | Develop Assurance Strategy, Risk Assessment, and Control Testing Plan. | TC21, TKU21 | Assurance Strategy Document. |
| **9** | Draft Incident Response Plan mapping roles, legal frameworks, and privacy measures. | TC21, TC25 | Incident Response Plan. |
| **10-11** | Configure Autopsy, create case, ingest evidence, and conduct preliminary investigation. | TC25, TKU25 | Autopsy Case File & Evidence Timeline. |
| **12** | Documentation: Collate evidence, finalize Part A & Part B written justifications. | TC9, TC12, TC25 | Completed 1000-word written justification. |

---
## 2. Deliverable Execution Plans

### Deliverable A: Malware Analysis & Identification
* **Overview & Goal:** Source, analyze, and identify mechanisms of a malware sample, scripting custom tools to achieve Distinction. 
* **Tools & Software Required:** Any.run, VirusShare, Python (pefile, hashlib).
* **Technical Step-by-Step Breakdown:**
  1. Download a highly obfuscated or packed malware sample from the VirusShare public repository.
  2. Write and execute a custom Python script (Distinction requirement) to extract static indicators of compromise (IoCs), imported DLLs, and file entropy to detect packing or anti-reverse engineering techniques.
  3. Upload the sample to Any.run and conduct dynamic analysis.
  4. Observe the interactive report to determine the malware's type and purpose (e.g., ransomware, C2 beaconing) and formulate specific mitigation actions.
* **Code, Scripts & Configurations:**
  ```python
  # Custom Static Analysis Script (Fulfills TC9 Distinction Requirement)
  import pefile
  import hashlib

  def analyze_malware(filepath):
      with open(filepath, "rb") as f:
          file_data = f.read()
          print(f"SHA-256: {hashlib.sha256(file_data).hexdigest()}")
      
      try:
          pe = pefile.PE(filepath)
          print("\n[+] Imported DLLs & Functions (Checking for Anti-Reversing):")
          for entry in pe.DIRECTORY_ENTRY_IMPORT:
              print(f"[-] {entry.dll.decode('utf-8')}")
              for imp in entry.imports:
                  if imp.name:
                      # Flag common anti-debugging/obfuscation APIs
                      if imp.name.decode('utf-8') in ['IsDebuggerPresent', 'VirtualAlloc']:
                          print(f"  [!] SUSPICIOUS API FOUND: {imp.name.decode('utf-8')}")
      except Exception as e:
          print(f"Error parsing PE (Possible heavy obfuscation/packing): {e}")

  analyze_malware("virusshare_sample.exe")
  ```
* **Evidence & Artifact Collection:** Custom Python script source code, script execution terminal output, Any.run interactive process tree screenshot, and behavioral flags export detailing the mitigation plan.

---

### Deliverable B: Threat Intel, Threat Modeling & Vulnerability Assessment
* **Overview & Goal:** Gather OSINT intelligence, model specific threats, conduct a vulnerability assessment, and simulate a real-world attack against the Exercise 1 web application.
* **Tools & Software Required:** Kali Linux, Burp Suite, Nmap, OSINT Frameworks.
* **Technical Step-by-Step Breakdown:**
  1. Conduct OSINT gathering by monitoring simulated social media platforms and dark web forums to collect intelligence on potential threats.
  2. Create a specific Threat Model (e.g., using STRIDE) that outlines threats based on the gathered intelligence.
  3. Conduct a vulnerability assessment on the web application developed in Exercise 1 to identify software vulnerabilities and configuration errors.
  4. Simulate a real-world attack in the lab setting (e.g., fuzzing with Burp Suite or port scanning with Nmap) to identify defensive weaknesses.
* **Code, Scripts & Configurations:**
  ```bash
  # Vulnerability Scanning & Simulated Attack Commands
  # 1. Enumerate the target application surface to find configuration errors
  nmap -sV --script http-enum <web-app-ip>
  
  # 2. Simulate directory traversal payload via CLI (or use Burp Repeater)
  curl -X POST -F "file=@/etc/passwd;filename=../../../var/www/html/shell.php" http://<web-app-ip>/upload.php
  ```
* **Evidence & Artifact Collection:** Threat intelligence summary documentation, Threat Model outline, vulnerability assessment log, Burp Suite request/response screenshots showing exploits, and Nmap scan output logs.

---

### Deliverable C: Assurance Strategy
* **Overview & Goal:** Develop a risk assessment plan, a comprehensive assurance strategy mapping mitigations to threats, and incident response procedures.
* **Tools & Software Required:** Word Processor / Spreadsheet for Risk Matrix.
* **Technical Step-by-Step Breakdown:**
  1. Develop a Risk Assessment Plan calculating the likelihood and potential impact for each threat identified in Deliverable B.
  2. Draft an Assurance Strategy detailing specific actions and controls to reduce the risk of each identified threat, vulnerability, and attack technique.
  3. Define explicit testing methodologies to evaluate the effectiveness of the implemented controls (e.g., scheduling penetration tests or code reviews).
  4. Identify and document baseline procedures for incident response in the event of a security breach.
* **Code, Scripts & Configurations:** N/A (Documentation focused).
* **Evidence & Artifact Collection:** Risk Assessment Matrix document, Assurance Strategy document outlining control testing, and the preliminary Incident Response procedures.

---

### Deliverable D: Incident Response & Legal Investigation
* **Overview & Goal:** Plan a comprehensive incident response and conduct digital forensics using Autopsy while strictly adhering to UK legal and ethical requirements.
* **Tools & Software Required:** Autopsy Forensics Browser.
* **Technical Step-by-Step Breakdown:**
  1. Review legal and ethical requirements (e.g., Data Protection Act, privacy laws, industry standards) relevant to incident response.
  2. Develop a comprehensive Incident Response Plan that outlines team roles, data collection/analysis procedures, and privacy protection measures.
  3. Configure the Autopsy software to suit the organization's legal requirements and analyze the affected data types.
  4. Conduct a preliminary investigation using Autopsy to identify the scope of the breach and collect potential evidence.
  5. Create a Case in Autopsy, input all relevant data, establish a timeline of events, and extensively document the data collection, analysis, and mitigation measures.
* **Code, Scripts & Configurations:** N/A (GUI based forensics).
* **Evidence & Artifact Collection:** Comprehensive Incident Response Plan, Autopsy Case summary screenshot, Autopsy Timeline view screenshot, and the exported forensic investigation documentation from Autopsy.
