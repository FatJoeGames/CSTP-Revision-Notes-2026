# Written Report & Assessment Breakdown

### Part A: Technical Execution ("What I Did")
* **Word Count:** Unlimited (Not assessed on length, but on comprehensive evidence).
* **Execution Strategy & Breakdown:** 
  * This section serves as your forensic and operational runbook. It must sequentially prove every action taken during the 12-hour block.
  * **Malware Analysis Evidence:** Embed the source code of your custom Python static analysis script alongside its terminal output, proving you scripted a custom toolset (TC9 Distinction). Include screenshots of the Any.run interactive process tree and behavioral flags.
  * **Threat Intelligence & Modeling:** Provide a summary table of the OSINT gathered from simulated dark web and social media sources, followed by your explicit Threat Model (e.g., a STRIDE diagram).
  * **Simulated Attack Logs:** Embed CLI snippets from Nmap and HTTP request/response screenshots from Burp Suite demonstrating the exploitation of the Exercise 1 web application in a lab setting (TC12 Pass).
  * **Digital Forensics Trail:** Provide step-by-step screenshots of configuring the Autopsy software, creating the case, ingesting the data, and the final timeline of events leading up to the simulated breach.

### Part B: Reflective & Justification Analysis ("Why I Did It")
* **Word Count:** Target 1,000 ± 100 words.
* **Sectional Allocation & Strategy:**
  
  * **Section 1: Malware Analysis & Scripting Justification (~250 words)**
    * Explain your methodology for analyzing the malware. 
    * *Distinction Focus:* Justify *why* you chose to write a custom script rather than relying solely on automated sandboxes. Explain how understanding low-level mechanisms (TKU9) allowed you to overcome anti-reverse engineering and obfuscation protections present in the sample, hitting the top criteria for TC9 and TKU9.
  
  * **Section 2: Threat Evaluation & Mitigation Strategy (~300 words)**
    * Detail how the intelligence gathered informed your vulnerability assessment. 
    * *Distinction Focus:* Critically evaluate the threats against your specific web application system. Devise and justify mitigations that go beyond simple technical patches—explain how services, processes, and employee culture must adapt to defend against these specific hazards (TC12 & TKU12 Distinction).
  
  * **Section 3: Assurance & Risk Confidence (~200 words)**
    * Break down the rationale behind your Assurance Strategy. 
    * Define the difference between a 'trusted' and a 'trustworthy' system in the context of your risk assessment (TKU21 Pass). 
    * Explain how integrating 3rd party testing (extrinsic assurance) into your strategy gives the risk owner confidence that your proposed mitigations actually work.
  
  * **Section 4: Legal, Ethical, and Incident Response Compliance (~250 words)**
    * Justify the procedures outlined in your Incident Response plan against English jurisdiction. 
    * Explicitly reference the UK Data Protection Act, GDPR privacy considerations, and the Computer Misuse Act. 
    * Explain how your Autopsy configuration and data handling procedures secured the evidence appropriately to maintain the chain of custody for legal proceedings (TC25 & TKU25 Pass).

---

## 4. Document Audit & Supplemental Requirements

To fully satisfy the explicit and implicit requirements of this scenario and support your written justification, ensure the following distinct documents are generated, clearly labeled, and referenced within your Part A/B submission:

1. **Malware Analysis & Triage Report:** Document containing the output of your custom static analysis script, the SHA-256 hash, and the Any.run dynamic behavioral matrix.
2. **Threat Intelligence & Threat Model (STRIDE):** The OSINT intelligence summary combined with the specific threat model applied to the web application.
3. **Vulnerability & Penetration Test Log:** The raw output of the vulnerability assessment and simulated attack demonstrating system weaknesses.
4. **Assurance Strategy & Risk Assessment Plan:** A formal matrix calculating likelihood and potential impact, paired with the schedule for testing implemented controls.
5. **Incident Response Plan:** A policy document defining team member roles, legal compliance procedures, and privacy protection measures for data handling.
6. **Autopsy Forensic Case Export:** The exported case file, evidence timeline, and preliminary investigation report generated directly from the Autopsy software.
