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
