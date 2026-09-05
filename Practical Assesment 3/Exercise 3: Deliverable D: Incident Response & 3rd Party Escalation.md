### Deliverable D: Incident Response & 3rd Party Escalation

**The Goal:** Manage intrusion response, develop a comprehensive incident response plan, establish communication protocols, and define explicit criteria for escalating incidents to third parties. 

**Required Tools:** Word Processor.

*Note: Technical Competency 22, Technical Competency 23, and Technical Knowledge & Understanding 22 all feature "Pass" criteria in the marking scheme. The focus here is on methodological correlation of evidence, structured incident handling, and clear communication boundaries.*

#### Phase 1: Security Monitoring, Correlation & Impact (Targeting TC22 & TKU22 Pass)
Before you can respond to an incident, you must formally declare that a breach has occurred based on verifiable evidence.
*   **Action:** Write a brief Anomaly Correlation Report based on the findings from Deliverable A.
*   **Execution:** 
    *   Explicitly state how you integrated and correlated information from various sources (e.g., Wireshark network logs, hypothetical physical security logs, and SIEM alerts) and compared it to known threat data to form a reasoned judgment that a network security breach occurred.
    *   Characterize the anomaly in terms of its potential impact on the organization (e.g., "The outbound 50GB transfer on Port 443 represents a severe data exfiltration event, threatening customer PII").
    *   Demonstrate your understanding (TKU22) of how attack techniques manifest in network monitoring tools and explain how you diagnosed the cause from these observables.

#### Phase 2: Incident Response Plan Development (Targeting TC23 Pass)
You must develop an incident response plan that covers the full lifecycle of a cybersecurity incident.
*   **Action:** Draft the Incident Response Plan document.
*   **Execution:** 
    *   Structure the plan with explicit procedures for detecting, analyzing, containing, eradicating, and recovering from cybersecurity incidents.
    *   **Roles & Responsibilities:** Identify the specific roles of your team members (e.g., Incident Commander, Network Analyst, Communications Lead) and establish an internal communication protocol for reporting and responding.
    *   **Local Response:** Include a specific procedural track for managing local response to *non-major* incidents (e.g., a single isolated malware infection) in accordance with defined procedures, proving you know how to handle lower-tier events without over-escalating.

#### Phase 3: 3rd Party Escalation & Interaction (Targeting TC23 Pass)
You must define the exact boundaries of your internal team's capabilities and establish when external help is required.
*   **Action:** Develop a 3rd Party Escalation Matrix within your IR Plan.
*   **Execution:** 
    *   Define explicit criteria for escalating incidents to 3rd parties (e.g., "If data exfiltration involves payment card information, escalate to external PCI forensic investigators within 24 hours").
    *   Establish specific communication channels with third parties such as law enforcement agencies (e.g., Action Fraud / NCSC in the UK), security vendors, and other stakeholders. 
    *   Document how your team will interact and communicate effectively with the external incident response teams or customers during a live event.

#### Phase 4: Evidence & Artifact Collection
*   **Action:** Compile the generated documents to prove your competency in security monitoring correlation and intrusion response management.
*   **Collection Requirements:**
    1.  **Anomaly Correlation & Impact Report:** A brief document pulling together the Wireshark/SQL/Python evidence from Deliverable A to formally declare a breach and assess its impact.
    2.  **Incident Response Plan (IRP):** The comprehensive document detailing the containment, eradication, and recovery phases, along with team member roles.
    3.  **3rd Party Escalation Matrix:** The specific criteria and communication channels established for interacting with law enforcement, security vendors, and stakeholders.
