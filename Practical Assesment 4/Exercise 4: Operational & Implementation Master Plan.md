# Exercise 4: Defensive Programming - Operational & Implementation Master Plan

## 1. Operational Plan Document

**Assessment Strategy:** 
The objective of this 12-hour practical test is to implement defensive programming techniques, write and debug code across high and low-level languages, and apply secure design patterns[cite: 2, 6]. Execution will focus on demonstrating proficiency with debugging tools (GDB, Valgrind, Intel Inspector) and static/dynamic analysis[cite: 6]. To secure Distinction grades (TC10, TKU10), the implementation and written justification must move beyond basic secure coding to identify subtle vulnerabilities in a codebase and actively develop complex mitigations for them[cite: 6].

**KSB Competency Mapping Table:**

| KSB Code | KSB Description | Practical Task Alignment |
| :--- | :--- | :--- |
| **TC6** | Write, test and debug programmes in high/low languages. | Debugging serial (GDB/Valgrind) and parallel (ITAC) programs; mapping high-level code to assembler[cite: 6]. |
| **TC7** | Design, implement and analyse algorithms. | Analyzing defensive programming vs normal programming; documenting guard clauses and assertions[cite: 6]. |
| **TC10** | Apply secure programming principles & design patterns. | Applying organizational coding standards, mitigating subtle vulnerabilities to produce resilient code[cite: 6]. |
| **TC11** | Apply system engineering principles and SDLC models. | Creating a complex system description; determining attack surfaces; managing external dependencies[cite: 6]. |
| **TKU6** | Algorithm and programme design, concepts, compilers. | Demonstrating language translation, syntax analysis, compiler semantic analysis, and assembler coding[cite: 6]. |
| **TKU10** | Defensive programming, malware resistance, code analysis. | Applying static/dynamic analysis; mitigating vulnerabilities (Distinction); using compiler features[cite: 6]. |
| **TKU11** | System development principles, tools, approaches. | Justifying iterative/agile approaches; dealing with complexity, emergence, and SDLC trade-offs[cite: 6]. |

**Hour-by-Hour Implementation Guide:**

| Hour | Action Step | Target KSBs | Output Deliverable |
| :--- | :--- | :--- | :--- |
| **1-2** | Write high-level (C/C++) and script (Python) solutions; apply compiler flags[cite: 6]. | TC6, TKU6 | Baseline source code and compilation logs[cite: 6]. |
| **3-4** | Debug serial programs (GDB/Valgrind) and parallel programs (Intel Inspector)[cite: 6]. | TC6, TKU10 | Debugging logs and memory leak reports[cite: 6]. |
| **5** | Map high-level code to low-level assembly; write simple assembler solution[cite: 6]. | TC6, TKU6 | Assembly `.s` files and mapping documentation[cite: 6]. |
| **6-7** | Refactor algorithms using defensive design (guard clauses, assertions)[cite: 6]. | TC7, TC10 | Hardened codebase[cite: 6]. |
| **8** | Identify subtle vulnerabilities and develop mitigations (Distinction focus)[cite: 6]. | TC10, TKU10 | Vulnerability assessment and patched code[cite: 6]. |
| **9** | Document attack surfaces and external dependency security rules[cite: 6]. | TC11, TKU11 | Attack Surface Model & Dependency check logs[cite: 6]. |
| **10-11** | Draft justifications for SDLC choices, agile vs sequential, formal methods[cite: 6]. | TKU10, TKU11 | Part B framework and SDLC justification[cite: 6]. |
| **12** | Documentation: Collate code snippets, logs, and finalize Part A & Part B[cite: 2, 6]. | TC10, TKU10 | Completed 1000-word written justification[cite: 2, 6]. |

---

## 2. Deliverable Execution Plans

### Deliverable A: Write, Test, & Debug Programs
* **Overview & Goal:** Demonstrate proficiency in writing, testing, and debugging programs in high-level languages, scripting languages, and assembler, utilizing static/dynamic analysis and compiler flags[cite: 6].
* **Tools & Software Required:** GCC/G++, Python, GDB, Valgrind, Intel Inspector (or ITAC), NASM (for Assembler).
* **Technical Step-by-Step Breakdown:**
  1. Write a flawed serial program in C/C++ (e.g., containing a memory leak or buffer overflow). Use compiler flags (`-Wall -Wextra -Werror -pedantic`) and static code checkers (e.g., `cppcheck`) to identify bugs early[cite: 6].
  2. Use Valgrind to perform dynamic analysis and locate memory leaks; use GDB to step through the execution and fix the logic[cite: 6].
  3. Write a flawed parallel program (e.g., OpenMP or MPI with a race condition). Use Intel Inspector or ITAC to debug and fix the parallel program[cite: 6].
  4. Map a high-level C function to its low-level executable code (assembly) using `gcc -S`[cite: 6].
  5. Design and implement a simple solution directly in an assembler language (e.g., x86 NASM)[cite: 6].
* **Evidence & Artifact Collection:** Source code (flawed and fixed), screenshots of Valgrind/GDB terminal sessions, Intel Inspector GUI output, assembly language source files, and a scripting language (Python) implementation of the same logic[cite: 6].

---

### Deliverable B: Design, Implement, and Analyse Algorithms
* **Overview & Goal:** Showcase critical analysis of defensive programming, distinguishing it from normal programming based on high availability, safety, and security[cite: 6].
* **Tools & Software Required:** IDE, Markdown/Word Processor.
* **Technical Step-by-Step Breakdown:**
  1. Define a specific use case (e.g., a financial transaction algorithm or medical device software) where defensive programming is essential[cite: 6].
  2. Refactor the algorithm developed in Deliverable A to utilize good coding styles, documentation strategies (e.g., Doxygen/Sphinx), and comprehensive testing techniques (e.g., Unit Testing with PyTest or Google Test)[cite: 6].
  3. Formulate a written critical analysis explaining the downsides of defensive programming (e.g., performance overhead, increased code complexity, longer development lifecycles)[cite: 6].
* **Evidence & Artifact Collection:** Refactored algorithm source code, Unit Test execution logs, and the critical analysis text for inclusion in Part B[cite: 6].

---

### Deliverable C: Apply Secure Programming Principles & Design Patterns
* **Overview & Goal:** Ensure the safety of a software application by applying secure programming principles, utilizing guard clauses and assertions, and establishing strict programming rules[cite: 6].
* **Tools & Software Required:** Strongly typed language compiler (e.g., Java, C#, or modern C++).
* **Technical Step-by-Step Breakdown:**
  1. Explain the benefits and limitations of strongly typed languages in the context of defensive programming[cite: 6].
  2. Establish necessary protections and programming rules (e.g., rules for naming objects, prohibiting certain constructions like `goto` or unbounded string copies, rules exported by execution platforms)[cite: 6].
  3. Illustrate the application of these rules by writing code that heavily utilizes **guard clauses** (early returns on invalid input) and **assertions** (runtime checks for impossible states)[cite: 6].
  4. **Distinction Focus:** Identify subtle vulnerabilities in the initial codebase (e.g., integer overflows leading to logic bypasses) and develop advanced mitigations for them[cite: 6].
* **Evidence & Artifact Collection:** Code snippets highlighting guard clauses and assertions, documentation of the applied programming rules, and a before/after comparison of the mitigated subtle vulnerability[cite: 6].

---

### Deliverable D: Apply System Engineering & SDLC Methodologies
* **Overview & Goal:** Evaluate the software application's security from a systems engineering perspective, determining attack surfaces, managing external dependencies, and assuming an environment where everything can fail[cite: 6].
* **Tools & Software Required:** OWASP Dependency-Check (or similar tool), Threat Modeling Software/Diagramming.
* **Technical Step-by-Step Breakdown:**
  1. Differentiate defensive programming from offensive programming[cite: 6].
  2. Create a system description and determine possible attack surfaces within the software (e.g., user inputs, API endpoints, file parsing)[cite: 6].
  3. Define the necessary security rules and policies to apply in defensive coding, justifying why code must be written assuming it will be attacked and that everything can fail (Defense in Depth)[cite: 6].
  4. Run a dependency checker (e.g., `pip-audit` or OWASP Dependency-Check) to demonstrate how external dependencies introduce security threats, and detail mitigation strategies (e.g., pinning versions, using private registries)[cite: 6].
* **Evidence & Artifact Collection:** Attack surface diagram/document, external dependency audit logs, and the documented security policies[cite: 6].
