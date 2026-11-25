# 🛍️ PASTA Threat Model: Sneaker Marketplace Mobile App

## 📌 Scenario Overview

I am a cybersecurity trainee working as part of the growing security team at a company for sneaker enthusiasts and collectors. The business is preparing to launch a mobile app that makes it easy for customers to buy and sell shoes. Before launch, I performed a threat model of the application using the **Process of Attack Simulation and Threat Analysis (PASTA)** framework to decide whether the app is safe to release.

The company's goals for the app are:

- Seamlessly connect sellers and shoppers
- Make it easy to sign up, log in, and manage accounts
- Protect user data privacy so customers feel confident in how their information is handled
- Let buyers message sellers directly and rate them to encourage good service
- Process sales quickly with several payment options
- Handle payments properly to avoid legal issues

I went through all seven stages of PASTA to identify the security requirements for the app.

---

## 🎯 Stage I: Define Business and Security Objectives

I identified three business requirements that shape the security analysis:

- Users can create member profiles internally or by connecting external accounts.
- The app must process financial transactions.
- The app should be in compliance with PCI-DSS.

These requirements matter because the app will store personal information and handle payment data, so a weak design could lead to data theft and legal consequences.

---

## 🧰 Stage II: Define the Technical Scope

The technologies used by the application are:

- Application Programming Interface (API)
- Public Key Infrastructure (PKI)
- Advanced Encryption Standard (AES)
- SHA-256
- SQL

APIs should be prioritized in the analysis. They exchange data between customers, partners, and employees, and they handle a lot of sensitive information while connecting various users and systems together. Because of this, they have a larger attack surface and can be more prone to vulnerabilities. Details such as which APIs are being used should also be considered before prioritizing one technology over another.

---

## 🧩 Stage III: Decompose the Application

### Data Flow Diagram
<img width="1093" height="523" alt="data-flow-diagram" src="https://github.com/user-attachments/assets/da49bde5-add8-4374-859c-b593f79414ba" />
*Completed using the data flow diagram template provided by Google.*

**Key Observations**

- The diagram shows a single process: **product search**.
- A user searches for sneakers for sale, and the application returns listings of current inventory.
- Data flows between the user, the search process, and the inventory data, which shows where the app handles and exchanges information.
- Real applications have much more complex data flow diagrams, but mapping even one process helps reveal where an attacker could interfere.

---

## ⚠️ Stage IV: Threat Analysis

I identified two threats that put the information handled by the application at risk:

- **Injection:** An attacker inserts malicious code or commands into an input field, such as the search bar or login form, to make the application run unintended actions or expose data.
- **Session hijacking:** An attacker takes over a legitimate user's active session and acts as that user, which could expose account details or allow fraudulent purchases.

---

## 🔓 Stage V: Vulnerability Analysis

I identified two vulnerabilities that could be exploited by the threats above:

- **Lack of prepared statements:** If database queries are built directly from user input, an attacker can use injection to read or change data in the database.
- **Broken API token:** If API tokens are poorly generated, stored, or validated, an attacker can steal or forge them to access the app as another user.

---

## 🌳 Stage VI: Attack Modeling

### Attack Tree
<img width="911" height="515" alt="attack-tree" src="https://github.com/user-attachments/assets/ac86cfc3-a87b-4ce7-96a9-fcc84525f126" />
*Completed using the attack tree template provided by Google.*

**Key Observations**

- The goal at the top of the tree is access to **user data**.
- One branch shows **SQL injection**, which becomes possible because of the **lack of prepared statements**.
- A second branch shows **session hijacking**, which becomes possible because of **weak login credentials**.
- Attack trees help show the different paths an attacker could take, so the security team can decide where to place controls. Real applications usually have many more branches.

---

## 🛡️ Stage VII: Risk Analysis and Impact

I recommended four security controls to reduce the risk:

- **SHA-256:** Hashing sensitive data such as passwords means stolen data is not readable in plain form.
- **Incident response procedures:** A documented plan lets the team detect, contain, and recover from an attack quickly.
- **Password policy:** Requiring strong, unique passwords reduces the chance of weak login credentials being guessed or cracked.
- **Principle of least privilege:** Giving users and systems only the access they need limits the damage if an account is compromised.

---

## 📝 Conclusion

Through this activity I learned how PASTA moves from business goals down to specific attack paths and controls. The biggest risks I found were injection and session hijacking, both tied to how the app handles user input and authentication. With the recommended controls in place, such as prepared statements, strong API token handling, and a solid password policy, the app can be launched with a much lower risk to user and payment data.

---

## 📂 Files in This Repository

- `PASTA_Worksheet.docx`: my completed PASTA worksheet
- `data-flow-diagram.png`: data flow diagram for the product search process
- `attack-tree.png`: attack tree for SQL injection and session hijacking

---

## 🧠 Skills Demonstrated

- Threat modeling with the PASTA framework
- Data flow diagramming and attack tree creation
- Identifying threats and vulnerabilities in application security
- Recommending security controls aligned with business and compliance needs (PCI-DSS)

*Completed as part of the Google Cybersecurity Professional Certificate.*
