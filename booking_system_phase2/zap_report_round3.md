# ZAP Report – Round 3 (Phase 2)

## Target
- URL: http://localhost:8002
- Date: 17.12.2025
- Tester: Chikadibia Eguzoro

## Tool Used
OWASP ZAP Desktop (Automated Scan)

## Scan Method
An automated scan was performed using OWASP ZAP Desktop. The scan used the traditional spider and AJAX spider to discover application endpoints and passive vulnerability detection to identify security issues.

## Results Summary
| Risk Level | Count |
|-----------|------:|
| High      | 0 |
| Medium    | 0 |
| Low       | 1 |
| Informational | 3 |

## Key Findings
1. **Absence of Anti-CSRF Tokens** (Low)  
   Some forms do not include Anti-CSRF tokens, which could allow cross-site request forgery attacks.

2. **ZAP is Out of Date** (Informational)  
   The tool reports that the current ZAP version is not the latest.

3. **Authentication Request Identified** (Informational)  
   Authentication-related requests were detected during the scan.

4. **User Agent Fuzzer** (Informational)  
   User-Agent header variations were tested to identify potential inconsistencies.

## Comparison with Previous Rounds
- Fixed since Round 2:
  - Improved authentication handling
  - No SQL injection vulnerabilities detected
- Still present:
  - Missing Anti-CSRF protection
- New findings:
  - No new significant vulnerabilities identified

## Conclusion
The Phase 2 version of the Booking System shows improved security compared to previous testing rounds. No high or medium risk vulnerabilities were found. The remaining issues are low-risk or informational and primarily related to missing CSRF protection and tool configuration warnings.
