### Deliverable A: Write, Test, & Debug Programs

**The Goal:** Write, test, and debug programs across high-level languages, low-level languages, and scripts, demonstrating proficiency with dynamic debugging tools and early-stage bug prevention techniques.

**Required Tools:** GCC/G++ (C/C++ compiler), Python (Scripting), GDB, Valgrind, Intel Inspector (or ITAC), NASM (Assembler).

#### Phase 1: High-Level Implementation & Early Bug Prevention (Targeting TC6 & TKU6 Pass)
You must write a program in a high-level language that works to achieve a defined specification, utilizing a scripting language alongside it, and employing tools to catch bugs early.
*   **Action:** Write a C or C++ application (the high-level language) and a Python equivalent (the scripting language) to solve a specific problem.
*   **Execution (Compiler Flags):** Compile the C/C++ code using strict compiler flags (e.g., `gcc -Wall -Wextra -Werror -pedantic -g main.c -o app`). Explain how using these flags, alongside static code checkers like `cppcheck`, prevents bugs by identifying them in an early stage of coding.
*   **Analysis Explanation:** Briefly document the differences between static analysis (examining code without executing it) and dynamic analysis (evaluating code during runtime), and mention how peer-reviewing code contributes to bug prevention.

#### Phase 2: Serial Program Debugging (Targeting TC6 Pass)
You must demonstrate the debugging of a serial program using specific dynamic analysis tools.
*   **Action:** Intentionally inject memory management flaws (e.g., a memory leak or dangling pointer) and logical errors into your C/C++ serial program.
*   **Execution (Valgrind):** Run the compiled serial program through Valgrind (`valgrind --leak-check=full ./app`). Capture the output showing the exact line numbers where the memory leaks occur.
*   **Execution (GDB):** Load the program into the GNU Debugger (`gdb ./app`). Set breakpoints, step through the code execution line-by-line, inspect variable states, and locate the logical error to fix the serial program.

#### Phase 3: Parallel Program Debugging (Targeting TC6 Pass)
You must demonstrate the debugging of a parallel program using advanced tools designed for concurrent execution.
*   **Action:** Write a simple parallel program (e.g., using OpenMP or MPI in C++) that contains a deliberate concurrency bug, such as a race condition or a deadlock.
*   **Execution (Intel Inspector / ITAC):** Run the parallel program through Intel Inspector or the Intel Trace Analyzer and Collector (ITAC). 
*   **Resolution:** Use the GUI tools provided by Inspector/ITAC to visualize the thread execution, identify the exact location of the race condition/deadlock, and apply the necessary lock or synchronization mechanism to fix the parallel program.

#### Phase 4: Low-Level Assembly Mapping & Implementation (Targeting TC6 Pass)
You must prove your understanding of language translation by mapping high-level code to assembler and writing assembler code directly.
*   **Action 1 (Mapping):** Take a small, specific function from your C program. Compile it directly to its assembly equivalent using the `-S` flag (`gcc -S function.c`). Create a document that maps the high-level programming language expression line-by-line to its resulting low-level executable code.
*   **Action 2 (Direct Implementation):** Design and implement a simple solution directly in an assembler language. Write a basic standalone `.s` or `.asm` file (using NASM or AT&T syntax) that performs a simple task, such as adding two registers or printing a string, and compile it to an executable.

#### Phase 5: Evidence & Artifact Collection
*   **Action:** Compile the generated logs and source code to definitively prove your competency across Technical Competency 6.
*   **Collection Requirements:**
    1.  **Source Code:** The high-level C/C++ files, the Python script, and the assembler source file.
    2.  **Compilation & Static Analysis Logs:** Terminal screenshots showing the `-Wall` compiler warnings and `cppcheck` outputs being resolved.
    3.  **Serial Debugging Logs:** Screenshots of the Valgrind memory leak summary and the GDB interactive stepping session.
    4.  **Parallel Debugging Logs:** Screenshots of the Intel Inspector / ITAC GUI highlighting the identified race condition.
    5.  **Assembly Mapping Document:** The text document explicitly drawing a line between the C syntax and the generated assembly instructions.
