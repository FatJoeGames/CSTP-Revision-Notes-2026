# Written Report & Assessment Breakdown

### Part A: Technical Execution ("What I Did")
* **Word Count:** Unlimited (Not assessed on length, but on comprehensive evidence).
* **Execution Strategy & Breakdown:** 
  * This section serves as your forensic and operational runbook. It must sequentially prove every action taken during the coding and debugging phases.
  * **Debugging Evidence:** Embed terminal screenshots of GDB and Valgrind successfully resolving bugs in your serial program, followed by GUI screenshots of Intel Inspector or ITAC fixing your parallel program (TC6 Pass).
  * **Code & Assembly Mapping:** Display your high-level C/C++ code alongside the generated low-level executable assembly code. Follow this with the source code of a simple solution implemented directly in an assembler language to definitively meet the TC6 Pass criteria.
  * **Static & Dynamic Analysis:** Provide the raw output from compiler flags (e.g., `-Wall`, `-Werror`) and static code checkers used early in the coding stage to identify bugs. 

### Part B: Reflective & Justification Analysis ("Why I Did It")
* **Word Count:** Target 1,000 ± 100 words.
* **Sectional Allocation & Strategy:**
  
  * **Section 1: Defensive Programming & Algorithms (~250 words)**
    * Differentiate defensive programming from normal programming, focusing on high availability, safety, and security. 
    * Provide your specific use case for defensive programming and justify why it is essential, while also critically analyzing its downsides (e.g., performance overhead). 
    * Explain the benefits and limitations of strongly typed languages in this context (TKU6, TC7).
  
  * **Section 2: Security Principles & Vulnerability Mitigation (Distinction Focus) (~300 words)**
    * *Crucial for TC10 & TKU10 Distinction:* Do not just list common bugs. Identify *subtle* vulnerabilities in the software codebase examples and develop explicit mitigations for them.
    * Illustrate how you applied secure programming rules (naming objects, prohibiting certain constructions). 
    * Explain your use of guard clauses and assertions with suitable examples, demonstrating how they resist malware techniques like memory corruption and privilege escalation (TKU10).
  
  * **Section 3: System Engineering & SDLC (~250 words)**
    * Justify your choice of software development process (e.g., iterative/agile vs. sequential) based on the context of your application. 
    * Explain the principles of systems engineering, covering technology, people, culture, and process. 
    * Describe the benefits of a systems approach when dealing with challenges arising from complexity, emergence, adaptation, and co-evolution (TC11, TKU11 Pass).
  
  * **Section 4: Attack Surfaces & External Dependencies (~200 words)**
    * Differentiate defensive programming from offensive programming.
    * Describe how you determined the possible attack surfaces in your software and why you must write code assuming it will be attacked and that everything can fail.
    * Explain why external dependencies are crucial to software security and how you prevented security threats arising from them. 
    * Describe at least one formal method (e.g., CSP) and evaluate its strengths and weaknesses when developing software with security properties (TKU10).

---

## 4. Document Audit & Supplemental Requirements

To fully satisfy the explicit and implicit requirements of this scenario and support your written justification, ensure the following distinct documents and artifacts are generated, clearly labeled, and referenced within your Part A/B submission:

1. **Debugging & Compilation Logs:** The raw terminal outputs from Valgrind, GDB, ITAC/Intel Inspector, and compiler warning (`-Wall`) resolutions demonstrating early bug detection.
2. **Assembly Mapping Document:** The high-level script (C/C++) mapped side-by-side to its low-level executable assembly code, plus the standalone assembler script.
3. **Refactored Codebase (Guard Clauses & Assertions):** The final, hardened codebase explicitly demonstrating the application of secure design patterns, guard clauses, and assertions.
4. **Vulnerability Mitigation Report (Distinction Criteria):** A dedicated document analyzing the subtle vulnerabilities found in the code and detailing the precise mitigations developed to fix them.
5. **Attack Surface & Dependency Audit:** The threat model outlining the software's attack surfaces, paired with the output from an external dependency vulnerability scanner (e.g., OWASP Dependency-Check).
