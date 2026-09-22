# Grand Crown security hardening

This build adds baseline application security controls for deployment.

- HTTP security headers: CSP, HSTS in production, X-Content-Type-Options, X-Frame-Options, Referrer-Policy and Permissions-Policy.
- HttpOnly/SameSite cookies; Secure is enabled when running over HTTPS/production.
- Session expiry after 12 hours and expired-session cleanup.
- Login rate limiting to reduce brute-force attempts.
- Same-origin checks for state-changing requests to reduce CSRF risk.
- Request-body limit of 100 KB.
- Production startup refuses the insecure default admin password and requires `ADMIN_USER` and `ADMIN_PASS` environment variables.
- Passwords are stored using Node.js `scrypt` hashing rather than plaintext.
- Admin password comparison uses constant-time comparison.
- Payment transaction IDs and phone numbers receive format validation.

## Important

No web application can be guaranteed to be impossible to hack. Before real-money production use, also use HTTPS, a persistent database with backups, least-privilege hosting credentials, secret rotation, monitoring/audit logs, dependency updates, and a professional security review. Do not store or publish payment-provider credentials in source code.
