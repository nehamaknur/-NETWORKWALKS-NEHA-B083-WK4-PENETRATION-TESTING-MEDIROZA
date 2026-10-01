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
| **📅 Date** | 16 September 2026 |
| **📂 Modules Completed** | Week 4: Mediroza General Hospital Penetration Test (Milestones 1 to 4) |
| **🎯 Client/Target** | `https://medirozahospital.com` (written permission secured) |
| **✍️ Permission Secured?** | ✅ Yes |
| **🔍 Scope & Objective** | Full black-box pentest. Identify vulnerabilities, exploit for real impact, and report. |

---

## ⚠️ 1. Liability Disclaimer
> I have performed these activities only on the systems & devices where I had secured written permission or the devices/systems that I own myself. All these materials are for education and research purpose only. Do not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorised access is a crime even when nothing is damaged.

---

## 🚀 2. Introduction
This report covers the penetration testing engagement conducted against Mediroza General Hospital (`https://medirozahospital.com`) during Week 4 of my ongoing cybersecurity internship program at Networkwalks. The assessment followed a full black-box methodology across four progressive milestones—ranging from initial reconnaissance and access control bypass, through cryptographic password cracking, to uncovering critical server-side internal data exposures (such as staff salaries and shareholder records).

---
# Project Milestones & Security Disclaimer

> **Disclaimer:** This documentation and all associated activities are strictly intended for educational and defensive security research purposes. All testing was conducted exclusively on authorized environments or systems with explicit permission. The author assumes full personal responsibility for all actions taken and disclaims any liability for misuse. This knowledge must never be used for unauthorized access, malicious activities, or illegal operations.
> 
| Milestone | Objective & Methodology | Discovery & Outcomes |
| :--- | :--- | :--- |
| **M1** | Initial access, reconnaissance, and vulnerability scoping. | Open ports, exposed services, attack surface mapping, and potential entry vectors. |
| **M2** | Data extraction and cryptographic hash cracking. | Extracted user records, database structures, and cracked plaintext credentials from hashes. |
| **M3** | Identification and documentation of critical internal data exposure. | Sensitive patient or internal administrative files, misconfigured shares, and privilege escalation paths. |
| **M4** | Compilation of findings into professional reporting and mitigation summaries. | Comprehensive risk breakdown, executive summaries, and actionable remediation steps. |

---

## 🛠️ 3. Tools & Technologies Used

| Tool / Technique | Purpose / Function |
| :--- | :--- |
| **💻 Kali Linux / Virtual Environment** | Isolated operating system environment utilized for security tooling, command-line operations, and safe lab execution. |
| **🌐 Web Browser / Recon Tools** | Surface mapping and initial access discovery against the target domain. |
| **🔑 Password Recovery Utilities** | Brute-forcing and cracking encryption on retrieved confidential PDF files. |
| **📁 Metadata & Property Analysis** | Deep inspection of file properties and hidden server directories to uncover sensitive internal data. |
| **📝 Reporting Frameworks** | Documenting findings, risk ratings, and actionable remediation guidelines. |

---

## ⚙️ 4. Activities Performed
The assessment was executed independently, structured around four core milestones:

* **🔓 Milestone 1 (Initial Access & Reconnaissance):** Attacked the target web application, analyzed access control mechanisms, and successfully retrieved 3 confidential patient PDF lab reports. Written permission was verified prior to testing.
* **🔑 Milestone 2 (Data Extraction & Cryptographic Cracking):** Analyzed the encryption protecting the 3 retrieved files and applied appropriate tools and wordlists to crack the encryption and recover readable contents.
* **📂 Milestone 3 (Critical Data Exposure):** Conducted a thorough examination of retrieved file properties and hidden server vectors, uncovering critical internal records including hospital staff salaries and shareholder details.
* **📊 Milestone 4 (Professional Reporting):** Compiled a structured penetration testing report detailing the executive summary, scope, technical findings, risk ratings, and remediation recommendations.

---

## 📊 5. Risk Analysis / Impact
Based on the vulnerabilities identified during the engagement, the following risks were assessed:

| # | Risk / Finding | Evidence / Observation | Potential Impact | Risk Level |
| :--- | :--- | :--- | :--- | :--- |
| **1** | Unauthorized Access to Patient Records | Direct exposure of confidential patient PDF lab reports via application entry points | Severe breach of Protected Health Information (PHI) and regulatory non-compliance | 🔴 **Critical** |
| **2** | Weak File Encryption Implementation | Retrieved files protected with weak passwords or legacy encryption schemes | Confidential healthcare documents easily read once exfiltrated | 🟠 **High** |
| **3** | Critical Server-Side Data Exposure | Administrative files containing staff salaries and shareholder details left exposed | Severe compromise of corporate governance and internal financial privacy | 🔴 **Critical** |

---

## 🛠️ 6. Recommendations and Remediation
Based on the findings from this engagement, the following remediation steps are recommended:
1. **🛡️ Enforce Strict Access Controls:** Implement robust authentication and authorization checks across all web application endpoints to prevent unauthorized file access.
2. **🔐 Upgrade File Encryption Standards:** Secure all sensitive documents with modern, robust cryptographic algorithms and avoid weak user-managed passwords.
3. **📂 Secure Server Configurations:** Conduct thorough reviews of web-accessible directories to ensure administrative backups, salary exports, and shareholder lists are never exposed.
4. **🔥 Deploy Web Application Firewalls (WAF):** Monitor and block abnormal traffic patterns, directory traversal attempts, and unauthorized data retrieval requests.
5. **🔍 Perform Regular Security Assessments:** Schedule routine vulnerability assessments and penetration tests under authorized scopes to proactively identify risks.

---

## 📌 7. Conclusion
During Week 4 of my cybersecurity internship at Networkwalks, I successfully completed a full black-box penetration testing engagement against Mediroza General Hospital. Through the four milestones, I gained practical experience in mapping web application vulnerabilities, extracting and decrypting confidential files, uncovering hidden server-side data exposures, and documenting professional-grade security findings. 

The engagement demonstrated that technical vulnerabilities and misconfigurations can lead to severe data breaches if left unaddressed. Proper risk documentation, clear evidence collection, and actionable remediation strategies are critical components of professional cybersecurity reporting. All testing was conducted strictly within the authorized educational scope.

---

## 📁 8. Evidences Collected
*(Placeholder for screenshots demonstrating milestone progression, successful access bypass, file decryption outputs, and discovered internal records as required by the practical task deliverables).*

---

## 👩‍💻 Author & Project Information
* **Author:** Neha Maknur
* **Internship Program:** NetworkWalks Cybersecurity Internship (Batch B083)
* **Repository:** GitHub (`CortexNeha`)
