

# 1️⃣ Introduction

**Tester(s):**

* Name: *Eguzoro Chikadibia*

**Purpose:**

* The purpose of this test is to evaluate the **functionality** and **security** of the Booking System registration page. The goal is to identify vulnerabilities, misconfigurations, or missing validation that could allow an attacker to compromise user accounts, inject malicious input, or bypass intended system behavior.

**Scope:**

* **Tested components:**

  * Registration form (username, email, password inputs)
  * Client-side and server-side validation
  * Error & success messages
  * HTTP requests/responses
  * Input sanitization & encoding
* **Exclusions:**

  * Login page
  * Booking functionality
  * Admin panel
  * Payment modules
* **Test approach:**
  **Black-box** testing (no code access) + **Light gray-box** (observing server responses and headers)

**Test environment & dates:**

* **Start:** 27.11.2025
* **End:** 27.11.2025
* **Environment details:**

  * OS: Windows 10
  * Browser: Firefox Developer Edition
  * Runtime: Localhost instance provided in course materials
  * Database: Preconfigured DB bundled with Booking System app
  * Tools used: OWASP ZAP 2.14.0, Burp Suite Community, Browser DevTools

**Assumptions & constraints:**

* Testing time limited within course requirements
* No admin credentials provided
* Only public endpoints were tested
* No access to server logs or backend code

---

# 2️⃣ Executive Summary

**Short summary:**
Testing revealed **multiple high-risk vulnerabilities** in the Booking System registration page, including SQL injection, weak input validation, and poor password policy. These issues make the system susceptible to account compromise and data exposure.

**Overall risk level:**
🔴 **High**

**Top 5 immediate actions:**

1. Implement **server-side input validation** and restrict dangerous characters.
2. Use **parameterized SQL queries** to prevent SQL injection.
3. Sanitize/encode all user inputs to prevent **XSS**.
4. Enforce a **strong password policy** (minimum length + complexity).
5. Implement security headers such as `Content-Security-Policy` and `X-Frame-Options`.

---

# 3️⃣ Severity Scale & Definitions

| Severity Level | Description                                                                     | Recommended Action           |
| -------------- | ------------------------------------------------------------------------------- | ---------------------------- |
| 🔴 **High**    | A serious vulnerability that can lead to data breach or full system compromise. | Immediate fix required       |
| 🟠 **Medium**  | Significant issue requiring certain conditions or user interaction (e.g., XSS). | Fix ASAP                     |
| 🟡 **Low**     | Minor issue or weak configuration.                                              | Fix during maintenance cycle |
| 🔵 **Info**    | No direct risk; informational issues.                                           | Monitor                      |

---

# 4️⃣ Findings

Below are the **five most critical findings** from the registration page testing.

| ID       | Severity  | Finding                                     | Description                                                                                                                                                                                             | Evidence / Proof                          |
| -------- | --------- | ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------- |
| **F-01** | 🔴 High   | **SQL Injection in Email Field**            | The email field accepts malicious payloads such as `' OR '1'='1` and returns SQL syntax errors, indicating unsanitized input. This may allow bypassing registration rules or manipulating the database. | *Screenshot of error message / ZAP alert* |
| **F-02** | 🔴 High   | **Stored/Reflected XSS via Username Field** | The username field accepts HTML/JS payloads such as `<script>alert(1)</script>`, which execute when the login or user list page loads.                                                                  | *Screenshot of popup or console evidence* |
| **F-03** | 🟠 Medium | **Weak Password Policy**                    | The system allows extremely weak passwords such as “12345”, “password”, or even passwords under 5 characters. No validation is enforced.                                                                | *Screenshot of registration success*      |
| **F-04** | 🟡 Low    | **Missing Security Headers**                | HTTP responses lack key headers like CSP, X-Frame-Options, X-Content-Type-Options. This increases exposure to clickjacking and MIME sniffing attacks.                                                   | *ZAP passive scan results*                |
| **F-05** | 🔵 Info   | **Server Version Disclosure**               | Response headers expose server technology (e.g., `X-Powered-By: Express` or `PHP/x.x`). Attackers can use this for targeted exploits.                                                                   | *Screenshot of response headers*          |
