## Deliverable C: Assurance Strategy

**The Goal:** Develop a comprehensive assurance strategy that incorporates a risk assessment plan, dictates specific mitigation controls, outlines the methodology for testing those controls, and establishes incident response procedures.

**Required Tools:** Word Processor, Spreadsheet Application (for Risk Matrix).

*Note: Technical Competency 21 and Technical Knowledge & Understanding 21 only have a "Pass" criteria in the marking scheme (Merit/Distinction are N/A). The focus here is on thoroughness and explicitly addressing all theoretical concepts required by the standard.*

#### Phase 1: Risk Assessment Plan (Targeting the "Pass" Grade)
You must formally determine the likelihood and potential impact of the threats you identified during the OSINT and simulated attack phases in Deliverable B.
*   **Action:** Create a quantitative or qualitative Risk Assessment Matrix. 
*   **Execution:** For each threat (e.g., Directory Traversal, Ransomware Infection via Phishing), assign a Likelihood score (e.g., 1-5) and an Impact score (e.g., 1-5). Multiply them to generate a Risk Rating.
*   **Documentation:** Clearly state which risks are deemed unacceptable and require immediate treatment (mitigation) via your assurance strategy.

**Risk Matrix Example Table (Markdown format for your report):**
| Threat / Vulnerability | Likelihood (1-5) | Impact (1-5) | Risk Score | Decision |
| :--- | :--- | :--- | :--- | :--- |
| Directory Traversal on `/upload.php` | 4 | 5 | 20 (Critical) | Mitigate |
| Ransomware via Employee Phishing | 3 | 5 | 15 (High) | Mitigate |

#### Phase 2: Developing the Assurance Strategy (Targeting TKU21 Pass)
Your strategy must outline specific actions to reduce risk and explicitly demonstrate your knowledge of assurance concepts.
*   **Action:** Draft the Assurance Strategy document. You must explicitly define and contrast a **"trusted"** system (one that relies on faith, reputation, or claims without proof) against a **"trustworthy"** system (one that provides verifiable evidence of its security controls). Explain that your strategy aims to make the web application trustworthy.
*   **Intrinsic Assurance:** Describe at least two ways the organization can provide intrinsic assurance. Example: Implementing mandatory secure coding standards (like OWASP Top 10) during application design, and enforcing internal peer code reviews before deployment.
*   **Extrinsic Assurance:** Describe the main approaches to extrinsic assurance (validating security from outside the development process). Give a specific example, such as adopting the Common Criteria standard or engaging in supply chain assurance audits, explaining both the benefits (objective validation) and limitations (high cost, snapshot in time).

#### Phase 3: Control Testing Methodology (Targeting TKU21 Pass)
You must describe how you will test the effectiveness of the controls put in place to mitigate your identified risks.
*   **Action:** Detail a testing schedule that combines both automated and manual techniques.
*   **Execution:** Explicitly explain what 3rd party testing (e.g., "ethical hacking" or penetration testing) is and how it contributes to assurance. Document that you will hire an external CREST-certified penetration testing firm annually to simulate advanced persistent threats (APTs), ensuring your WAF and input validation controls actually hold up against live, unbiased attacks.

#### Phase 4: Defining Incident Response Procedures
Identify and document baseline procedures for incident response in the event a security breach bypasses your tested controls. (This perfectly sets up Deliverable D).
*   **Action:** Outline a standard framework, such as the PICERL methodology (Preparation, Identification, Containment, Eradication, Recovery, Lessons Learned).
*   **Execution:** For the threats in your risk matrix, write a brief procedure. For example, if ransomware is identified (Identification), the immediate procedure is to isolate the affected host from the network switch (Containment) and trigger the backup restoration protocol (Recovery).

#### Phase 5: Evidence & Artifact Collection
*   **Action:** Collate the Risk Assessment Matrix, the drafted Assurance Strategy (ensuring the bolded TKU21 keywords are heavily featured), the control testing schedule, and the high-level Incident Response flowchart. These text-based artifacts will form a massive portion of your Part B written justification.
