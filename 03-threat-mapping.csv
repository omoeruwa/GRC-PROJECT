# Phase 3: Threat Mapping

### Overview
This phase maps identified technical vulnerabilities to the specific threat scenarios that could compromise our assets. By understanding how an attacker thinks, we can implement targeted controls to break their attack chain.

### Threat Mapping Table

| Threat ID | Target Asset | Technical Vulnerabilities | Threat Scenario / Vector | Business & Regulatory Impact |
| :--- | :--- | :--- | :--- | :--- |
| **THR-01** | AST-01 | SQL Injection (SQLi) | Malicious input in login fields used to bypass authentication or dump database contents. | Financial: Potential theft of customer funds. Legal: Major data breach notification requirements. |
| **THR-02** | AST-02 | AI Prompt Injection | Crafting malicious instructions to manipulate the AI into revealing internal logic or performing unauthorized actions. | Reputational: Loss of public trust in AI capabilities. Operational: Unauthorized system manipulation. |
| **THR-03** | AST-03 | Plaintext storage, BOLA | Manipulation of API parameters to force arbitrage or access other customers' virtual card data. | Financial: Direct theft of funds. Legal: Non-compliance with PCI-DSS. |
| **THR-04** | AST-04 | Tokens in localStorage, no server-side invalidation | XSS or shared machine access used to extract valid JWTs and maintain persistent unauthorized access. | Financial: Account takeovers. Reputational: Devastating brand loss due to insecure sessions. |
| **THR-05** | AST-05 | Plaintext keys, missing idempotency | Interception of API keys or replay attacks against the checkout endpoint. | Financial: Chargeback/dispute losses. Operational: System degradation due to API abuse. |
| **THR-06** | AST-06 | Debug mode enabled, root containers | Triggering runtime errors to access the Werkzeug debugger and execute arbitrary code as root. | Operational: Total infrastructure compromise. Legal: Breach of data custody requirements. |
