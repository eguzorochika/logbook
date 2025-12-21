# GDPR Compliance Checklist – Web-based Booking System

## Personal data mapping and minimization

| Check | Result | Notes |
|------|--------|-------|
| All personal data identified (name, email, age, username) | ✅ | Data collected during registration is limited and clearly identifiable |
| Data minimization applied | ✅ | Only essential data required for booking and authentication is collected |
| User age recorded to verify over 15 | ✅ | Age verification is implemented to restrict underage bookings |

---

## User registration and management

| Check | Result | Notes |
|------|--------|-------|
| GDPR-compliant consent during registration | ⚠️ | Privacy policy exists but explicit consent checkbox should be clearly visible |
| Admin can delete reserver (Right to be Forgotten) | ✅ | Administrator role supports deleting users |
| Underage registration and booking restricted | ✅ | Booking restricted to users over 15 |

---

## Booking visibility

| Check | Result | Notes |
|------|--------|-------|
| Public bookings shown without personal data | ✅ | Only resource and time information is visible |
| No personal data exposed publicly | ✅ | Names and emails are not displayed |

---

## Access control and authorization

| Check | Result | Notes |
|------|--------|-------|
| Only admins can manage resources and bookings | ✅ | Role-based access enforced |
| Role-based access control implemented | ✅ | Reserver and Administrator roles exist |
| Admin privileges limited for GDPR purposes | ⚠️ | No technical misuse observed, but policy guidance recommended |

---

## Privacy by Design principles

| Check | Result | Notes |
|------|--------|-------|
| Privacy by Default implemented | ✅ | Minimal data collected by default |
| Logs avoid unnecessary personal data | ⚠️ | Logging exists; log minimization should be documented |
| Secure and minimal forms | ✅ | Login and registration forms are protected with CSRF tokens |

---

## Data security

| Check | Result | Notes |
|------|--------|-------|
| CSRF, XSS, SQLi protections | ✅ | CSRF tokens detected in ZAP scan |
| Passwords securely hashed | ✅ | Industry-standard hashing used |
| GDPR-compliant backups | ⚠️ | Backup process not documented |
| Data stored within EU | ⚠️ | Hosting location not explicitly documented |

---

## Data anonymization and pseudonymization

| Check | Result | Notes |
|------|--------|-------|
| Data anonymized where possible | ✅ | Public views anonymize users |
| Pseudonymization applied | ⚠️ | Internal identifiers used but not explicitly documented |

---

## Data subject rights

| Check | Result | Notes |
|------|--------|-------|
| Users can request their personal data | ⚠️ | Manual request process required |
| Users can request deletion | ✅ | Admin-supported deletion exists |
| Users can withdraw consent | ⚠️ | Withdrawal possible via account deletion |

---

## Documentation and communication

| Check | Result | Notes |
|------|--------|-------|
| Privacy policy available and accessible | ✅ | Available via `/privacypolicy` |
| Documented data protection practices | ⚠️ | Internal documentation recommended |
| Data breach response process documented | ⚠️ | Not yet formally documented |

---

### Symbols used
- ✅ Pass  
- ❌ Fail  
- ⚠️ Attention / Improvement recommended
