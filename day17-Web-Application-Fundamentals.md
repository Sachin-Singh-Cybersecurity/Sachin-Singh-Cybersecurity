# Day 17 – Web Application Fundamentals (December 30, 2025)

**Week:** 3 · **Day:** 17  
**Focus:** HTTP, Web Basics & Burp Suite Practice  
**Total Time:** 4.75 hours  

---

## Overview

- Built a solid foundation in how web apps communicate over HTTP/HTTPS.  
- Learned how browsers and servers exchange requests and responses.  
- Practiced intercepting and modifying traffic using Burp Suite.  

---

## HTTP Concepts Covered

### Request–Response Model

- HTTP is stateless; each request is independent.  
- Typical flow:
  1. DNS lookup and TCP/TLS handshake.
  2. Browser sends HTTP request (method + path + headers + optional body).
  3. Server responds with status code, headers, and body.
  4. Browser parses HTML and issues more requests for CSS/JS/images.  

### Core HTTP Methods

- **GET** – Retrieve data, no body, should not change server state, cacheable.  
- **POST** – Create/submit data, body used, not idempotent, used for forms and logins.  
- **PUT** – Replace a resource completely, idempotent.  
- **DELETE** – Remove a resource, idempotent.  
- **PATCH** – Partially update a resource, commonly used in modern APIs.  

Key rules:
- Avoid putting sensitive data (passwords, tokens) in GET URLs.  
- Use POST/PUT/PATCH bodies plus HTTPS for sensitive operations.

### Important Request Headers

- `Host` – Which virtual host/domain the request targets (mandatory in HTTP/1.1).  
- `User-Agent` – Client identifier; useful for analytics, not for security.  
- `Content-Type` – Media type of the body (JSON, form‑urlencoded, multipart).  
- `Authorization` – Credentials (Basic, Bearer tokens, etc.), must go over HTTPS.  
- `Cookie` – Sends browser‑stored cookies to the server.  
- `Accept` / `Accept-Language` – Client’s preferred formats and languages.  

### Important Response Headers

- `Content-Type` – How the browser should interpret the body (HTML, JSON, etc.).  
- `Set-Cookie` – Instructs browser to store a cookie (session IDs, preferences).  
- `Cache-Control` – Caching behavior (max‑age, no-store, private/public).  
- `Location` – Used with 3xx redirects.  
- Security‑related:
  - `Access-Control-Allow-Origin` (CORS).  
  - `Strict-Transport-Security` (HSTS).  
  - `X-Frame-Options` / `Content-Security-Policy` / `X-Content-Type-Options`.  

---

## State, Cookies & Sessions

### Why State Is Needed

- HTTP itself has no memory of users.  
- After login, the server must recognize which subsequent requests belong to that user.  

### How Cookies Work

- Server sends:  
  `Set-Cookie: sessionid=abc123; Path=/; Secure; HttpOnly; SameSite=Strict`  
- Browser stores and sends back:  
  `Cookie: sessionid=abc123` on future requests.  

Important flags:
- **Secure** – Only send over HTTPS.  
- **HttpOnly** – Not accessible to JavaScript (protects against XSS stealing cookies).  
- **SameSite** – Controls cross‑site cookie sending, mitigates CSRF.  

### Session Approaches

- **Server‑side sessions:**
  - Server keeps session data; cookie holds only a random ID.
  - Easy to revoke and rotate, but needs server/state storage.  

- **Token‑based (e.g., JWT):**
  - Encoded and signed data stored client‑side.
  - Scales well; revocation and long expiries must be handled carefully.

---

## Browser Security: Origin & CORS

### Same‑Origin Policy (SOP)

- Two URLs are same origin only if **scheme + domain + port** all match.  
- Prevents a malicious site from reading data from another origin in the browser.  
- Critical protection for cookies, DOM access, and most sensitive APIs.

### CORS (Cross‑Origin Resource Sharing)

- Mechanism to *selectively* allow cross‑origin requests.  
- Browser may send a preflight `OPTIONS` request with `Origin` and requested method/headers.  
- Server replies with:
  - `Access-Control-Allow-Origin`
  - `Access-Control-Allow-Methods`
  - `Access-Control-Allow-Headers`
  - `Access-Control-Allow-Credentials` (for cookies/auth)  

Misconfigurations:
- `Access-Control-Allow-Origin: *` combined with credentials is dangerous.  
- Allowing untrusted origins leaks sensitive API data to arbitrary sites.

---

## Practical Labs (Burp Suite)

### Lab 1 – Intercept & Inspect HTTP Traffic

- Configured browser (Firefox) to proxy through Burp at `127.0.0.1:8080`.  
- Installed Burp’s CA certificate to inspect HTTPS traffic.  
- Intercepted:
  - Basic page loads (GET /).  
  - A login form POST and examined:
    - Method, headers, and body parameters.
    - How credentials appear when not using HTTPS.  

**Outcome:**  
Gained comfort reading raw HTTP flows and clearly seeing what data is exposed on the wire.

### Lab 2 – Modify & Replay Requests (Repeater)

- Captured an API request like `GET /api/users/123`.  
- Used Repeater to:
  - Change IDs to access other users → demonstrates IDOR risk.  
  - Modify cookies (e.g., `userid=123` → `userid=42`) to impersonate another user.  
  - Tweak headers (e.g., User-Agent, custom headers) to illustrate how client‑side checks can be bypassed.  

**Outcome:**  
Understood how trivial it is for an attacker to change any part of a request and why backend authorization is essential.

### Lab 3 – Cookie & Session Analysis

- Inspected `Set-Cookie` headers for:
  - Presence/absence of `Secure`, `HttpOnly`, `SameSite`.  
  - How session IDs look (random vs predictable).  
- Explored session fixation concepts:
  - Reusing a known session ID through login flow.  

**Outcome:**  
Saw how weak cookie settings and predictable sessions enable hijacking and CSRF.

### Lab 4 – CORS Testing

- Sent requests with custom `Origin` headers using curl/Burp.  
- Checked server responses for:
  - `Access-Control-Allow-Origin` (`*`, specific domain, `null`).  
  - `Access-Control-Allow-Credentials`.  
- Identified patterns of overly permissive CORS policies.

**Outcome:**  
Learned how to quickly spot CORS misconfigurations that leak data cross‑origin.

### Lab 5 – Vulnerability Hunting on Practice Apps

- Used deliberately vulnerable apps (DVWA, WebGoat, Juice Shop) to:  
  - Find information disclosure in headers and error messages.  
  - Test for IDOR by changing IDs in paths/parameters.  
  - Observe where authentication or authorization is missing.  

**Outcome:**  
Connected theory to real exploit patterns seen in actual web apps.

---

## Key Learnings – Day 17

- Can read and reason about raw HTTP requests and responses.  
- Understand when and how to use each HTTP method correctly.  
- Know which headers are security‑sensitive and how to configure them.  
- Appreciate the importance of cookies, sessions, and their secure configuration.  
- See how SOP and CORS form the browser’s primary defense line.  
- Comfortable using Burp Suite for basic interception and request manipulation.  
- Recognize common web vulns: IDOR, weak sessions, bad CORS, plaintext credentials.

---

## Progress Snapshot

- Total cumulative hours: **99.25 / 560** (~17.7%).  
- Still significantly **ahead of the planned schedule** going into the next module (OWASP Top 10).
