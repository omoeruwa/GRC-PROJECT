Overview
To make informed decisions, we translate technical threats into a standardized 5x5 Risk Matrix. This allows us to visualize the probability of an attack against the potential impact on the bank.

The 5x5 Risk Matrix Logic
We score each risk based on:

Likelihood (1-5): How easy is it for an attacker to exploit this vulnerability?

Impact (1-5): How much financial, legal, or operational damage will occur?

Total Risk Score = Likelihood × Impact

Risk ID,Target Asset,Threat Scenario / Vector,Likelihood (1-5),Impact (1-5),Risk Score (L × I),Risk Rating,Risk Treatment Strategy & Remediation Action
THR-01,AST-01 (User DB),External attacker exploits SQL injection at /login to bypass authentication and dump plaintext credentials and balances.,4,5,20,Critical,Mitigate: Implement parameterized queries/ORMs; implement secure bcrypt hashing for all stored passwords immediately.
THR-02,AST-02 (AI Agent),"Malicious actor uses prompt injection to override the system prompt, gaining unauthorized direct access to database schemas.",4,4,16,High,Mitigate: Enforce strict LLM input validation; separate AI system instructions from user inputs; implement a hard guardrail layer.
THR-03,AST-03 (Virtual Cards),Attacker manipulates API parameters via BOLA to view or fund cards belonging to other account IDs.,4,5,20,Critical,Mitigate: Implement robust object-level authorization checks (validate session token matches card owner); encrypt card numbers at rest.
THR-04,AST-04 (Session Tokens),Persistent session hijacking due to insecure localStorage storage and a lack of server-side token invalidation upon logout.,4,4,16,High,"Mitigate: Transition session tokens to secure, HttpOnly, SameSite cookies; implement a server-side Redis blocklist for logged-out tokens."
THR-05,AST-05 (Merchant API),Exfiltration of plaintext API keys or execution of duplicate transaction replay attacks due to missing idempotency controls.,3,4,12,High,Mitigate: Mask API keys on creation; enforce standard HTTP idempotency keys (Idempotency-Key) and mandatory API rate-limiting.
THR-06,AST-06 (Infrastructure),"An attacker triggers a runtime application crash to access the interactive Werkzeug console, running OS commands as root.",4,5,20,Critical,Mitigate: Set debug=False in environment configurations; modify the Dockerfile to run the Flask application container under a non-root user.

Analysis Findings
Critical Zone (Score 15-25): These risks pose an existential threat to the platform and require immediate mitigation.

High Zone (Score 8-14): These risks are significant and must be addressed in the next development cycle.

Moderate Zone (Score 1-7): These are managed via ongoing monitoring and standard security hygiene.

Conclusion
Our analysis highlights that the most severe risks are concentrated in our authentication and API layers. This dictates where our remediation resources must be deployed first.
