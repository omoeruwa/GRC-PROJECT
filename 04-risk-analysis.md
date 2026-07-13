
### Overview
To make informed decisions, we translate technical threats into a standardized 5x5 Risk Matrix. This allows us to visualize the probability of an attack against the potential impact on the bank.

### 5x5 Risk Matrix Reference Grid

| Impact \ Likelihood | 1 (Rare) | 2 (Unlikely) | 3 (Possible) | 4 (Likely) | 5 (Certain) |
| --- | --- | --- | --- | --- | --- |
| **5 (Catastrophic)** | 5 | 10 | 15 | 20 | 25 |
| **4 (Major)** | 4 | 8 | 12 | 16 | 20 |
| **3 (Moderate)** | 3 | 6 | 9 | 12 | 15 |
| **2 (Minor)** | 2 | 4 | 6 | 8 | 10 |
| **1 (Insignificant)** | 1 | 2 | 3 | 4 | 5 |

### Risk Assessment Table

| Risk ID | Target Asset | Threat Scenario / Vector | L | I | Score | Rating | Strategy | Remediation |
| :--- | :--- | :--- | :---: | :---: | :---: | :--- | :--- | :--- |
| **THR-01** | AST-01 | SQL Injection (Auth Bypass) | 4 | 5 | **20** | **CRITICAL** | Mitigate | Parameterized queries/ORMs |
| **THR-02** | AST-02 | AI Prompt Injection | 4 | 4 | **16** | High | Mitigate | Implement hard guardrail layer |
| **THR-03** | AST-03 | Virtual Card BOLA | 4 | 5 | **20** | **CRITICAL** | Mitigate | Strict object-level auth |
| **THR-04** | AST-04 | Persistent Session Hijacking | 3 | 4 | **12** | High | Mitigate | Secure cookies; Redis blocklist |
| **THR-05** | AST-05 | Payment API Replay Attacks | 3 | 4 | **12** | High | Mitigate | Idempotency keys; rate-limiting |
| **THR-06** | AST-06 | Infrastructure Debug Exposure | 4 | 5 | **20** | **CRITICAL** | Avoid | Disable debug; rootless containers |

### Analysis Findings
* **Critical Zone (Score 15-25):** These risks pose an existential threat to the platform and require immediate mitigation.
* **High Zone (Score 8-14):** These risks are significant and must be addressed in the next development cycle.
* **Moderate Zone (Score 1-7):** These are managed via ongoing monitoring and standard security hygiene.

---
[« Phase 3: Threat Mapping](03-threat-mapping.md) | [Phase 5: Risk Treatment »](05-risk-treatment.md)
