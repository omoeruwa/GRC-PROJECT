# Phase 2: Asset Inventory

### Overview
Before we can secure the system, we must identify what we are actually protecting. In the context of the Vuln-Bank platform, we define "Assets" as any data, hardware, or software component that, if compromised, would cause financial loss, reputational damage, or regulatory failure.

### Critical Assets Inventory

| Asset ID | Asset Name | Description | Data Classification | App Component |
| :--- | :--- | :--- | :--- | :--- |
| **AST-01** | User Database | Names, Emails, Passwords, and Wallet balances. | Restricted | `/db/users.db` |
| **AST-02** | Virtual Card Data | 16-digit PANs, CVV codes, and card operations handling. | Highly Confidential | `/api/cards` |
| **AST-03** | AI Support Logic | System prompts, internal logic, and AI decision-making flow. | Internal | `/ai/support` |
| **AST-04** | Session Tokens | JWTs used for user authentication and cryptographic signing keys. | Confidential | `LocalStorage / Cookies` |
| **AST-05** | App Environment | Flask configuration settings, debug parameters, and runner scripts. | Internal | `/healthz & start.sh` |
| **AST-06** | Merchant Payment API | Merchant registration responses and checkout endpoints. | Confidential | `/api/merchant` |

### Asset Summary
*   **Customer PII & Balances:** Primary target for identity-related attacks and financial theft.
*   **Authentication Data:** Critical vector for account impersonation and persistent session hijacking.
*   **Financial & Card Data:** Subject to rigorous regulatory mandates (PCI-DSS) and high fraud risks.
*   **AI Context & Infrastructure:** Vulnerable to manipulation, prompt-injection, or unauthorized system execution.

---
[« Phase 1: Context](01-context.md) | [Main Page](README.md) | [Phase 3: Threat Mapping »](03-threat-mapping.md)
