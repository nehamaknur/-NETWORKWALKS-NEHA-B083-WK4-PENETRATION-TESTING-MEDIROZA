<h1 align="center">🏥 MEDIROZA HOSPITAL - PENETRATION TESTING PROJECT</h1>
<h2 align="center">Batch B083 | Week 4: Professional Penetration Testing Report</h2>

<p align="center">
  <a href="https://github.com/cortexneha"><img src="https://img.shields.io/badge/PROJECT-MEDIROZA_PENTEST-red?style=for-the-badge"></a>
  <a href="https://github.com/cortexneha"><img src="https://img.shields.io/badge/TARGET-MEDIROZAHOSPITAL.COM-orange?style=for-the-badge"></a>
  <a href="https://github.com/cortexneha"><img src="https://img.shields.io/badge/SCOPE-FULL_BLACKBOX-green?style=for-the-badge"></a>
  <a href="https://github.com/cortexneha"><img src="https://img.shields.io/badge/MILESTONES-M1_TO_M4-yellowgreen?style=for-the-badge"></a>
  <a href="https://github.com/cortexneha"><img src="https://img.shields.io/badge/INTERNSHIP-NETWORKWALKS_B083-blueviolet?style=for-the-badge"></a>
  <a href="https://github.com/cortexneha"><img src="https://img.shields.io/badge/GITHUB-CORTEXNEHA-black?style=for-the-badge"></a>
  <a href="https://github.com/cortexneha"><img src="https://img.shields.io/badge/AUTHOR-NEHA_MAKNUR-purple?style=for-the-badge"></a>
</p>

---

## 📋 Project Details

| Field | Details |
| :--- | :--- |
| **👤 Pentester Name** | Neha Maknur |
| **🎓 Program/Batch** | B083-Networkwalks Cybersecurity Internship |
| **📅 Date** | 30 September 2026 |
| **📂 Modules Completed** | Week 4: Mediroza General Hospital Penetration Test (Milestones 1 to 4) |
| **🎯 Client/Target** | `https://medirozahospital.com` (written permission secured) |
| **✍️ Permission Secured?** | ✅ Yes |
| **🔍 Scope & Objective** | Full black-box penetration test. Identify vulnerabilities, exploit for real impact, and document findings. |

---

## ⚠️ 1. Liability Disclaimer
> I have performed these activities only on the systems & devices where I had secured written permission or the devices/systems that I own myself. All these materials are for education and research purpose only. Do not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorised access is a crime even when nothing is damaged.

---

## 🚀 2. Introduction
This report covers the comprehensive penetration testing engagement conducted against Mediroza General Hospital (`https://medirozahospital.com`) during Week 4 of my ongoing cybersecurity internship program at Networkwalks. The assessment followed a strict full black-box methodology across four progressive milestones—ranging from initial reconnaissance, infrastructure discovery, and access control bypass, through cryptographic password cracking, to uncovering critical server-side internal data exposures (such as staff salaries and shareholder records).

---
## 🔬 3. Project Milestones & Technical Breakdown

### 🎯 Milestone 1: Initial Access & Reconnaissance
* **Target Domain:** `medirozahospital.com` (`199.188.201.16`)
* **Methodology:** Black-box web assessment and infrastructure enumeration (conducted with zero prior credentials or application source code provided).
* **Active Reconnaissance Findings:**
  * **Network Port Scanning (`nmap -sV`):** Successfully identified open ports and running services across the target infrastructure, including FTP (Port 21, Pure-FTPd), DNS (Port 53, BIND), HTTP/HTTPS proxies (Ports 80 & 443, HAProxy 2.0.8), and mail services (POP3/IMAP/SMTP via Dovecot and Exim).
    
    <img src="Evidence%20files/nmap_screenshot.png" width="800">
    
    *Figure: Running port and service detection scans using nmap -sV*

 * **HTTP Probing & WAF Detection (`curl`, `wafw00f`):** Used `curl` requests to inspect server headers and deployed `wafw00f` against the web application, confirming that no active Web Application Firewall (WAF) was deployed (`No WAF detected by the generic detection`).
    <img src="Evidence%20files/Curl_Wafw00f_screenshots.png" width="800">

    *Figure: Checking HTTP server headers and fingerprinting WAF presence using wafw00f*

  * **DNS Enumeration (`nslookup`, `dig`, `dnsrecon`):** Mapped authoritative name servers and mail exchange routing records (`mx1-hosting.jellyfish.systems`) hosted via web infrastructure (`server274.web-hosting.com`).
    
    <img src="Evidence%20files/nslookup_dig_screenshorts.png" width="800">

    *Figure: Performing DNS lookup and domain queries using nslookup and dig*

    <img src="Evidence%20files/dnsrecon_screenshot.png" width="800">
    
    *Figure: Executing automated DNS enumeration via dnsrecon against medirozahospital.com*

* **Attack Execution & SQL Injection Discovery:** 
  * While analyzing the Patient Portal login functionality (`/patient/login.php`), input fields were tested for improper escaping. Entering specialized characters triggered an explicit database warning: `Warning: mysqli_query(): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '\'' at line 1`.
    
    <img src="Evidence%20files/syntax_error.png" width="800">
  
    *Figure: Executing SQL injection authentication bypass on the Patient Portal login form*

  * This error confirms that the application directly concatenates user input into backend SQL queries without parameterization, exposing a high-severity SQL Injection vulnerability that facilitates authentication bypass.

* **Milestone Deliverable:** Successfully identified the injection vector and retrieved **3 confidential patient PDF lab reports** following access bypass.
  
    <img src="Evidence%20files/Lab_Reports_screenshot.png" width="800">
  
    *Figure: Accessing the authenticated My Lab Reports dashboard displaying encrypted PDF files*

### 🔑 Milestone 2: Data Extraction & Cryptographic Cracking
* **Objective:** Crack the cryptographic encryption protecting all 3 retrieved patient PDF lab reports.
* **Methodology:** File encryption analysis and targeted password recovery.
* **Execution & Challenges:** 
  * Analyzed the specific encryption scheme protecting each document to determine the appropriate cracking methodology.
  * Tested various tools and customized wordlists, recognizing that a single brute-force approach would not succeed uniformly across all files.
    
   <img src="Evidence%20files/Pdf1_password_screenshot.png" width="800">
  
   *Figure: Cracking password hash for My Locked PDF1.pdf using the Networkwalks password cracker*
  
   <img src="Evidence%20files/Pdf2_password_screenshot.png" width="800">
  
   *Figure: Cracking password hash for My Locked PDF2.pdf using the Networkwalks password cracker*
  
   <img src="Evidence%20files/Pdf3_password_screenshot.png" width="800">
  
   *Figure: Cracking password hash for My Locked PDF3.pdf using the Networkwalks password cracker*
  
* **Milestone Deliverable:** Successfully recovered the plaintext contents of all 3 restricted files with verifiable proof of access.
  
   <img src="Evidence%20files/Patient_report1_screenshot.png" width="800">
  
   *Figure: Viewing the decrypted confidential pathology report for patient Sipho Dlamini*

   <img src="Evidence%20files/Patient_report2_screenshot.png" width="800">
  
   *Figure: Viewing the decrypted confidential pathology report for patient Priya Reddy*

   <img src="Evidence%20files/Patient_report3_screenshot.png" width="800">
   
   *Figure: Viewing the decrypted confidential pathology report for patient Emily Thompson*


---

### 📂 Milestone 3: Critical Data Exposure
* **Objective:** Uncover critical internal server-side data exposures on the client server.
* **Methodology:** Deep examination of retrieved file properties, metadata, directory enumeration, and hidden server paths.
* **Findings & Discoveries:**
  * Conducted a thorough analysis beyond the obvious application content, examining all file properties carefully.
    
    <img src="Evidence%20files/robots.txt.png" width="800">
    
     *Figure: Analyzing the robots.txt file to uncover sensitive internal administrative paths*
    
  * Uncovered sensitive internal administrative files pointing to further critical server exposures.
    
    <img src="Evidence%20files/website_old_path.png" width="800">
    
    *Figure: Uncovering sensitive internal administrative files and server path exposures*
    
  * Successfully extracted the **salaries of all hospital employees** and the **shareholder details of the hospital**.
* **Milestone Deliverable:** Full documented evidence of the server exposure and a readable summary of the confidential financial and corporate records uncovered.
  
  <img src="Evidence%20files/Blur_staffs_info_sql_file.png" width="800">
  
   *Figure: Extracting hospital employee salaries and staff information from the SQL database file*
  
  <img src="Evidence%20files/Blur_shareholders_info_sql_file.png" width="800">

   *Figure: Extracting hospital employee salaries and staff information from the SQL database file*

---

### 📊 Milestone 4: Professional Reporting
* **Objective:** Compile all findings, evidence, and risk assessments into a professional penetration testing report for the client.
* **Structure & Deliverables:**
  * **01. Executive Summary:** A concise overview of the engagement, key findings, and overall risk to the client.
  * **02. Scope and Methodology:** Target specification, tools utilized, approach taken, and testing limitations.
  * **03. Findings and Proof of Exploitation:** Comprehensive breakdown of each vulnerability with screenshots and evidence across Milestones 1 through 3.
  * **04. Risk Rating:** Categorization of vulnerabilities into Critical, High, Medium, or Low with detailed justifications.
  * **05. Recommendations and Remediation:** Actionable, technical steps the client must take to fix each identified flaw.
* **Milestone Deliverable:** A complete professional penetration testing report submitted for the internship evaluation.

---

## 📊 4. Risk Analysis / Impact
Based on the vulnerabilities identified during the engagement, the following risks were assessed:

| # | Risk / Finding | Evidence / Observation | Potential Impact | Risk Level |
| :--- | :--- | :--- | :--- | :--- |
| **1** | Unauthorized Access to Patient Records | Direct exposure of confidential patient PDF lab reports via application entry points | Severe breach of Protected Health Information (PHI) and regulatory non-compliance | 🔴 **Critical** |
| **2** | Weak File Encryption Implementation | Retrieved files protected with weak passwords or legacy encryption schemes | Confidential healthcare documents easily read once exfiltrated | 🟠 **High** |
| **3** | Critical Server-Side Data Exposure | Administrative files containing staff salaries and shareholder details left exposed | Severe compromise of corporate governance and internal financial privacy | 🔴 **Critical** |

---

## 🛠️ 5. Recommendations and Remediation
Based on the findings from this engagement, the following remediation steps are recommended:
1. **🛡️ Enforce Strict Access Controls:** Implement robust authentication and authorization checks across all web application endpoints to prevent unauthorized file access.
2. **🔐 Upgrade File Encryption Standards:** Secure all sensitive documents with modern, robust cryptographic algorithms and avoid weak user-managed passwords.
3. **📂 Secure Server Configurations:** Conduct thorough reviews of web-accessible directories to ensure administrative backups, salary exports, and shareholder lists are never exposed.
4. **🔥 Deploy Web Application Firewalls (WAF):** Monitor and block abnormal traffic patterns, directory traversal attempts, and unauthorized data retrieval requests.
5. **🔍 Perform Regular Security Assessments:** Schedule routine vulnerability assessments and penetration tests under authorized scopes to proactively identify risks.

---

## 📌 6. Conclusion
During Week 4 of my cybersecurity internship at Networkwalks, I successfully completed a full black-box penetration testing engagement against Mediroza General Hospital. Through the four milestones, I gained practical experience in mapping web application vulnerabilities, extracting and decrypting confidential files, uncovering hidden server-side data exposures, and documenting professional-grade security findings. 

The engagement demonstrated that technical vulnerabilities and misconfigurations can lead to severe data breaches if left unaddressed. Proper risk documentation, clear evidence collection, and actionable remediation strategies are critical components of professional cybersecurity reporting. All testing was conducted strictly within the authorized educational scope.

---

## 📁 7. Evidences Gallery Index

### 🔍 Milestone 1 Evidence
* **Network Enumeration & Scanning:**
  * `nmap_screenshot.png`
  * `nslookup_dig_screenshorts.png`
  * `dnsrecon_screenshot.png`
* **WAF & Target Probing:**
  * `Curl_Wafw00f_screenshots.png`
* **Authentication & Access Bypass:**
  * `Patient_login_screenshot.png`
  * `Lab_Reports_screenshot.png`

### 🔑 Milestone 2 Evidence
* **Password Cracking & Decryption:**
  * `Pdf1_password_screenshot.png`
  * `Pdf2_password_screenshot.png`
  * `Pdf3_password_screenshot.png`
* **Recovered File Contents:**
  * `Patient_report1_screenshot.png`
  * `Patient_report2_screenshot.png`
  * `Patient_report3_screenshot.png`

### 📂 Milestone 3 Evidence
* **Recon & Enumeration Outputs:**
  * `robots.txt.png`
  * `website_old_path.png`
* **Extracted Sensitive Internal Records:**
  * `staffs_info_sql_file.png`
  * `shareholders_info_sql_file.png`

---

## 👩‍💻 Author & Project Information
* **Author:** Neha Maknur
* **Internship Program:** NetworkWalks Cybersecurity Internship (Batch B083)
* **Repository:** GitHub (`CortexNeha`)
