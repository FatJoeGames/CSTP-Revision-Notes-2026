### Deliverable D: Security Components & Key Management

**The Goal:** Configure and use security technology components (such as firewalls and IDPS), implement cryptographic protocols for secure communication and data storage, and develop/implement a key management plan[cite: 1].

**Required Tools:** Snort, XAMPP (OpenSSL), Windows Defender Firewall.

#### Phase 1: Security Technology Component Configuration
Select and configure common security hardware and software components to implement the required security policy and protect the system[cite: 1].
*   **Action:** Deploy and configure an Intrusion Detection and Prevention System (IDPS) using Snort on your Windows host/VM environment to monitor network traffic hitting your web application server[cite: 1].
*   **Firewall Hardening:** Ensure Windows Defender Firewall rules are strictly configured to drop unauthorized traffic while maintaining explicit rules for secure management access and encrypted web traffic (Port 443)[cite: 1].

**Snort Rule Configuration Snippet (`snort.rules`):**
```text
# Alert rule to detect potential brute force or directory traversal attempts against the web app
alert tcp any any -> $HOME_NET 443 (msg:"Potential Directory Traversal or Attack Payload Detected"; flow:to_server,established; content:"../"; sid:1000002; rev:1;)
```

#### Phase 2: Cryptographic Protocols Implementation (TLS)
Configure cryptographic protocols to ensure secure communication for the web application, safeguarding data in transit[cite: 1].
*   **Action:** Use OpenSSL within your XAMPP/Apache environment to generate a private key and a self-signed TLS certificate, enforcing HTTPS encryption for all employee logins and file uploads[cite: 1].

**OpenSSL Certificate Generation & Apache Configuration Snippets:**
```bash
# 1. Generate RSA Private Key and Self-Signed Certificate
openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
  -keyout C:/xampp/apache/conf/ssl.key/server.key \
  -out C:/xampp/apache/conf/ssl.crt/server.crt
```

```text
# 2. Configure Apache SSL Virtual Host (httpd-ssl.conf)
<VirtualHost *:443>
    DocumentRoot "C:/xampp/htdocs/secure_app"
    ServerName secure-app.local
    SSLEngine on
    SSLCertificateFile "conf/ssl.crt/server.crt"
    SSLCertificateKeyFile "conf/ssl.key/server.key"
    SSLProtocol all -SSLv2 -SSLv3 -TLSv1 -TLSv1.1
    SSLCipherSuite HIGH:!aNULL:!MD5
</VirtualHost>
```

#### Phase 3: Key Management Plan Development
Develop and implement a formal key management plan covering the lifecycle of the cryptographic keys and certificates used by the application[cite: 1].
*   **Action:** Document a comprehensive Key Management Plan addressing the following core elements:
    *   **Generation:** Utilizing secure cryptographic algorithms (RSA 2048-bit minimum) with high entropy.
    *   **Storage:** Storing private keys in restricted-access directories (`conf/ssl.key/`) with strict NTFS file permissions allowing only SYSTEM/Administrator access.
    *   **Rotation & Expiry:** Enforcing a 365-day validity window with a scheduled procedure for annual certificate renewal before expiry.
    *   **Revocation & Destruction:** Establishing protocols for immediate key revocation and secure file shredding if a private key compromise is detected.

#### Phase 4: Evidence & Artifact Collection
*   **Action:** Capture screenshots of the browser showing a valid secure padlock connection (HTTPS)[cite: 1], collect Snort log outputs showing active rule triggers during security testing, and compile the final written Key Management Plan document for inclusion in your submission evidence.


Info Policy:
1. Purpose and Scope

    Purpose: To define the security baseline, protect corporate information assets, ensure business continuity, and enforce legal compliance across all Home Tech operating environments.

    Scope: This policy applies to all Home Tech employees, contractors, third-party vendors, and all digital systems, including the central administrative network, distribution center management systems, retail store point-of-sale (POS) terminals, and the remote employee web portal.

2. Regulatory and Legal Compliance (TC26 Alignment)

Home Tech operations strictly comply with the following legislative frameworks under English jurisdiction:

    UK GDPR & Data Protection Act 2018: Mandates the lawful, transparent, and secure processing of personal and sensitive data (e.g., employee credentials and operational records). All data stored on internal databases or uploaded via corporate applications must be encrypted at rest and in transit (utilising TLS protocols).

    Computer Misuse Act 1990: Prohibits unauthorized access to computer material, unauthorized modification of computer data, and impairment of system operation. All internal testing must be authorized and restricted to designated testing environments.

3. Access Control and Authentication Policy

    Principle of Least Privilege: Employees at distribution centers and retail stores shall only be granted access to the specific network segments, applications, and files necessary to perform their job roles.

    Authentication Standards:

        Access to corporate systems and the web portal requires unique user credentials (email and a complex password enforcing minimum length and complexity rules).

        Session management must utilize secure tokens with automatic timeouts to prevent session hijacking.

    Prohibited Practices: Sharing account credentials or using default system accounts is strictly prohibited.

4. Network Security and Multi-Site Segmentation

    Site Isolation: Distribution centers and retail stores must operate on segmented subnets, isolated from the central corporate network via firewalls and Access Control Lists (ACLs).

    Payment & Critical Systems Protection: Payment terminals and sensitive inventory databases must be heavily restricted, blocking unauthorized inter-VLAN communication to minimize the lateral movement of threats.

    Remote Access: Any external interaction with Home Tech infrastructure must occur over encrypted secure channels (e.g., HTTPS/TLS).

5. Software Development and Data Handling Policy

    Secure Coding: Software developed for Home Tech (such as internal web applications) must follow defensive programming principles, including input validation, parameterized queries (PDO) to prevent SQL injection, and output encoding to prevent Cross-Site Scripting (XSS).

    File Management: Files uploaded by employees must undergo strict type verification and be stored using randomized file identifiers to prevent directory traversal and arbitrary code execution vulnerabilities.

6. Incident Reporting and Enforcement

    Breach Reporting: Any suspected security breach, unauthorized access attempt, or data leak must be reported immediately to the IT Security team.

    Disciplinary Action: Failure to comply with this policy may result in disciplinary action up to and including termination of employment, alongside potential legal prosecution under the Computer Misuse Act 1990.


Crypto:

This appendix provides the technical evidence, configuration logs, and lifecycle management plan associated with the deployment of cryptographic controls for the Home Tech secure web portal, fulfilling requirements under Technical Competency 18 (TC18) and Technical Knowledge and Understanding 18 (TKU18).  1. OpenSSL Certificate Generation & Cryptographic ParametersTo protect data in transit and establish secure communications across the web portal, a self-signed RSA x509 digital certificate was generated using the OpenSSL command-line toolkit.  Execution Command Log:Bashsudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
-keyout /etc/ssl/private/zoneup.key \
-out /etc/ssl/certs/zoneup.crt \
-subj "/C=GB/ST=East Yorkshire/L=Hull/O=Home Tech/CN=portal.hometech.local"
Technical Parameter Justification:Algorithm: RSA with a 2048-bit modulus length was selected to balance strong cryptographic security with computational efficiency, aligning with current industry baselines.Validity Period: Configured for 365 days to align with internal operational rotation schedules.Entropy Source: Leveraged underlying Linux kernel entropy pools (/dev/urandom) during private key generation to ensure adequate unpredictability.2. Apache TLS VirtualHost ConfigurationThe generated keys and certificates were integrated into the Apache web server configuration to enforce secure HTTPS transport and deprecate unencrypted HTTP connections.Configuration Snippet (/etc/apache2/sites-available/default-ssl.conf):Apache<VirtualHost *:443>
    ServerName portal.hometech.local
    DocumentRoot /var/www/html

    SSLEngine on
    SSLCertificateFile /etc/ssl/certs/zoneup.crt
    SSLCertificateKeyFile /etc/ssl/private/zoneup.key

    # Enforce modern secure protocols and ciphers
    SSLProtocol all -SSLv3 -TLSv1 -TLSv1.1 +TLSv1.2 +TLSv1.3
    SSLCipherSuite HIGH:!aNULL:!MD5

    ErrorLog ${APACHE_LOG_DIR}/ssl_error.log
    CustomLog ${APACHE_LOG_DIR}/ssl_access.log combined
</VirtualHost>
3. Home Tech Key Management Plan (Lifecycle & Governance)To satisfy the key management plan requirement for enterprise deployment, the following governance lifecycle is established:Lifecycle StageOperational Procedure & Security Control1. GenerationCryptographic keys generated on isolated administrative systems using cryptographically secure pseudo-random number generators (CSPRNG) with verified entropy.  2. StoragePrivate keys (.key) are stored strictly within restricted server directories (/etc/ssl/private/) with file permissions locked down to root:root (chmod 600), preventing unauthorized local read access.3. UsageKeys are accessed exclusively by the Apache web service daemon (www-data) during TLS handshake initialization and session establishment.  4. Rotation & RevocationCertificates are scheduled for mandatory annual renewal (365-day lifecycle). In the event of a suspected compromise, keys are immediately revoked, regenerated via OpenSSL, and redeployed.
