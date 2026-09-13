## Exercise 3: Monitor (Statistical Analysis & Risk Management)

### Deliverable A: Traffic Capture & Big Data Analysis
*   **Wireshark:** For executing the live network packet capture and exporting the traffic logs to CSV format.
*   **SQLite3 / DB Browser:** For building the relational database and executing the required declarative SQL queries.
*   **Jupyter Notebooks (Python):** The best environment for running Pandas (data cleaning), Scikit-learn (K-Means/Isolation Forest algorithms), and Matplotlib (rendering the scatter plots).

### Deliverable B: Risk Modelling & External Standard Assessment
*   **STRIDE / CVSS Frameworks:** Methodological tools for conducting the comparative risk analysis (qualitative vs. quantitative).
*   **ISO/IEC 27001 or NIST CSF Documentation:** Official frameworks required to perform the gap analysis on the organization's current IT infrastructure.

### Deliverable C: ISMS Mitigation & Implementation Plan
*   **Spreadsheet Software (Excel / Google Sheets):** For creating the prioritization matrix (Impact vs. Feasibility).
*   **GanttProject (or equivalent):** For drafting the implementation timeline, tracking SLAs, and mapping resource allocations for the ISMS plan.

### Deliverable D: Incident Response & 3rd Party Escalation
*   **Splunk (Free Tier) / ELK Stack:** To simulate how log files, network data, and access control systems are correlated to declare a breach.
*   **Action Fraud / NCSC (Websites):** For referencing the official UK escalation criteria and reporting portals for 3rd party law enforcement involvement.



### Datasets

*  **Malware-Traffic-Analysis.net:** The gold standard for PCAPs. It provides real-world traffic captures of malware infections (e.g., Emotet, Qakbot). You can download a PCAP, run it through Wireshark/TShark, and easily fulfill the "inspection of network packet data structures" requirement.
* **Splunk "Boss of the SOC" (BOTS) Datasets (Available on GitHub):** This is a massive, enterprise-grade SIEM dataset. It includes Windows Event Logs, firewall logs, and crucially, AWS/Azure access logs. It is perfect for demonstrating SIEM correlation.
* **Kaggle (CIC-IDS2017 or UNSW-NB15):** These are massive, heterogeneous datasets containing millions of rows of network traffic with labelled anomalies (DDoS, Brute Force, Web Attacks). They are perfect for importing into a database to demonstrate your SQL querying and statistical analysis skills.

### Scripts

## The SQL Correlation Query
**The Requirement:** Use a declarative query language and correlate network logs with physical security systems.
**The Scenario:** You are looking for an "Impossible Access" anomaly—a user who authenticated to the internal network, but physical CCTV/badge logs show they never actually entered the building.

```bash
-- Objective: Detect internal network logins from users who have not physically swiped into the building.

SELECT 
    nl.timestamp AS network_login_time,
    nl.username,
    nl.source_ip,
    nl.destination_ip,
    ps.last_swipe_time,
    ps.building_location
FROM 
    network_authentication_logs nl
LEFT JOIN 
    physical_badge_swipes ps ON nl.username = ps.username
WHERE 
    nl.authentication_status = 'SUCCESS'
    AND nl.source_ip LIKE '192.168.%' -- Internal network IP range
    AND (ps.last_swipe_time IS NULL OR ps.last_swipe_time < DATE_SUB(nl.timestamp, INTERVAL 12 HOUR))
ORDER BY 
    nl.timestamp DESC;
```

## The Python Statistical Anomaly Script
```bash
import pandas as pd
import numpy as np
from scipy import stats

# 1. Load the heterogeneous big data log (e.g., firewall or proxy logs)
# Using pandas to handle the massive data architecture
df = pd.read_csv('firewall_traffic_logs.csv')

# 2. Group traffic by Source IP to find total bytes sent
traffic_volumes = df.groupby('source_ip')['bytes_out'].sum().reset_index()

# 3. Apply statistical technique: Calculate the Z-Score
# A Z-Score above 3 indicates an algorithmic anomaly (3 standard deviations from the mean)
traffic_volumes['z_score'] = np.abs(stats.zscore(traffic_volumes['bytes_out']))

# 4. Filter and flag the anomalies (Potential Data Exfiltration)
anomalies = traffic_volumes[traffic_volumes['z_score'] > 3.0]

print("--- ALGORITHMIC ANOMALY DETECTION RESULTS ---")
print(anomalies.sort_values(by='z_score', ascending=False))
```

## The TShark PCAP Extraction Cheat Sheet
**The Requirement:** Recognize anomalies by inspection of network packet data structures/protocol behaviors.
**The Scenario:** You need to extract specific anomalous protocol behaviors from a PCAP file without scrolling blindly through Wireshark.
```bash
# 1. Extract and count anomalous HTTP User-Agents (often reveals malware beacons)
tshark -r capture.pcap -T fields -e http.user_agent | sort | uniq -c | sort -n

# 2. Identify protocol anomalies: DNS queries to excessively long subdomains (DNS Tunneling)
tshark -r capture.pcap -Y "dns.qry.name" -T fields -e dns.qry.name | awk '{ if (length($1) > 50) print $1 }'

# 3. Spot unencrypted credential transmission (Cleartext FTP/HTTP)
tshark -r capture.pcap -Y "http.request.method == POST" -T fields -e text
```
