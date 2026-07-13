# Phase 2: Asset Inventory

### Overview
Before we can secure the system, we must identify what we are actually protecting. In the context of the Vuln-Bank platform, we define "Assets" as any data, hardware, or software component that, if compromised, would cause financial loss, reputational damage, or regulatory failure.

### Critical Assets Inventory

| Asset ID | Asset Name | Description | Data Classification | App Component |
| :--- | :--- | :--- | :--- | :--- |
| **AST-01** | User PII & Balances | Names, Emails, Passwords, and Wallet balances. | Restricted | /db/users.db |
| **AST-02** | Virtual Card Data | 16-digit PANs and CVV codes (Stored in plaintext). | Highly Confidential | /api/cards |
| **AST-03** | AI Support Logic | System prompts and AI decision-making flow. | Internal | /ai/support |
| **AST-04** | Session Tokens | JWTs used for user authentication. | Confidential | LocalStorage / Cookies |
| **AST-05** | App Environment | Flask debug mode and server headers. | Internal | /healthz & start.sh |

### Asset Summary
*   **Customer PII:** Primary target for identity-related attacks.
*   **Authentication Data:** Critical vector for account impersonation.
*   **Financial & Card Data:** Subject to rigorous regulatory mandates (PCI-DSS).
*   **AI Context & Infrastructure:** Vulnerable to manipulation, poisoning, or unauthorized environment access.
