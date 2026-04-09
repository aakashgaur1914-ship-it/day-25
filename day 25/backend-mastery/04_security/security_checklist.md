# Module 4: API Security Checklist & Deep Dive

Security is not a feature; it's a foundational requirement. For APIs, the attack surface is vast and requires a multi-layered defense strategy.

## 1. OWASP Top 10 for APIs (2023/2026 Core)
1.  **Broken Object Level Authorization (BOLA)**: Manipulating IDs in the URL to access other users' data.
2.  **Broken Authentication**: Weak token management or lack of rate limiting on login.
3.  **Broken Object Property Level Authorization**: Accessing or modifying internal fields (e.g., `isAdmin`).
4.  **Unrestricted Resource Consumption**: Lack of rate limits leads to DoS.
5.  **Broken Function Level Authorization**: Accessing administrative endpoints as a regular user.
6.  **Unrestricted Access to Sensitive Business Logic**: Exploiting logic flows (e.g., bypassing a payment step).
7.  **Server-Side Request Forgery (SSRF)**: Tricking the server into making requests to internal resources.
8.  **Security Misconfiguration**: Default passwords, improper CORS headers.
9.  **Improper Inventory Management**: Leaving old API versions (v1, v2) exposed and unpatched.
10. **Unsafe Consumption of APIs**: Trusting data returned from third-party APIs without validation.

## 2. API Security Best Practices
- **Use OAuth2 and OpenID Connect (OIDC)** for modern authentication.
- **Implement Fine-Grained RBAC (Role-Based Access Control)**.
- **Always Validate and Sanitize Input** (Use JSON schema validation).
- **Encrypt Data in Transit (TLS 1.3)** and **At Rest (AES-256)**.
- **Use Secure Headers**: `Content-Security-Policy`, `X-Content-Type-Options`, `Strict-Transport-Security`.
- **Rate Limiting & Throttling**: Protect against brute force and DDoS.

## 3. Zero Trust Architecture
The "Never Trust, Always Verify" principle.
- **Identity-Centric**: Every request must be authenticated, regardless of network origin.
- **Micro-Segmentation**: Services can only talk to specific other services they need.
- **Least Privilege**: Users and services have the minimum permissions required.

## 4. Secret Management
Never hardcode secrets (API keys, DB passwords).
- **Tools**: HashiCorp Vault, AWS Secrets Manager, Azure Key Vault.
- **Rotational Policy**: Automatically rotate secrets every 30-90 days.

## 5. Penetration Testing Basics
- **Dynamic Analysis (DAST)**: Testing the running application for vulnerabilities.
- **Static Analysis (SAST)**: Scanning source code for security flaws.
- **Fuzzing**: Sending massive amounts of random data to endpoints to find crashes or leaks.
- **Tools**: OWASP ZAP, Burp Suite, Postman (for manual testing).

---

## 6. Security Checklist for Every Deployment
- [ ] Are all endpoints behind authentication (except public ones)?
- [ ] Is rate limiting enabled for all routes?
- [ ] Have you implemented BOLA/BOPA checks?
- [ ] Are secrets managed outside the codebase?
- [ ] Is logging enabled for security events (failed logins, 403 errors)?
- [ ] Is TLS correctly configured?
