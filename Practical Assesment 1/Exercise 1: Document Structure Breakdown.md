# Written Report & Assessment Breakdown

### Part A: Technical Execution ("What I Did")
* **Word Count:** Unlimited.
* **Breakdown:** 
  * Treat this as a comprehensive runbook. Document the exact sequence of the Hyper-V and Packet Tracer builds.
  * Embed code snippets and CLI outputs directly alongside the narrative. 
  * Provide visual evidence that the system meets the "distributed network (more than 1 sub-net) with static and dynamic routes" requirement (TC2 Pass). 
  * Detail the step-by-step troubleshooting of network issues, as resolving "complex problems" secures the Distinction for TC2.

### Part B: Reflective & Justification Analysis ("Why I Did It")
* **Word Count:** Target 1,000 ± 100 words.
* **Sectional Allocation & Strategy:**
  * **System Architecture & Risk Justification (300 words):** Justify the network and system design using NIST SP 800-53 or NCSC CAF principles. Explain how the architecture successfully covers enterprise, network, and application layers to secure the Distinction in TC19.
  * **Network Design Alternatives (200 words):** Explicitly discuss alternative network designs (e.g., comparing a flat network vs. the chosen segmented DMZ approach) and explain why your choice was optimal. This specifically hits the Merit criteria for TC2.
  * **Security Control Evaluation (250 words):** Critically analyze how effectively your implemented controls (IDPS, TLS, UFW) mitigate the risks identified in your Risk Management Plan. Detail how the risk owner can have confidence in these mitigations (TC20 Pass).
  * **Assurance & Legal Compliance (250 words):** Propose additional security controls (e.g., 3rd party penetration testing) to mitigate residual weaknesses (TC20 Merit). Relate these proposed measures to a publicly available standard of cyber security assurance to secure the TC20 Distinction. Discuss how your Information Security Policy implements relevant data protection laws (e.g., GDPR) for the file upload system (TC26 Pass).

---

## Document Audit & Supplemental Requirements

To fully satisfy the explicit and implicit requirements of the scenario, ensure the following supplemental documents are created and referenced within Part A/B:

1. **Information Security Policy:** A formal document dictating password complexity, data backup rules, access control, and regulatory compliance (GDPR) for employee data.
2. **Risk Management Plan:** A formal risk matrix identifying threats (malware, SQLi, unauthorized access), evaluating impact/likelihood, and defining the mitigation strategy.
3. **Cryptographic Key Management Plan:** A documented procedure outlining the lifecycle, storage, and rotation of the TLS certificates used by the web application.
4. **Disaster Recovery (DR) & Business Continuity Plan:** A brief strategy document detailing backup procedures and recovery time objectives for the file upload server.
5. **Security Case Document:** A unified document that synthesizes the Risk Plan, Security Policy, and implemented controls into a justified argument proving the system is secure.
