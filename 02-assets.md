Overview
Before we can secure the system, we must identify what we are actually protecting. In the context of the Vuln-Bank platform, we define "Assets" as any data, hardware, or software component that, if compromised, would cause financial loss, reputational damage, or regulatory failure.

Inventory of Critical Assets
Customer PII (Personally Identifiable Information): Names, home addresses, phone numbers, and email addresses. This is our most sensitive data and a primary target for attackers.

Authentication Data: User passwords, session tokens, and multi-factor authentication secrets. If these are stolen, an attacker can impersonate any customer.

Financial Transaction Data: Account balances, bank transfer history, and transaction logs. This is the direct target for fraud.

Virtual Card Data: PAN (Primary Account Numbers) and security codes. This data is subject to strict PCI-DSS compliance requirements.

AI Agent Context: The memory and instructions provided to our customer support AI. If this is poisoned or exfiltrated, it can be used to manipulate the system.

Infrastructure & API Keys: The server environments, container configs, and API keys used to talk to third-party payment gateways.

Asset ID,Asset Name,Description,Data Classification,App Component
AST-01,User PII & Balances,"Names, Emails, Passwords, and Wallet balances.",Restricted,/db/users.db
AST-02,Virtual Card Data,16-digit PANs and CVV codes (Stored in plaintext).,Highly Confidential,/api/cards
AST-03,AI Support Logic,System prompts and AI decision-making flow.,Internal,/ai/support
AST-04,Session Tokens,JWTs used for user authentication.,Confidential,LocalStorage / Cookies
AST-05,App Environment,Flask debug mode and server headers.,Internal,/healthz & start.sh
