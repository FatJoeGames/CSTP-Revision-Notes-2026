# Exercise 1: Operational & Implementation Master Plan

## 1. Operational Plan Document

**Assessment Strategy:** 
The objective of this 12-hour practical test is to design, build, and secure a complete digital environment for "Zone-Up Security"[cite: 1, 2]. The strategy leverages Cisco Packet Tracer for the network topology simulation and Hyper-V for the digital system deployment. Execution will strictly adhere to the NIST SP 800-53 and NCSC CAF frameworks to ensure compliance and provide a solid foundation for the written justification. To achieve Distinction marks, the architecture must encompass enterprise, network, and application layers (TC19), incorporate complex network troubleshooting (TC2), and propose additional publicly standardized assurance measures (TC20).

**KSB Competency Mapping Table:**

| KSB Code | KSB Description | Practical Task Alignment |
| :--- | :--- | :--- |
| **TC2** | Design, build, configure, optimize, test and troubleshoot simple and complex networks. | Packet Tracer distributed network build, VLANs, static/dynamic routing, and complex troubleshooting. |
| **TC4** | Build, test and debug a digital system to a specification. | Hyper-V deployment of Debian VMs for web hosting and IDPS components. |
| **TC5** | Configure an OS in accordance with security policy. | Hardening Debian (UFW, user accounts, patching) aligned to the defined security policy. |
| **TC8** | Construct software to interact with real-world & analyze exploits. | Development of the secure Python/Flask file-upload web application and dynamic exploit analysis. |
| **TC18** | Configure security technology components & key management. | pfSense deployment, Wazuh/Snort IDPS configuration, and TLS certificate (crypto) deployment. |
| **TC19** | Design & evaluate a system to a security case. | Cross-layer security implementation (Enterprise, Network, Application) mapped to the risk analysis. |
| **TC20** | Architect, analyze & justify a secure system. | Evaluating controls against NIST/NCSC CAF, planning DR, mitigating vulnerabilities. |
| **TC26** | Develop information security policy for legal/regulatory reqs. | Drafting a policy addressing data protection (e.g., GDPR) for the file upload application[cite: 1, 3]. |

**Hour-by-Hour Implementation Guide:**

| Hour | Action Step | Target KSBs | Output Deliverable |
| :--- | :--- | :--- | :--- |
| **1** | Requirement analysis, architecture planning, and Risk Management Plan drafting. | TC19, TC20, TC26 | Network Topology Diagram, Risk Register. |
| **2** | Packet Tracer build: Subnets, routers, switches. Implement static/dynamic routes. | TC2, TKU2 | Functional simulated network infrastructure. |
| **3** | Hyper-V deployment: Spin up target Debian VMs and configure base OS. | TC4, TKU4 | Base digital system environment. |
| **4** | OS Hardening: Apply security policies, UFW, least privilege, and patching. | TC5, TKU5 | Hardened OS baseline. |
| **5-7** | Software Construction: Code the web app (login, secure upload, file management). | TC8, TKU8 | Functional web application codebase. |
| **8** | App Security: Implement input validation, parameterization, and analyze for exploits. | TC8, TKU8 | Analyzed and secured software application. |
| **9** | Security Components: Deploy firewall rules and IDPS (e.g., Snort/Wazuh). | TC18, TKU18 | Active security monitoring & filtering. |
| **10** | Key Management: Generate TLS certs, implement HTTPS, establish crypto policy. | TC18, TKU18 | Secure encrypted communication channels. |
| **11** | Testing & Troubleshooting: End-to-end connectivity, exploit testing, and optimization. | TC2, TC4 | Verified, bug-free system state. |
| **12** | Documentation: Collate screenshots, finalize Part A & Part B justifications[cite: 1, 2]. | TC20, TKU19 | Completed 1000-word written justification[cite: 1, 2]. |

---

## 2. Deliverable Execution Plans

### Deliverable A: Network Design & Build
* **Overview & Goal:** Design, assemble, and configure a distributed network with multiple subnets and dynamic routing. 
* **Tools & Software Required:** Cisco Packet Tracer.
* **Technical Step-by-Step Breakdown:**
  1. Map out an external WAN, an internal LAN, and an isolated DMZ for the web server.
  2. Deploy Cisco routers and Layer 3 switches to establish multiple subnets.
  3. Configure OSPF (Dynamic) and edge static routes.
  4. Optimize traffic flow and troubleshoot simulated connectivity issues.
* **Code, Scripts & Configurations:**
  ```text
  ! Cisco IOS OSPF Configuration Example
  router ospf 1
   network 192.168.10.0 0.0.0.255 area 0
   network 192.168.20.0 0.0.0.255 area 0
  !
  ! Standard ACL for DMZ Isolation
  access-list 100 permit tcp any host 10.0.0.50 eq 443
  access-list 100 deny ip any any
  ```
* **Evidence & Artifact Collection:** Screenshot of the Packet Tracer topology, `show ip route` output displaying static/dynamic routes, successful ping test logs between subnets.

### Deliverable B: Digital System & OS Hardening
* **Overview & Goal:** Build the digital system and enforce security policy on the host operating system.
* **Tools & Software Required:** Hyper-V, Debian Linux.
* **Technical Step-by-Step Breakdown:**
  1. Provision Debian VM in Hyper-V.
  2. Implement strict password complexity and create dedicated service accounts.
  3. Configure the host firewall to only allow required ports (e.g., TCP 443, 22).
* **Code, Scripts & Configurations:**
  ```bash
  # UFW Firewall Configuration
  sudo ufw default deny incoming
  sudo ufw default allow outgoing
  sudo ufw allow 443/tcp
  sudo ufw allow from 192.168.10.0/24 to any port 22
  sudo ufw enable
  ```
* **Evidence & Artifact Collection:** `ufw status verbose` output, `/etc/security/pwquality.conf` configuration screenshot, user account permission matrices.

### Deliverable C: Secure Web Application Construction
* **Overview & Goal:** Construct an internet-facing application for secure employee file uploads.
* **Tools & Software Required:** Python (Flask), SQLite, Nginx (Reverse Proxy).
* **Technical Step-by-Step Breakdown:**
  1. Construct user login logic using hashed passwords (Argon2/Bcrypt).
  2. Build the upload mechanism, strictly verifying MIME types and utilizing `werkzeug.utils.secure_filename` to prevent directory traversal.
  3. Implement session management ensuring users can only view/delete their own uploaded files.
  4. Perform dynamic testing to verify SQLi and buffer overflow resilience.
* **Code, Scripts & Configurations:**
  ```python
  # Python Flask Secure Upload Snippet
  import os
  from werkzeug.utils import secure_filename
  from flask import request, abort

  ALLOWED_EXTENSIONS = {'txt', 'pdf', 'png', 'jpg'}

  def allowed_file(filename):
      return '.' in filename and filename.rsplit('.', 1)[1].lower() in ALLOWED_EXTENSIONS

  @app.route('/upload', methods=['POST'])
  def upload_file():
      # Validate user session here
      if 'file' not in request.files:
          abort(400)
      file = request.files['file']
      if file and allowed_file(file.filename):
          filename = secure_filename(file.filename) # Mitigates directory traversal
          file.save(os.path.join(app.config['UPLOAD_FOLDER'], filename))
          # Log upload date, size, and user to database via parameterized query
  ```
* **Evidence & Artifact Collection:** Source code snippets of input validation, screenshots of the functional web GUI (upload, view, delete), and a vulnerability analysis log proving SQLi/brute force mitigation.

### Deliverable D: Security Components & Key Management
* **Overview & Goal:** Deploy security components and cryptographic protocols.
* **Tools & Software Required:** pfSense (if virtualized routing is used alongside Packet Tracer) or Snort/Wazuh, OpenSSL.
* **Technical Step-by-Step Breakdown:**
  1. Configure an IDPS (Intrusion Detection and Prevention System) to monitor the web application traffic.
  2. Generate a TLS cryptographic certificate for the web application.
  3. Develop a Key Management Plan detailing certificate generation, storage, and rotation.
* **Code, Scripts & Configurations:**
  ```bash
  # Generate RSA Private Key and Self-Signed Certificate for Web App (HTTPS)
  openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
    -keyout /etc/ssl/private/webapp.key \
    -out /etc/ssl/certs/webapp.crt
  ```
* **Evidence & Artifact Collection:** IDPS rule configuration snippet, browser padlock screenshot verifying HTTPS, OpenSSL command execution log, and the Key Management Plan document.

---
