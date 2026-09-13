# Exercise 3: Deliverable B: Risk Modelling & External Standard Assessment
**Target Competencies:** TC15, TKU15 (Distinction Focus), TC16, TKU16, TC17, TKU17
**Grading Target:** Distinction

---

## 1. Dual Risk Modelling & Commercial Investment Case (TC15, TKU15) [DISTINCTION FOCUS]
*Goal: Model system risks using two distinct methodologies, critically compare their analytical impacts, and build a formal enterprise business case with costed investment options.*

### 1.1 Architectural Model & Methodological Application
*   **System Architectural Model:** Compose an architectural model of the target system integrated within the broader enterprise model for the purpose of risk assessment.
*   **Technique 1 (Quantitative Focus): CVSS Scoring Framework**
    *   Apply CVSS scoring (Base, Temporal, and Environmental metrics) to technical vulnerabilities identified within the architecture.
    *   Evaluate attack vector, complexity, privileges required, user interaction, scope, and CIA impact metrics to produce standardized numerical risk scores.
*   **Technique 2 (Qualitative Focus): STRIDE Threat Modelling**
    *   Apply the STRIDE methodology across system trust boundaries:
        *   *Spoofing:* Identity theft and authentication bypass.
        *   *Tampering:* Unauthorized data or binary modification.
        *   *Repudiation:* Inability to trace actions to specific actors.
        *   *Information Disclosure:* Exposure of sensitive data or PII.
        *   *Denial of Service:* Resource exhaustion and service interruption.
        *   *Elevation of Privilege:* Unauthorized gain of administrative rights.

### 1.2 Comparative Analysis & Effect on Risk Analysis (Merit Criteria)
*   **Comparative Evaluation:** Compare and contrast the CVSS scoring framework with the STRIDE threat modelling methodology.
*   **Analytical Impact:** Explicitly evaluate how choosing one technique over the other affects the subsequent risk analysis:
    *   *CVSS Impact:* Focuses strictly on known software vulnerabilities and technical severity; however, it lacks contextual awareness of business processes, threat actor motivations, and systemic architectural design flaws.
    *   *STRIDE Impact:* Uncovers architectural design flaws, trust boundary violations, and business process weaknesses early in system design; however, it lacks standardized numerical prioritization and does not measure temporal exploit availability.
    *   *Synthesis:* Demonstrate how combining both techniques creates an enriched risk perspective—STRIDE identifies *where* threats exist across architectural boundaries, while CVSS quantifies *how severe* individual technical entry points are.

### 1.3 Enterprise Business Case & Investment Options (Distinction Criteria)
*   **Risk Economics & Asset Valuation:** Detail asset valuation concepts, balancing organizational *Risk Appetite* (the level of risk House Tech is willing to accept) against *Risk Tolerance* (the threshold of unmitigated risk before operations are impaired).
*   **Business Risk Alignment:** Relate technical cyber risks directly to wider business and operational risks (e.g., supply chain disruption in distribution centres, store retail downtime, regulatory fines, and brand damage).
*   **Cost Analysis & Trade-Off Arguments:** Present trade-off arguments in a formal business case, demonstrating commercial and value-for-money judgment.
*   **Identified Mitigation Investment Options:** Based on the dual STRIDE/CVSS analysis, define explicit options for business investment:
    *   *Option A (Technical Patching & Vulnerability Management):* Low capital expenditure (CapEx); mitigates high CVSS technical vulnerabilities but leaves architectural STRIDE risks (e.g., identity spoofing) unaddressed.
    *   *Option B (Architectural Redesign & IDAM Integration):* Higher CapEx; addresses fundamental STRIDE design flaws by implementing Zero Trust micro-segmentation and centralized MFA/SSO, lowering long-term operational expenditure (OpEx) and residual risk.
    *   *Option C (Risk Transfer & Managed SIEM/SOC):* Balanced CapEx/OpEx; transfers monitoring overhead to a third-party SOC, providing continuous threat detection aligned with enterprise SLA targets.

---

## 2. Cyber Risk Assessment to External Standard (TC16, TKU16)
*Goal: Conduct an independent cyber-risk assessment aligned with ISO 27001 / ISO 27005.*

### 2.1 ISO 27001 / ISO 27005 Assessment Methodology
*   **Risk Assessment Execution:** Conduct a formal security risk assessment for the target system without direct supervision using a recognized risk assessment methodology (e.g., ISO 27005 / ISO 27001).
*   **Qualitative & Quantitative Measurement:** Define risks using qualitative descriptors (High/Medium/Low likelihood and impact) combined with quantitative metrics (Single Loss Expectancy [SLE] and Annualized Loss Expectancy [ALE]).
*   **Remediation Advice:** Formulate prioritized remediation advice tailored to the operational context of the employer/business.

### 2.2 Stakeholder Roles & Governance
*   **Risk Owner Definition:** Define the explicit role of the *Risk Owner* (e.g., CISO or Business Unit Director)—the individual accountable for accepting, treating, or transferring risk.
*   **Stakeholder Distinction:** Contrast the Risk Owner role with other organizational stakeholders (e.g., System Administrators who act as *Risk Custodians*, Data Protection Officers who enforce compliance, and end-users who execute operational tasks).

### 2.3 Risk Treatment Strategies
*   Detail the four recognized options for treating identified risks:
    1.  *Mitigate (Modify):* Applying technical or procedural controls to reduce likelihood/impact.
    2.  *Transfer (Share):* Offloading financial risk via cyber insurance or third-party service contracts.
    3.  *Accept (Retain):* Formally documenting acceptance of residual risk within risk appetite limits.
    4.  *Avoid (Eliminate):* Terminating the vulnerable business process or system component entirely.

---

## 3. Information Security Management Plan (ISMP) & Governance (TC17, TKU17)
*Goal: Develop an ISMP aligned with ISO 27001 and establish governance structures.*

### 3.1 ISO 27001 Aligned Security Management Plan
*   **ISMP Development:** Develop an Information Security Management Plan (ISMP) for a defined business area (e.g., E-Commerce & Retail Operations) in accordance with ISO 27001.
*   **Organizational Policies:** Identify and align the plan with organizational security policies, processes, Service Level Agreements (SLAs), and operational performance targets.

### 3.2 Governance, Organizational Structure & Access Rights
*   **Governance Framework:** Explain the necessity of governance, organizational structures, defined roles, policies, standards, and guidelines working together to achieve secure outcomes.
*   **IDAM Integration:** Explain how security policies are actively enforced through Identity and Access Management (IDAM) and provisioning:
    *   Detail implementation for databases (Role-Based Access Control - RBAC).
    *   Detail implementation for applications (Least Privilege & MFA).
    *   Detail implementation for physical access control systems (Badge/Biometric restrictions).

### 3.3 Third-Party Security & Industry Experts
*   **External Experts:** Explain the role of industry experts, how they are recognized, and their operational contributions.
*   **Operational Engagement:** Detail how an organization effectively utilizes:
    *   *Computer Emergency Response Teams (CERTs):* For immediate threat intelligence and national advisory feeds.
    *   *OSINT Providers:* For continuous external attack surface management and brand monitoring.
    *   *Incident Response Providers:* For retainer-based third-party forensic escalation during major security events.
