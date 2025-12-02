# Test Report – Booking System (Phase 1 / Part 2 Verification)

Tester: Eguzoro Chikadibia  
Date: 2025-12-XX  
Application URL: `http://localhost:8001`  

---

## Round 2 – Verification of Top 5 Findings (From Phase 1 / Part 1)

| # | Finding (Round 1) | Round 2 Test Steps | Observed Result | Status |
|---|-------------------|--------------------|-----------------|--------|
| F-01 | SQL Injection in Email Field | 1. Open Registration page. 2. Enter `' OR 1=1--` or `test@example.com'`. 3. Submit. | *Fill after testing* | Fixed / Not fixed |
| F-02 | Stored/Reflected XSS in Username Field | 1. Register username `<script>alert(1)</script>`. 2. Login or view profile/user list. | *Fill after testing* | Fixed / Not fixed |
| F-03 | Weak Password Policy | 1. Try weak passwords (`12345`, `password`). 2. Observe if accepted or rejected. | *Fill after testing* | Fixed / Not fixed |
| F-04 | Missing Security Headers | Inspect response headers in DevTools → Network. | *Fill after testing* | Fixed / Not fixed |
| F-05 | Server Version Disclosure | Inspect headers for `X-Powered-By` or server info. | *Fill after testing* | Fixed / Not fixed |

---

## Notes:
Round 2 testing was performed after deploying the updated application using Docker Compose in Phase 1 / Part 2. The purpose was to verify if the original high-risk vulnerabilities have been fixed.
