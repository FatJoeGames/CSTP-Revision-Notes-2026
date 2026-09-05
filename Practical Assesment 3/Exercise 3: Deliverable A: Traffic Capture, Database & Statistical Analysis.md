### Deliverable A: Traffic Capture, Database & Statistical Analysis

**The Goal:** Collect network traffic data, design and populate a database, and apply statistical techniques (clustering, classification, outlier detection) to identify anomalies and vulnerabilities.

**Required Tools:** Wireshark, SQLite (or MySQL/PostgreSQL), Python (Pandas, Scikit-learn, Matplotlib).

#### Phase 1: Traffic Capture & Big Data Architecture (Targeting TC3 & TKU3)
You must capture real-time network traffic from the devices you designed in the previous exercises and understand the underlying data architectures.
*   **Action:** Run Wireshark on your network interfaces (e.g., mirroring a port on your virtual switch or monitoring the DMZ edge).
*   **Execution:** Capture a substantial PCAP file containing normal traffic mixed with simulated anomalous traffic (e.g., an Nmap scan or large file exfiltration). Export this capture to a CSV format for ingestion.
*   **Big Data Vulnerability Identification:** To meet the TC3 requirement of identifying vulnerabilities in big data architectures, document the inherent risks of storing large PCAP datasets. Explicitly mention vulnerabilities such as unencrypted data-at-rest in Hadoop clusters, weak access controls on data lakes, and the risk of data poisoning.

#### Phase 2: Database Design & Querying (Targeting TC3)
You must design a database of relevant information and use a declarative query language (SQL) to elicit information from it.
*   **Action:** Set up a relational database and define a schema that accurately represents the network traffic data.
*   **Execution:** Import the CSV data into the database. Write SQL queries to extract specific subsets of data (e.g., filtering out standard internal broadcast traffic) to feed into your statistical tool.

**SQL Database Schema & Elicitation Snippet:**
```sql
-- 1. Design and set up the database schema
CREATE TABLE network_traffic (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    timestamp DATETIME,
    source_ip TEXT,
    dest_ip TEXT,
    dest_port INTEGER,
    protocol TEXT,
    bytes_transferred INTEGER
);

-- 2. Declarative query to elicit information (TC3 Pass Requirement)
-- Extracting high-volume traffic targeting critical web server ports
SELECT source_ip, dest_port, SUM(bytes_transferred) as total_bytes
FROM network_traffic
WHERE dest_port IN (80, 443, 22)
GROUP BY source_ip, dest_port
ORDER BY total_bytes DESC;
```

#### Phase 3: Data Cleaning & Pre-processing (Targeting TC14)
Import the data into a statistical analysis tool (Python) and perform data cleaning and pre-processing to remove any errors or inconsistencies.
*   **Action:** Write a Python script using the Pandas library to connect to your database, load the query results into a DataFrame, and handle missing or malformed data.
*   **Execution:** Drop null values, normalize IP addresses, and ensure byte counts are numerical to prepare the dataset for machine learning algorithms.

#### Phase 4: Statistical Analysis & Visualization (Targeting TC3 & TKU3)
Use statistical techniques such as clustering analysis, classification analysis, and outlier detection to identify any anomalies in the network traffic, and visualize the findings.
*   **Action:** Implement a machine learning algorithm (e.g., K-Means for clustering or Isolation Forest for outlier detection) using Scikit-learn in Python. 
*   **Execution:** Train the model on the pre-processed data to flag traffic that deviates from the baseline. Generate charts and graphs to communicate these findings clearly.

**Python Statistical Analysis & Visualization Snippet:**
```python
import sqlite3
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler

# 1. Connect and Load Data
conn = sqlite3.connect('traffic_analysis.db')
df = pd.read_sql_query("SELECT dest_port, bytes_transferred FROM network_traffic WHERE dest_port IS NOT NULL", conn)

# 2. Data Pre-processing
# Scale the data so large byte counts don't skew the clustering algorithm
scaler = StandardScaler()
scaled_data = scaler.fit_transform(df)

# 3. Apply Statistical Techniques (Clustering Analysis)
# Group traffic into 3 clusters: Normal, High-Volume, and Anomalous
kmeans = KMeans(n_clusters=3, random_state=42)
df['cluster'] = kmeans.fit_predict(scaled_data)

# 4. Data Visualization
plt.figure(figsize=(10, 6))
colors = {0: 'blue', 1: 'green', 2: 'red'} # Red denotes the anomaly cluster
plt.scatter(df['dest_port'], df['bytes_transferred'], c=df['cluster'].map(colors), alpha=0.6)
plt.title('Network Traffic Clustering: Anomaly Detection')
plt.xlabel('Destination Port')
plt.ylabel('Bytes Transferred')
plt.grid(True)
plt.savefig('traffic_clusters.png')
```

#### Phase 5: Evidence & Artifact Collection
*   **Action:** Compile the evidence to prove competency across the KSBs.
*   **Collection Requirements:**
    1. A screenshot of the raw Wireshark capture running in real-time.
    2. The SQL script showing database creation and the declarative `SELECT` queries.
    3. The full Python script demonstrating data cleaning, clustering, and plotting.
    4. The exported `traffic_clusters.png` graph, paired with a brief paragraph explaining how the visual data proves a network anomaly (e.g., identifying a red cluster of massive data transfer over port 443 indicating exfiltration).
    5. A brief summary documenting the vulnerabilities in big data architectures used for storing these logs.
