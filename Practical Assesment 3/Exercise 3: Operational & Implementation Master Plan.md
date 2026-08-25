# Exercise 3: Monitor - Operational & Implementation Master Plan

## 1. Operational Plan Document

**Assessment Strategy:** 
The objective of this 12-hour practical test is to implement comprehensive monitoring techniques, analyze large network traffic datasets for anomalies using statistical methods, and formalize risk management and incident response frameworks[cite: 5]. To secure Distinction grades, execution must explicitly compare and contrast two distinct risk modelling techniques (e.g., STRIDE vs. CVSS) to justify specific financial investments in security mitigations (TC15)[cite: 5]. The technical build requires setting up a database to house traffic logs and utilizing declarative query languages (SQL) to feed data into Python or R for advanced statistical visualization (TC3)[cite: 5].

**KSB Competency Mapping Table:**

| KSB Code | KSB Description | Practical Task Alignment |
| :--- | :--- | :--- |
| **TC3** | Apply statistical techniques to large data sets. | Capturing Wireshark PCAPs, loading into a SQL database, and using Python for clustering/outlier detection[cite: 5]. |
| **TC14** | Undertake ethical system reconnaissance/intel analysis. | Cleaning dataset errors, identifying anomalies, and considering source provenance in OSINT[cite: 5]. |
| **TC15** | Undertake risk modelling, analysis, and trades. | Comparing STRIDE vs. CVSS to justify mitigation investments in a business case[cite: 5]. |
| **TC16** | Undertake risk assessment to an external standard. | Auditing the discovered gaps against the ISO/IEC 27001 or NIST Cybersecurity Framework[cite: 5]. |
| **TC17** | Apply a management system and ISMS plan. | Drafting timelines, resources, and prioritized remediation plans under ISO 27001[cite: 5]. |
| **TC22** | Security monitoring, analysis & intrusion detection. | Correlating Wireshark/SIEM alerts to known threats to prove a network breach[cite: 5]. |
| **TC23** | Manage intrusion response, including with 3rd parties. | Defining IR roles and escalation criteria for CERTs and law enforcement[cite: 5]. |

**Hour-by-Hour Implementation Guide:**

| Hour | Action Step | Target KSBs | Output Deliverable |
| :--- | :--- | :--- | :--- |
| **1-2** | Capture live network traffic via Wireshark; export to CSV[cite: 5]. | TC3, TKU22 | Raw PCAP and CSV traffic datasets[cite: 5]. |
| **3-4** | Set up SQL database, import data, execute declarative queries[cite: 5]. | TC3, TKU3 | SQL Database and extracted query results[cite: 5]. |
| **5-6** | Python/R analysis: Clean data, run clustering algorithms, generate charts[cite: 5]. | TC3, TC14 | Data visualizations and anomaly report[cite: 5]. |
| **7-8** | Develop Risk Models: Compare STRIDE vs. CVSS and analyze trades[cite: 5]. | TC15, TKU15 | Comparative Risk Model Document[cite: 5]. |
| **9** | Perform Risk Assessment against ISO 27001 / NIST CSF[cite: 5]. | TC16, TKU16 | External Standard Audit Report[cite: 5]. |
| **10** | Draft ISMS Implementation Plan (Timelines, resources, priorities)[cite: 5]. | TC17, TKU17 | ISMS Mitigation Plan[cite: 5]. |
| **11** | Draft Incident Response Plan (Containment, 3rd party escalation)[cite: 5]. | TC23, TKU15 | Incident Response & Escalation Policy[cite: 5]. |
| **12** | Documentation: Collate code, graphs, and finalize Part A & Part B[cite: 5]. | TC15 (Distinction) | Completed 1000-word written justification[cite: 5]. |

---

## 2. Deliverable Execution Plans

### Deliverable A: Traffic Capture, Database & Statistical Analysis
* **Overview & Goal:** Capture network traffic, ingest it into a relational database, and apply Python-based statistical techniques (clustering/outliers) to identify anomalies[cite: 5].
* **Tools & Software Required:** Wireshark, SQLite/PostgreSQL, Python (Pandas, Scikit-learn, Matplotlib).
* **Technical Step-by-Step Breakdown:**
  1. Use Wireshark to capture traffic on the network designed in Exercise 1[cite: 5]. Export the capture as a CSV file.
  2. Create an SQLite database. Design a schema to hold the traffic data (Source IP, Dest IP, Port, Protocol, Bytes)[cite: 5].
  3. Import the CSV into the database and write a declarative SQL query to extract top talkers or anomalous port activity[cite: 5].
  4. Write a Python script to ingest the SQL output, clean the data (drop nulls), and apply K-Means clustering or Isolation Forests to automatically flag outliers[cite: 5].
  5. Generate a scatter plot visualizing the anomalous traffic cluster[cite: 5].
* **Code, Scripts & Configurations:**
  ```python
  import sqlite3
  import pandas as pd
  import matplotlib.pyplot as plt
  from sklearn.ensemble import IsolationForest

  # 1. Declarative Query to elicit information (TC3 Pass requirement)
  conn = sqlite3.connect('network_traffic.db')
  query = "SELECT src_ip, dest_port, bytes_transferred FROM traffic_logs WHERE bytes_transferred > 0"
  df = pd.read_sql_query(query, conn)

  # 2. Data Cleaning & Pre-processing
  df.dropna(inplace=True)

  # 3. Statistical Anomaly Detection (Outlier Detection)
  model = IsolationForest(contamination=0.01)
  df['anomaly'] = model.fit_predict(df[['bytes_transferred']])

  # 4. Visualization
  anomalies = df[df['anomaly'] == -1]
  plt.scatter(df['dest_port'], df['bytes_transferred'], c=df['anomaly'], cmap='coolwarm')
  plt.title('Network Traffic Anomaly Detection (Isolation Forest)')
  plt.xlabel('Destination Port')
  plt.ylabel('Bytes Transferred')
  plt.savefig('anomaly_chart.png')
  ```
* **Evidence & Artifact Collection:** Wireshark PCAP screenshot, SQLite schema definition, Python script source code, and the exported `anomaly_chart.png` graph[cite: 5].

---

### Deliverable B: Risk Modelling & External Standard Assessment
* **Overview & Goal:** Evaluate vulnerabilities identified via the traffic analysis, explicitly comparing two risk modelling techniques to justify investment in mitigations, audited against NIST/ISO 27001[cite: 5].
* **Tools & Software Required:** Spreadsheet Software, NIST CSF / ISO 27001 Framework documentation.
* **Technical Step-by-Step Breakdown:**
  1. Document the vulnerabilities exposed by the anomalies (e.g., cleartext protocols, large unexpected data exfiltration)[cite: 5].
  2. **Distinction Requirement:** Perform a risk analysis using *both* CVSS (quantitative scoring of the technical flaw) and STRIDE (qualitative architectural threat modeling)[cite: 5].
  3. Compare the two models: Note how CVSS focuses on the technical severity, while STRIDE highlights the business architecture impact[cite: 5].
  4. Assess the existing infrastructure against ISO 27001 Annex A controls, identifying gaps where current defenses failed to stop the observed anomalies[cite: 5].
* **Evidence & Artifact Collection:** STRIDE vs. CVSS comparison table, Risk Analysis matrix (Likelihood x Impact), and the External Standard Gap Analysis document[cite: 5].

---

### Deliverable C: ISMS Mitigation & Implementation Plan
* **Overview & Goal:** Develop a prioritized Information Security Management System (ISMS) implementation plan to close the gaps identified in Deliverable B[cite: 5].
* **Tools & Software Required:** Project Management format (Gantt Chart or structured table).
* **Technical Step-by-Step Breakdown:**
  1. Define the specific controls to be implemented (e.g., deploying a SIEM, enforcing TLS 1.3)[cite: 5].
  2. Prioritize recommendations based on commercial value-for-money judgements and feasibility[cite: 5].
  3. Draft an implementation roadmap detailing timelines (e.g., Q1, Q2), assigned responsibilities (e.g., Network Admin, SecOps), and required resources[cite: 5].
* **Evidence & Artifact Collection:** ISMS Mitigation Plan table detailing controls, priorities, resources, and timelines[cite: 5].

---

### Deliverable D: Incident Response & 3rd Party Escalation
* **Overview & Goal:** Manage the intrusion response process, defining containment procedures and establishing strict protocols for 3rd party involvement[cite: 5].
* **Tools & Software Required:** Word Processor.
* **Technical Step-by-Step Breakdown:**
  1. Draft a formal Incident Response Plan using the PICERL phases (Preparation, Identification, Containment, Eradication, Recovery, Lessons Learned) customized for the anomalies discovered in Deliverable A[cite: 5].
  2. Map internal team roles and communication protocols[cite: 5].
  3. Explicitly define criteria for escalating the incident to 3rd parties (e.g., "If data exfiltration exceeds 500MB of PII, immediately notify the ICO and external forensics vendors")[cite: 5].
* **Evidence & Artifact Collection:** Written Incident Response Plan with a dedicated 3rd Party Communication & Escalation matrix[cite: 5].
