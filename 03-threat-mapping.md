# Phase 3: Threat Mapping

### Overview
This phase maps identified technical vulnerabilities to the specific threat scenarios that could compromise our assets. By understanding how an attacker thinks, we can implement targeted controls to break their attack chain.

### Threat Mapping Table

| Threat ID | Target Asset | Technical Vulnerabilities | Threat Scenario / Vector | Business & Regulatory Impact |
| :--- | :--- | :--- | :--- | :--- |
| **THR-01** | AST-01 (User Database) | • SQL Injection (SQLi) in auth fields<br>• Lack of input sanitization<br>• Plaintext storage of secondary backup data | Malicious input in login fields used to bypass authentication or dump database contents. | Financial: Potential theft of customer funds. Legal: Major data breach notification requirements. |
| **THR-02** | AST-02 (AI Agent Service) | • Lack of input validation/filtering<br>• Over-privileged API access<br>• Absence of context-aware guardrails | Crafting malicious instructions to manipulate the AI into revealing internal logic or performing unauthorized actions. | Reputational: Loss of public trust in AI capabilities. Operational: Unauthorized system manipulation. |
| **THR-03** | AST-03 (Virtual Card Management System) | • Plaintext storage of card PAN/CVV<br>• Client-controlled currency conversion<br>• BOLA in card operations | A malicious user manipulates API parameters during card-funding transactions to arbitrage rates or alters the account ID parameter to spend from another customer's virtual card. | Financial: Direct theft of funds. Legal: Non-compliance with PCI-DSS. |
| **THR-04** | AST-04 (Session Tokens / JWT Keys) | • Tokens stored in `localStorage`<br>• No server-side token invalidation<br>• Weak JWT secret keys | An attacker uses Cross-Site Scripting (XSS) or accesses a shared machine to extract a valid JWT from `localStorage`. Because the system doesn't invalidate tokens upon logout, the attacker maintains persistent access. | Financial: Account takeovers. Reputational: Devastating brand loss due to insecure sessions. |
| **THR-05** | AST-05 (Merchant Payment API) | • Plaintext API keys in registration responses<br>• Missing idempotency & rate-limiting | A rogue merchant or external attacker intercepts plaintext API keys or spams the checkout endpoint with duplicate payment requests (replay attacks) due to a lack of unique transaction tracking. | Financial: Chargeback/dispute losses. Operational: System degradation due to API abuse. |
| **THR-06** | AST-06 (Deployment Infrastructure) | • Flask development server running with `debug=True`<br>• Root-privileged Docker containers | An attacker deliberately triggers runtime errors on the web platform to access the interactive Werkzeug debugger web console, executing arbitrary code as root. | Operational: Total infrastructure compromise. Legal: Breach of data custody requirements. |

---
[« Phase 2: Assets Inventory](02-assets.md) | [Main Page](README.md) | [Phase 4: Analysis »](04-risk-analysis.md)
