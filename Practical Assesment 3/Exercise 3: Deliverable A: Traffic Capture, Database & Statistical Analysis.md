# Exercise 3: Deliverable A: Traffic Capture, Database & Statistical Analysis
**Target Competencies:** TC3, TKU3, TC22, TKU22
**Grading Target:** Pass (Maximum achievable for these specific competencies)

---

## 1. Network Monitoring, PCAP & Anomaly Detection (TC22, TKU22)
*Goal: Demonstrate the ability to inspect network data, recognize anomalies, and justify breach conclusions using evidence.*

### 1.1 Network Data & Protocol Inspection
*   **Packet Inspection:** Analyze observed network data structures (PCAPs) to identify anomalies. 
*   **Protocol Behavior:** Detail how specific attack techniques manifest in network monitoring tools and logging systems. *(Provide an example of how inspecting protocol behaviors—e.g., malformed HTTP headers or unexpected DNS tunneling—reveals the likely means of an attack.)*
*   **Impact Characterization:** Characterize the identified anomaly strictly in terms of its potential business and operational impact on the organization.

### 1.2 SIEM Integration & Multi-Source Correlation
*   **Data Correlation:** Integrate and correlate heterogeneous information from multiple distinct sources to form an evidence-based judgment of a network security breach.
*   **Required Log Sources:** Explicitly mention combining:
    *   Network monitoring tools / PCAPs.
    *   Secure Information and Event Management (SIEM) tools.
    *   Access control systems.
    *   **CRITICAL REQUIREMENT:** You must include *physical security systems* (e.g., CCTV logs, badge swipes) in your correlation to satisfy the standard.
*   **Threat Intelligence Comparison:** Compare the correlated log data against known threat and vulnerability data (e.g., MITRE ATT&CK, CVE databases) to justify your breach conclusion.

### 1.3 Detection Methodologies (The "Relative Merits" Requirement)
*   **Manual vs. Automated:** Discuss the relative merits of manual log analysis versus automated SIEM correlation. 
*   **Signature vs. Algorithmic:** Compare the relative merits of *signature-based* anomaly detection (matching known IOCs/hashes) versus *algorithmic* anomaly detection (machine learning baselines identifying deviations).

---

## 2. Database Design & Information Management (TC3, TKU3)
*Goal: Prove knowledge of database mechanics, query languages, and data structure theory.*

### 2.1 Database Architecture & DBMS Functions
*   **Database Setup:** Design and set up a database to hold relevant security information.
*   **Core Mechanics:** Explain the components of database systems and the design of core DBMS functions, specifically focusing on *query mechanisms* and *access methods*.
*   **Information Management Concepts:** Detail the concepts of information capture, representation, storage, and retrieval. Explain how data is searched, retrieved, linked, and navigated.

### 2.2 Declarative Query Language (SQL)
*   **Query Execution:** You must explicitly demonstrate using a declarative query language (e.g., SQL) to elicit specific information from your database. *(Draft out 2-3 complex SQL queries here, such as `SELECT` statements with `JOIN` or `GROUP BY` clauses, to show you are eliciting actionable security analytics).*

### 2.3 Graph Theory 
*   **Graph Theory Application:** Briefly explain how *Graph Theory* applies to information management and security analytics (e.g., using nodes and edges to map relationships between compromised IP addresses, user accounts, and physical badge swipes).

---

## 3. Big Data Concepts & Statistical Analytics (TC3, TKU3)
*Goal: Apply math and statistics to massive datasets and evaluate Big Data architecture vulnerabilities.*

### 3.1 Statistical Security Analytics
*   **Trend & Anomaly Determination:** Apply statistical techniques (e.g., standard deviation, mean baseline comparison, or time-series analysis) to large heterogeneous data sets to determine trends or anomalies in support of cyber security incident analysis. 
*   **Tooling:** Identify the tools and techniques used for analyzing these large heterogeneous data sets.

### 3.2 Big Data Architectures (Hadoop)
*   **Benefits & Limitations:** Analyze the core benefits and limitations of 'big data' approaches. 
*   **Architecture Components:** Describe the components and architectures employed in systems for big data. **CRITICAL:** You must explicitly mention and describe a *Hadoop cluster* (or equivalent distributed file system/MapReduce architecture).
*   **Vulnerability Identification:** Identify specific vulnerabilities inherent in big data architectures (e.g., lack of inherent encryption in Hadoop data nodes, or weak authentication mechanisms in distributed clusters).
