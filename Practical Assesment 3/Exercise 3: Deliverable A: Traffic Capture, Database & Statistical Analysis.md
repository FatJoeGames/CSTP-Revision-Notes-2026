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




To guarantee you hit every Pass criteria for Deliverable A, you need to seamlessly transition from raw data ingestion to statistical anomaly detection. By pre-staging these exact scripts and workflows, you eliminate the cognitive load of writing code on the day and can focus entirely on your written justifications.
Here is your exact execution playbook and the scripts to run for Deliverable A.
1. Network Traffic Inspection (TC22, TKU22)
The Execution: Do not waste time manually scrolling through Wireshark. Open your terminal and use tshark to instantly parse the provided PCAP file and extract the protocol anomalies.
The Script:
# 1. Spot Malware Beacons: Extract and count all HTTP User-Agents
tshark -r capture.pcap -T fields -e http.user_agent | sort | uniq -c | sort -nr | head -n 10

# 2. Spot DNS Tunneling: Find abnormally long DNS queries
tshark -r capture.pcap -Y "dns.qry.name" -T fields -e dns.qry.name | awk '{ if (length($1) > 50) print $1 }'

# 3. Spot Cleartext Credentials: Extract HTTP POST request payloads
tshark -r capture.pcap -Y "http.request.method == POST" -T fields -e text

Write-up Action: Paste the terminal output into your report. State that by inspecting network packet data structures, you identified anomalous protocol behaviors (e.g., a suspicious User-Agent or DNS exfiltration) that signature-based tools missed.
2. Database Creation & SQL Correlation (TC3, TC22)
The Execution: You must demonstrate the use of a declarative query language to correlate logical SIEM logs with physical security systems. You can use DB Browser for SQLite or a quick MySQL instance in your lab to execute this.
The Script:
-- Step 1: Design the database structure
CREATE TABLE network_logs (timestamp DATETIME, username VARCHAR(50), source_ip VARCHAR(15), status VARCHAR(10));
CREATE TABLE physical_access (last_swipe_time DATETIME, username VARCHAR(50), location VARCHAR(50));

-- Step 2: The Correlation Query ("Impossible Access")
SELECT 
    n.timestamp, 
    n.username, 
    n.source_ip, 
    p.last_swipe_time,
    p.location
FROM 
    network_logs n
LEFT JOIN 
    physical_access p ON n.username = p.username
WHERE 
    n.status = 'SUCCESS'
    AND n.source_ip LIKE '192.168.%'
    AND (p.last_swipe_time IS NULL OR p.last_swipe_time < datetime(n.timestamp, '-12 hours'));

Write-up Action: Export the query result. Explain that this SQL script successfully correlated heterogeneous sources by proving a user successfully authenticated to the internal network despite having no physical CCTV or badge swipe records for the building.
3. Statistical Security Analytics (TKU3, TKU22)
The Execution: To satisfy the "Big Data" and "Algorithmic Detection" requirements, run this Python script against a large CSV log file (e.g., a firewall or proxy log).
The Script:
import pandas as pd
from scipy import stats
import numpy as np

# 1. Ingest Big Data Log (Simulating a Hadoop/distributed dataset export)
df = pd.read_csv('firewall_logs.csv')

# 2. Group traffic by user to calculate total outbound bytes
user_traffic = df.groupby('source_ip')['bytes_out'].sum().reset_index()

# 3. Apply Statistical Technique: Calculate the Z-Score
user_traffic['z_score'] = np.abs(stats.zscore(user_traffic['bytes_out']))

# 4. Algorithmic Detection: Flag data exfiltration (> 3 standard deviations)
exfiltration_alerts = user_traffic[user_traffic['z_score'] > 3.0]

print("--- ALGORITHMIC ANOMALY DETECTION RESULTS ---")
print(exfiltration_alerts.sort_values(by='z_score', ascending=False))

Write-up Action: Paste the script and output. Explicitly state that you applied statistical techniques (Z-score standard deviation) to a large dataset, successfully demonstrating algorithmic anomaly detection over standard signature-based methods.
Are you comfortable executing these scripts in the lab environment, or do you need to adjust them for a specific operating system like Debian or Windows?

