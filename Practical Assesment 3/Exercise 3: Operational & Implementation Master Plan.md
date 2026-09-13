# Exercise 3: Operational & Implementation Master Plan
**Objective:** Operational roadmap for executing the technical analysis, threat intelligence profiling, risk modelling, and governance implementation for Practical Assessment 3.

---

## Phase 1: Data Analytics, SIEM & Data Architecture Setup (TC3, TKU3, TC22, TKU22)
*Focus: Capturing traffic, querying database structures, and executing correlation analytics.*

### 1.1 Technical Execution
1.  **Traffic Capture & Anomaly Identification:**
    *   Inspect network packet data structures (PCAPs) and protocol behaviours to identify network anomalies.
    *   Characterise identified anomalies by evaluating their operational and business impact on enterprise systems.
2.  **Database Design & SQL Querying:**
    *   Design and deploy a relational database structure to store relevant security information.
    *   Execute a declarative query language (e.g., SQL `SELECT`, `JOIN`, `GROUP BY`) to elicit actionable threat analytics from the database.
    *   Apply **Graph theory** concepts to map information management and relationships.
3.  **Big Data & Hadoop Evaluation:**
    *   Analyse the benefits, limitations, and vulnerabilities of 'big data' approaches and architectures.
    *   Specifically detail components employed in systems for big data, such as a **Hadoop cluster**.
4.  **SIEM & Multi-Source Correlation:**
    *   Correlate logs across heterogeneous sources: network monitoring tools, SIEM alerts, access control systems, and **physical security systems**.
    *   Compare correlated data against known threat and vulnerability data to validate breach judgements based on evidence.
    *   Document the relative merits of:
        *   Manual log inspection vs. automated techniques.
        *   Signature-based anomaly detection vs. algorithmic anomaly detection.

---

## Phase 2: OSINT Intelligence Gathering & Source Evaluation (TC14, TKU14)
*Focus: Profiling the target, evaluating contradictory intelligence, and establishing provenance.*

### 2.1 Intelligence Gathering Workflow
1.  **Target Profiling:** Conduct legal and ethical Open-source Intelligence (OSINT) reconnaissance to profile the defined target organisation/system and identify potential vulnerabilities.
2.  **Attacker Reconnaissance Mapping:** Detail how external threat actors build target knowledge using:
    *   Phishing.
    *   Exploiting an insider.
    *   Port scanning.
    *   Open-source intelligence.
3.  **Evaluating Provenance & Contradictory Feeds:**
    *   Analyse multiple, **potentially contradictory** sources of information to identify patterns.
    *   Critically consider the *provenance* of these sources and document how this affects the quality of the evidence, arguments, and conclusions.
    *   Formulate a reasoned, evidence-backed hypothesis detailing likely threat actor actions.

---

## Phase 3: System Risk Modelling & Business Investment Case (TC15, TKU15) [DISTINCTION FOCUS]
*Focus: Performing dual-framework risk modelling, comparing analytical impacts, and building a commercial business case.*

### 3.1 Dual-Model Technical Execution
1.  **Architectural Composition:** Compose a system architectural model integrated into an enterprise model for the purpose of risk assessment.
2.  **Model 1 (CVSS Scoring):** Apply CVSS scoring to quantitatively model risks, vulnerabilities, and impacts.
3.  **Model 2 (STRIDE Threat Modelling):** Map qualitative threats across system trust boundaries using the STRIDE framework.

### 3.2 Comparative Analysis & Commercial Investment Case
1.  **Methodology Comparison (Merit Requirement):**
    *   Compare and contrast the two system modelling techniques (CVSS scoring vs. STRIDE).
    *   Analyse the differences between the two techniques in terms of their effect on any subsequent risk analysis.
2.  **Business Investment Options (Distinction Requirement):**
    *   Relate cyber risk to other relevant classes of risk (business and operational risks).
    *   Incorporate risk economics: balance risk appetite and risk tolerance concepts alongside asset valuation.
    *   Perform a cost analysis and present trade-off arguments in a business case, illustrating commercial or value for money judgement.
    *   Ensure options are identified for investment in measures to mitigate cyber risk based on the dual-modelling analysis.

---

## Phase 4: ISO 27001 Risk Assessment & ISMP Deployment (TC16, TKU16, TC17, TKU17)
*Focus: Executing an external standard risk assessment and formulating an ISMP.*

### 4.1 Assessment & Governance Workflow
1.  **External Standard Risk Assessment:**
    *   Conduct a cyber-risk assessment against an externally recognised standard (e.g., ISO 27001) using a recognised methodology.
    *   Describe risks in qualitative and quantitative terms.
    *   Understand the role of the **risk owner** and contrast that role with other stakeholders.
    *   Apply the different ways of treating risk: mitigate, transfer, accept, etc..
2.  **Information Security Management Plan (ISMP):**
    *   Develop an ISMP for a defined business area in accordance with ISO 27001.
    *   Ensure operations align with service level agreements (SLAs) or employer defined performance targets.
    *   Explain how security policies are supported by provisioning and access rights (IDAM) for:
        *   A database.
        *   An application.
        *   A physical access control system.
3.  **Third-Party Integration:** Detail operational workflows for effectively using external organisations: a CERT, an OSINT provider, and an incident response provider.

---

## Phase 5: Incident Response & Escalation Management (TC23, TKU23)
*Focus: Executing non-major incident management, advising teams, and managing communications.*

### 5.1 Incident Management Lifecycle
1.  **Local Response Execution:** Manage the local response to a non-major incident in accordance with a defined procedure.
2.  **Advising Teams:** Advise others on cyber incident response processes, incident management processes, and evidence collection/preservation requirements to support incident investigation.
3.  **Communication Matrix:**
    *   *Internal:* Interact and communicate effectively with the incident response team/process.
    *   *External:* Communicate effectively with the customer or other external authority incident response team/process for incidents.

---

## 6. KSB Evidence Mapping Table (Exercise 3)
*Use this table during the write-up to ensure every competency is explicitly tagged in your final report submission.*

| KSB Code | KSB Description | Practical Alignment / Required Evidence | Status |
| :--- | :--- | :--- | :--- |
| **TC3 / TKU3** | Big Data, Statistics & Database Concepts | Execute a declarative query language, analyse Hadoop architecture/graph theory, and apply statistical techniques to large data sets. | [ ] |
| **TC14 / TKU14** | Ethical OSINT & Intelligence Analysis | Profile target via OSINT, consider provenance of contradictory sources, and hypothesise a likely picture based on evidence. | [ ] |
| **TC15 / TKU15** | Risk Modelling & Business Trades *(Distinction)* | Compare two models (CVSS vs. STRIDE). Evaluate effect on risk analysis. Identify investment options based on cost analysis/trade-offs. | [ ] |
| **TC16 / TKU16** | Risk Assessment to External Standard | Conduct assessment to external standard. Use qualitative/quantitative terms. Define Risk Owner vs. other stakeholders. | [ ] |
| **TC17 / TKU17** | ISMS, Governance & External Standards | Develop an ISMP. Document IDAM for DB, App, and physical systems. Define use of CERTs, OSINT, and IR providers. | [ ] |
| **TC22 / TKU22** | SIEM, Anomaly & Intrusion Detection | Inspect PCAPs. Correlate SIEM, network, and physical security logs. Compare signature vs. algorithmic anomaly detection. | [ ] |
| **TC23 / TKU23** | Incident Response & Communication | Manage local non-major incident. Advise others on evidence preservation. Communicate with internal team, customers, and external authorities. | [ ] |

---

## 7. Hour-by-Hour Execution Schedule
*This schedule assumes a standard 7-hour assessment window (plus lunch). Adjust timestamps based on your actual start time.*

| Time Window | Operational Phase | Key Deliverables & Actions | Target KSBs |
| :--- | :--- | :--- | :--- |
| **09:00 - 10:30** | Phase 1: Data Analytics & SIEM | Extract PCAPs, execute SQL database queries, and correlate physical/network logs. Draft algorithmic vs. signature analysis. | TC3, TKU3, TC22, TKU22 |
| **10:30 - 11:30** | Phase 2: OSINT & Intelligence | Run ethical reconnaissance. Profile threat actor methods (phishing, insider, etc.). Document provenance of contradictory intelligence. | TC14, TKU14 |
| **11:30 - 13:00** | Phase 3: Dual Risk Modelling | **(Distinction Sprint)** Run STRIDE and CVSS models. Draft comparative analysis and identify costed investment mitigation options. | TC15, TKU15 |
| **13:00 - 13:30** | *Lunch Break* | *Step away from the screen. Hydrate and reset.* | - |
| **13:30 - 15:00** | Phase 4: ISO 27001 & ISMP | Execute formal risk assessment. Define Risk Owner. Document IDAM integration across DB/App/Physical. Detail CERT/IR use. | TC16, TKU16, TC17, TKU17 |
| **15:00 - 16:15** | Phase 5: Incident Response | Write up non-major incident procedure. Draft advisory notes on RAM/evidence preservation. Map internal/external communications. | TC23, TKU23 |
| **16:15 - 17:00** | Review & KSB Tagging | Cross-reference report against the KSB table. Ensure explicit headers match the grading matrix precisely. | All |
