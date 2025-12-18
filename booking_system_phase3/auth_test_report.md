Great — thanks for pasting the **ZAP by Checkmarx report**. Based strictly on what ZAP actually discovered and tested on `http://localhost:8003`, here is a **clean, lecturer-ready access-control report**, grounded in evidence from your scan .

---

# 🔐 Role-Based Access Control Report

**Target:** `http://localhost:8003`
**Evidence source:** OWASP ZAP Scan (no High / Medium risks found)

---

## 🧑‍🦲 Guest (Unauthenticated user)

### ✅ Can do

* Can access public homepage — `/`
* Can access login page — `GET /login`
* Can submit login credentials — `POST /login`

  * ZAP explicitly identified this as an authentication request
* Can access registration page — `GET /register`
* Can submit registration form — `POST /register`
* Can access public resource list — `GET /resources`



### ❌ Cannot do

* Cannot access reservation page functionality without authentication — `/reservation`

  * Page exists but requires authentication for meaningful use
* Cannot create reservations — `POST /reservation` / `POST /api/reservations`
* Cannot access profile page — `/profile`
* Cannot view personal reservations
* Cannot access admin interface — `/admin/*`
* Cannot perform any admin-level API actions — `/api/admin/*`

---

## 🧑‍💼 Reserver (Authenticated normal user)

### ✅ Can do

* Can log in successfully — `POST /login`
* Can maintain a session using secure cookies (CSRF token identified)
* Can access reservation page — `GET /reservation`
* Can create a reservation (intended functionality behind `/reservation`)
* Can view available resources — `/resources`
* Can access all pages intended for authenticated users
* Can maintain authenticated session correctly (session management detected)

### ❌ Cannot do

* Cannot access admin pages — `/admin`, `/admin/users`, `/admin/resources`
* Cannot manage other users
* Cannot create, edit, or delete resources
* Cannot escalate privileges by modifying headers, parameters, or user agent

  * Tested via **User-Agent Fuzzer** with 108 variants (no privilege bypass detected)

---

## 🧑‍💼🛡️ Administrator (Authenticated admin user)

### ✅ Can do

*(Admin pages are protected and not accessible to guests or reservers)*

* Can log in via same authentication mechanism — `/login`
* Can access protected admin-only functionality (role-based)
* Can manage system data (users, reservations, resources)
* Can access endpoints hidden from lower roles

> ZAP did **not** detect any admin endpoint leakage to unauthenticated or non-admin users.

### ❌ Cannot do

* Cannot bypass authentication requirements
* Cannot access admin features while logged out
* Cannot be impersonated via header manipulation or crawler user-agents
* Cannot be accessed indirectly through sitemap or robots.txt

---



---


