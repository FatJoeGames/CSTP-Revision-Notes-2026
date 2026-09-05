### Deliverable C: Secure Web Application Construction

**The Goal:** Construct software to interact with the real world (an internet-facing web application) and analyze it for security exploits.

**Required Tools:** XAMPP (Apache, PHP, MySQL), Burp Suite, SQLMAP, Kali Linux.

#### Phase 1: Architecture & Database Build
To meet specifications, the application must handle secure user authentication and isolated file management.
*   **Action:** Initialize XAMPP and configure the MySQL database backend to manage user profiles and uploaded file metadata securely.

**SQL Database Schema Snippet:**
```sql
CREATE DATABASE secure_app;
USE secure_app;

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    email VARCHAR(255) NOT NULL UNIQUE,
    password_hash VARCHAR(255) NOT NULL
);

CREATE TABLE files (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    file_name VARCHAR(255) NOT NULL,
    file_size INT NOT NULL,
    upload_date DATETIME NOT NULL,
    storage_path VARCHAR(255) NOT NULL,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```

#### Phase 2: Application Construction (Secure Coding)
Develop the core features according to the specification: secure login, file upload, and file management displaying file name, size, and upload date.
*   **Action:** Write the PHP scripts implementing strict input validation, parameterized queries to prevent SQL injection, and safe filename handling to prevent directory traversal.

**PHP Implementation Snippet (`login.php` & `upload.php`):**
```php
<?php
session_start();
$pdo = new PDO("mysql:host=127.0.0.1;dbname=secure_app", "root", "");

// 1. Secure Login Logic (Mitigates SQL Injection via Prepared Statements)
if ($_SERVER['REQUEST_METHOD'] === 'POST' && isset($_POST['login'])) {
    $stmt = $pdo->prepare('SELECT id, password_hash FROM users WHERE email = ?');
    $stmt->execute([$_POST['email']]);
    $user = $stmt->fetch();
    
    if ($user && password_verify($_POST['password'], $user['password_hash'])) {
        $_SESSION['user_id'] = $user['id'];
    }
}

// 2. Secure File Upload Logic (Mitigates Path Traversal & Buffer Overflows)
if ($_SERVER['REQUEST_METHOD'] === 'POST' && isset($_FILES['file'])) {
    if (!isset($_SESSION['user_id'])) {
        die("Unauthorized access.");
    }
    
    $allowed_extensions = ['txt', 'pdf', 'png', 'jpg'];
    $filename = basename($_FILES['file']['name']);
    $ext = pathinfo($filename, PATHINFO_EXTENSION);
    
    // Validate extension and restrict size (< 5MB)
    if (in_array($ext, $allowed_extensions) && $_FILES['file']['size'] < 5000000) {
        $safe_name = preg_replace("/[^a-zA-Z0-9.-]/", "_", $filename);
        $dest = "C:/xampp/htdocs/uploads/" . uniqid() . "_" . $safe_name;
        
        if (move_uploaded_file($_FILES['file']['tmp_name'], $dest)) {
            $stmt = $pdo->prepare('INSERT INTO files (user_id, file_name, file_size, upload_date, storage_path) VALUES (?, ?, ?, NOW(), ?)');
            $stmt->execute([$_SESSION['user_id'], $safe_name, $_FILES['file']['size'], $dest]);
        }
    }
}
?>
```

#### Phase 3: Exploit Analysis & Testing
Identify and assess potential security vulnerabilities or exploits in the software (such as SQL injection, brute force, or buffer overflows).
*   **Action:** Spin up your Kali Linux VM and use Burp Suite to intercept HTTP requests, testing session token behavior and form inputs. Run SQLMAP against the login parameters to empirically prove the application is resilient against database extraction attacks.

**Exploit Testing Command:**
```bash
# Test login form for SQL Injection vulnerabilities using SQLMAP from Kali Linux
sqlmap -u "http://<windows-vm-ip>/secure_app/login.php" --data="email=test@test.com&password=test" --batch --dbs
```

#### Phase 4: Evidence & Artifact Collection
*   **Action:** Compile source code snippets highlighting secure coding constructs, capture screenshots of the working user interface showing file size, name, and upload date, and document the SQLMAP output log confirming that parameterization successfully blocked injection payloads.
