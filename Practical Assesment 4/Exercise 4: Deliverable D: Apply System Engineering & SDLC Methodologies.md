### Deliverable D: Apply System Engineering & SDLC Methodologies

**The Goal:** Assess the security of your software application from a macro level by determining attack surfaces, assuming failure, and managing the risks of external dependencies.

**Required Tools:** Threat Modeling Tool (e.g., Microsoft Threat Modeling Tool), Software Composition Analysis (SCA) Tool (e.g., OWASP Dependency-Check).

#### Phase 1: Offensive vs. Defensive Methodologies (Targeting TC11 Pass)
*   **Action:** Differentiate the mindsets required for systems engineering.
*   **Execution:** Explain the difference between defensive programming (building resilient structures to prevent breaches) with offensive programming (exploiting structures to identify weaknesses like a red team).

#### Phase 2: Attack Surface Determination (Targeting TC11 Pass)
*   **Action:** Create a system description and threat model.
*   **Execution:** Show and describe how you would determine possible attack surfaces in your software (e.g., mapping all API endpoints, user input fields, and database connections). Ensure this system description includes aspects of people, culture, technology, and process in your defined environment.

#### Phase 3: Security Policies & Zero-Trust Coding (Targeting TC11 Pass & TKU11)
*   **Action:** Establish overarching security policies.
*   **Execution:** Show and describe what necessary security rules or policies you will apply in your defensive coding. Critically explain why you should write your code as if it will be attacked and everything can fail (emulating Zero-Trust and Defense-in-Depth principles).

#### Phase 4: External Dependency Management (Targeting TC11 Pass)
Modern software relies heavily on third-party code, representing a massive supply-chain risk.
*   **Action:** Audit your software's dependencies.
*   **Execution:** Explain why external dependencies are so crucial to ensure the security of your software. Describe exactly how you would prevent security threats in your defensive coding due to external dependencies (e.g., running automated SCA scans, pinning version numbers, and mirroring repositories). 

#### Phase 5: Evidence & Artifact Collection
*   **Collection Requirements:**
    1.  **System Description & Attack Surface Map:** The diagram or documented list identifying where the software is exposed.
    2.  **Dependency Audit Log:** The output from an SCA tool proving you checked external dependencies for vulnerabilities.
    3.  **Policy Document:** The written text detailing the security rules, the differentiation of offensive/defensive programming, and the justification for assuming failure.
