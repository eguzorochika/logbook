1️⃣ Introduction

Tester(s):

Name: Eguzoro Chikadibia

Purpose:

The purpose of this test is to identify security vulnerabilities and functional issues in the Booking System registration page, focusing on insecure input handling, broken validation, and missing security controls.

Scope:

Tested components:

Registration page UI

Registration POST request

Input validation (email, username, password)

Response messages & error handling

Server behavior under malformed inputs

Security checks via OWASP ZAP (Round 1)

Exclusions:

Login page

Reservation system

Admin interface

Payment or resource booking functionality

Test approach:

Black-box (form inputs, UI testing)

Gray-box (observing server responses, analyzing devtools headers)

Automated scanning with OWASP ZAP

Test environment & dates:

Start: 27.11.2025

End: 27.11.2025

Environment:

OS: Windows 10

Browser: Firefox Developer Edition

Runtime: Docker (cybersec-phase1-part1 images)

DB: Preconfigured PostgreSQL

Tools: OWASP ZAP 2.16.1, Browser DevTools

Assumptions & constraints:

Default system credentials not provided

Only publicly accessible endpoints were tested

Strict time limit (course requirement)

No backend code access

2️⃣ Executive Summary

Testing revealed multiple high-risk security issues in the registration endpoint.
OWASP ZAP detected SQL Injection and Path Traversal, indicating poor input handling and missing sanitization.
Several security headers were also missing.

Overall risk level: 🔴 HIGH

Top 5 immediate actions:

Implement prepared statements to prevent SQL Injection

Sanitize & validate all user inputs on the server side

Implement CSRF protection

Add missing security headers (CSP, X-Frame-Options, X-Content-Type-Options)

Fix path traversal risk by restricting file system access

3️⃣ Severity scale & definitions
Severity Level	Description	Recommended Action
🔴 High	Vulnerabilities enabling data breach or full system compromise	Immediate fix required
🟠 Medium	Issues requiring user action or specific conditions	Fix ASAP
🟡 Low	Weak configurations or minor exposure	Fix during maintenance
🔵 Info	No direct risk; informational	Monitor
4️⃣ Findings
ID	Severity	Finding	Description	Evidence
F-01	🔴 High	SQL Injection in /register	ZAP detected SQL Injection patterns in POST /register, causing 500 errors, meaning server is processing unsafe SQL inputs.	ZAP alert (Round 1)
F-02	🔴 High	Path Traversal	ZAP flagged path traversal risk on registration endpoint, meaning user input may influence file paths.	ZAP alert (Round 1)
F-03	🟠 Medium	Missing Anti-CSRF tokens	The registration form does not contain CSRF tokens; ZAP flagged this.	ZAP Passive Scan
F-04	🟡 Low	Missing security headers	CSP, X-Frame-Options, and X-Content-Type-Options headers are absent.	Browser DevTools / ZAP
F-05	🔵 Info	Weak error handling	Application displays raw error messages such as “Error during registration”.	Manual testing
5️⃣ OWASP ZAP Test Report (Attachment)

Purpose:
This report includes all ZAP scan alerts for Phase 1, including SQL Injection, Path Traversal, and missing security headers.

Attached file:
➡️ zap_report_round1.md

Stored in:

logbook/booking_system_phase1/zap_report_round1.md

6️⃣ Attachments

ZAP Alerts Screenshot

ZAP Scan Logs

Registration error screenshots
(Already included as PNG files in repo)