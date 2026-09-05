### Deliverable B: Risk Modelling & External Standard Assessment

**The Goal:** Utilize insights gained from data analysis to identify vulnerabilities, perform risk analysis, compare distinct risk modelling techniques to justify financial investments, and assess the organization's infrastructure against an external cybersecurity standard.

**Required Tools:** Spreadsheet Software (Excel/Google Sheets), Formal Framework Documentation (NIST CSF or ISO/IEC 27001), Word Processor.

#### Phase 1: Vulnerability Identification & Baseline Risk Assessment (Targeting TC15 & TC16 Pass)
You must translate the technical anomalies discovered in Deliverable A into documented business vulnerabilities and perform a baseline risk assessment.
*   **Action:** Review the Python clustering charts (from Deliverable A) indicating potential unauthorized access or data exfiltration.
*   **Execution:** Identify the specific weaknesses in the network security architecture that allowed the anomaly to occur (e.g., lack of egress filtering, weak access controls).
*   **Risk Analysis:** Perform a quantitative and qualitative risk analysis to determine the likelihood and potential impact of each vulnerability, prioritizing them based on their severity. Note how these cyber risks relate to broader business and operational risks (e.g., reputational damage, regulatory fines).

#### Phase 2: Comparative Risk Modelling (Targeting TC15 Merit)
To achieve the Merit for Technical Competency 15, you must explicitly compare and contrast two distinct system modelling techniques.
*   **Action:** Select two methodologies from the approved list: SABSA, DBSy, CVSS scoring, STRIDE, or NIST 800-154. (Recommendation: STRIDE and CVSS).
*   **Execution:** 
    *   **Model 1 (STRIDE):** Apply this architectural threat modelling technique to categorize the threat (e.g., Information Disclosure due to exfiltration).
    *   **Model 2 (CVSS):** Apply this technical scoring system to rate the severity of the underlying vulnerability (e.g., assigning a Base Score of 8.5 for a network-exploitable misconfiguration).
*   **Comparison:** Explicitly compare and contrast the differences between the two techniques. Document how STRIDE informs qualitative risk analysis by focusing on architectural flaws, whereas CVSS informs quantitative risk analysis by providing a standardized severity metric.

#### Phase 3: Trade-Offs & Business Case (Targeting TC15 Distinction)
To secure the TC15 Distinction, you must use your comparative modelling to identify investment options and present trade-off arguments in a business case.
*   **Action:** Draft a brief business case illustrating commercial and value-for-money judgement.
*   **Execution:** Propose two investment options to mitigate the identified risks. 
    *   *Option A:* Implement a fully managed 3rd-party SIEM (High cost, low internal resource burden, fast deployment).
    *   *Option B:* Deploy an open-source IDS/IPS like Snort (Low software cost, high internal resource burden, slower tuning).
*   **Trade-off Argument:** Justify the recommended investment measure based on the STRIDE/CVSS analysis, proving that the cost of the mitigation is proportionate to the potential financial impact of the risk.

#### Phase 4: External Standard Assessment (Targeting TC16 Pass)
Evaluate the organization's IT infrastructure, systems, and policies against an external, market-recognized standard.
*   **Action:** Conduct a cyber-risk assessment using the NIST Cybersecurity Framework or ISO/IEC 27001.
*   **Execution:** 
    *   Assess the risks associated with the assets and data identified during your information gathering.
    *   Identify the existing controls currently in place and evaluate their effectiveness (or failure) in stopping the anomalies detected in Deliverable A.
    *   Identify the gaps in the organization's security posture and provide formal recommendations mapped to the chosen standard (e.g., mapping a recommendation to NIST CSF's "Detect" or "Respond" functions).

#### Phase 5: Evidence & Artifact Collection
*   **Action:** Compile the generated documents to prove your competency in risk management and external standard auditing.
*   **Collection Requirements:**
    1.  **Baseline Risk Register:** A spreadsheet showing identified vulnerabilities, likelihood, impact, and prioritization.
    2.  **Comparative Modelling Document:** The written comparison of STRIDE versus CVSS, specifically detailing how they differently affect subsequent risk analysis.
    3.  **Business Case & Trade-off Analysis:** The document outlining the investment options for mitigation measures, demonstrating commercial judgement.
    4.  **External Standard Gap Analysis:** The formal assessment identifying existing control effectiveness and security posture gaps mapped against NIST CSF or ISO 27001.
