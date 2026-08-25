### Deliverable D: Incident Response & Legal Investigation

**The Goal:** Organise and conduct testing and investigation work in accordance with legal and ethical requirements under English jurisdiction, utilizing Autopsy to perform digital forensics, establish timelines, and secure evidence for potential legal proceedings.

**Required Tools:** Autopsy Forensics Browser, Word Processor.

*Note: Technical Competency 25 and Technical Knowledge & Understanding 25 only have a "Pass" criteria in the marking scheme. The focus is on strict compliance with English law, ethical frameworks, and proper forensic methodology.*

#### Phase 1: Legal & Ethical Framework Review (Targeting TKU25 Pass)
Before touching forensic software, you must demonstrate an understanding of the laws, regulations, and ethical standards that govern intelligence collection, security testing, and incident response.
*   **Action:** Document the specific English jurisdiction laws applicable to the scenario. 
*   **Execution:** Explicitly reference the **Computer Misuse Act 1990** (authorizing ethical hacking/testing versus unauthorized access), the **UK Data Protection Act 2018 / UK GDPR** (governing how you must protect privacy and handle PII during an investigation), and the **Human Rights Act 1998** (right to privacy regarding employee monitoring and intelligence collection).
*   **Ethical Standards:** Reference at least one recognized professional body (e.g., CIISec or (ISC)²) and describe the ethical responsibilities of a cyber-security professional during an investigation, specifically regarding maintaining confidentiality and operating within legal bounds.

#### Phase 2: Incident Response Plan Development (Targeting TC25 Pass)
Develop a comprehensive Incident Response (IR) plan that operationalizes the legal requirements outlined in Phase 1.
*   **Action:** Draft an IR document outlining specific team member roles (e.g., Incident Commander, Lead Forensics Analyst, Legal Counsel Liaison).
*   **Execution:** Define rigid procedures for data collection that maintain the chain of custody (e.g., acquiring bit-for-bit disk images before analysis, utilizing write-blockers). Detail the exact measures your team will take to protect privacy and confidentiality during the investigation, such as redacting customer data from final reports and storing forensic images on encrypted, air-gapped drives.

#### Phase 3: Autopsy Configuration & Case Creation
You must configure the forensic software to suit organizational requirements and ensure compliance with the legal standards for securing evidence.
*   **Action:** Launch Autopsy and begin the case creation process.
*   **Configuration for Legal Compliance:** When setting up the case, ensure you configure Autopsy to automatically calculate MD5 and SHA-256 hashes during data ingestion. This is the critical step to prove evidence integrity and secure it appropriately to support legal proceedings.
*   **Execution:** Create the case by inputting all relevant metadata (Case Name, Examiner Name, Organization). Import the provided data source (the breached disk image or logical file dump).

#### Phase 4: Preliminary Investigation & Timeline Establishment
Conduct the investigation to identify the scope of the breach, affected data, and establish a chronological timeline of events.
*   **Action:** Use Autopsy's ingest modules (e.g., Recent Activity, File Type Identification, Keyword Search) to collect and analyze data.
*   **Execution:** Identify the specific data affected by the simulated attack from Deliverable B. Navigate to Autopsy's Timeline feature to visually map the sequence of events leading up to the breach (e.g., file creation times of the malicious payload, execution timestamps). 

#### Phase 5: Documentation & Artifact Collection
You must meticulously document all aspects of the investigation within Autopsy and export it.
*   **Action:** Utilize Autopsy's tagging and reporting features to flag potential evidence. Generate a final HTML or PDF report directly from Autopsy.
*   **Evidence Collection:** The deliverables for your final Part A/B submission must include:
    1.  The written Incident Response Plan and Legal/Ethical Review.
    2.  Screenshots showing Autopsy configured to calculate cryptographic hashes.
    3.  A screenshot of the Autopsy Timeline view detailing the breach events.
    4.  The generated Autopsy Case Report detailing the data collection, analysis findings, and the subsequent mitigation measures implemented to plug the vulnerability.
