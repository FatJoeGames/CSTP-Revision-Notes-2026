### Deliverable C: Apply Secure Programming Principles & Design Patterns

**The Goal:** Ensure the safety of a software application by establishing strict programming rules, leveraging guard clauses and assertions, and mitigating subtle vulnerabilities to achieve Distinction-level grades[cite: 3].

**Required Tools:** Strongly typed programming language (e.g., C++, Java, Rust).

#### Phase 1: Language Safety & Typing (Targeting TKU10 Pass)
Evaluate the safety of the software application starting at the language level[cite: 3].
*   **Action:** Document the fundamental traits of strongly typed languages.
*   **Execution:** Explain what strongly typed languages are, and critically explain their benefits (e.g., preventing type-juggling attacks at compile-time) and limitations (e.g., reduced flexibility, casting errors) in defensive programming[cite: 3].

#### Phase 2: Establishing Programming Rules (Targeting TC10 Pass)
Since most programming languages are not perfect for defensive programming, you must artificially enforce safety[cite: 3].
*   **Action:** Define and illustrate the necessary protections or programming rules you will apply in your defensive coding[cite: 3].
*   **Execution:** Use suitable programming examples to illustrate the application of:
    *   **Rules for naming objects:** (e.g., Hungarian notation or strict verb-noun casing to prevent logic confusion)[cite: 3].
    *   **Rules for prohibiting certain constructions:** (e.g., globally banning the use of `goto` or unsafe functions like `strcpy`)[cite: 3].
    *   **Rules exported by reused/pre-existing elements:** (e.g., strictly validating the return types of legacy libraries)[cite: 3].
    *   **Rules exported by execution platform:** (e.g., accounting for OS-level memory limits or endianness)[cite: 3].

#### Phase 3: Guard Clauses & Assertions (Targeting TC10 Pass)
*   **Action:** Refactor your codebase to heavily utilize specific defensive design patterns.
*   **Execution:** Explain what guard clauses and assertions are[cite: 3]. Provide a suitable example in your code: use **guard clauses** at the top of a function to immediately reject invalid input (failing fast), and use **assertions** to check for states during execution that should be mathematically or logically impossible[cite: 3].

#### Phase 4: Subtle Vulnerability Mitigation (Targeting TC10 Merit & Distinction)
To secure top marks, you must move beyond basic errors (like typos) and tackle complex software flaws[cite: 3].
*   **Action:** Review your codebase examples to identify more subtle vulnerabilities (e.g., integer overflows, race conditions, or cryptographic timing attacks)[cite: 3].
*   **Execution:** Develop specific, code-level mitigations to these vulnerabilities and document the before-and-after states to produce more resilient code, with evidence[cite: 3]. 

#### Phase 5: Evidence & Artifact Collection
*   **Collection Requirements:**
    1.  **Code Examples:** Snippets illustrating the programming rules, guard clauses, and assertions[cite: 3].
    2.  **Vulnerability Report (Distinction):** The specific breakdown identifying the subtle vulnerabilities and the exact code refactoring used to develop mitigations[cite: 3].
    3.  **Language Evaluation Text:** The written analysis of strongly typed languages[cite: 3].
