# 🛡️ Security Best Practices & Defensive Engineering

Security is a primary design constraint, not an afterthought. This document outlines the defensive principles adhered to across all repositories and applications in this ecosystem.

---

## 🔐 1. Cryptographic Key Management

- **No Hardcoded Secrets:** Cryptographic keys must never be embedded in source code, commit history, or configuration files tracked by version control.
- **Local Generation:** Applications generate secret keys dynamically at runtime (`secret.key`) on the host system.
- **Access Controls:** Restrict read and write permissions to the owning process or user.
- **Safe Algorithms:** Rely exclusively on standardized, peer-reviewed implementations (e.g., Fernet for authenticated symmetric encryption; Ed25519 for signatures). Avoid homemade rolling cipher algorithms.

---

## 🛡️ 2. Input Validation & Error Boundaries

- **Never Trust Input:** Sanitize and validate all user inputs before processing or passing to system routines.
- **Boundary Checking:** Verify string lengths, file formats, and buffer limits to prevent memory overflow or abnormal resource exhaustion.
- **Defensive Exceptions:** Catch specific exceptions (e.g. `InvalidToken` from Fernet) and present user-friendly error messages without leaking stack traces or internal memory addresses.

---

## 🌐 3. Safe Web Data Extraction

- **Robots & Terms Compliance:** Respect web server rate limits and structural guidelines.
- **Timeout Configuration:** Always specify explicit timeout values in network calls (`requests.get(url, timeout=10)`) to prevent hang attacks or denial of service.
- **Status Code Verification:** Inspect HTTP status codes (`response.raise_for_status()`) before parsing DOM structures.

---

## 📋 4. Responsible Disclosure

For any discovered security vulnerabilities, follow the procedures detailed in [SECURITY.md](https://github.com/Manshi-Chauhan/Manshi-Chauhan/blob/main/SECURITY.md) and report directly to `manshichauhan923@gmail.com`.
