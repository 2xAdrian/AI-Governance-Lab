# Lab 3: Regulatory Classification Memo

> Coral Bay Credit Union is a fictional company created for this project.

## Module 3 and Lab 3: classification memo (deliverable D3)

**Result:** all five systems classified. Four are high risk; Coral Bay is the deployer for every vendor system; Colorado's law reaches QuickDecision from January 1, 2027.

**Module 3 key points:**

- Laws follow the member: Colorado's law applies when you do business with Colorado residents.
- EU AI Act tiers: prohibited, high risk, transparency, minimal. High-risk duties delayed to December 2, 2027 (credit, hiring) and August 2, 2028 (regulated products).
- Executive Order 14365 starts legal challenges but cancels no state law. Only Congress or a court can.
- Regulation B requires specific denial reasons; model complexity is no excuse.
- The April 2026 model risk guidance is best practice for Coral Bay and excludes generative AI.
- There's no fixed list of laws. Ask four questions: what industry rules cover the decision, where affected people live, whether it decides something important about a person, and what personal data it uses. Then confirm with legal.
- Deployer becomes provider by substantially modifying or rebranding a system.

### Classification memo

**To:** Coral Bay leadership · **From:** AI governance · **Re:** Legal classification of Coral Bay's AI systems (fictional company)

| System | Laws that apply | Tier | Role | Key obligations |
| --- | --- | --- | --- | --- |
| QuickDecision | Equal Credit Opportunity Act and Regulation B; Fair Credit Reporting Act; Gramm-Leach-Bliley Act; Colorado SB 26-189 from January 1, 2027. Best practice: model risk guidance. EU: would be high risk; not applicable | High | Deployer | Specific denial reasons tested against the model; credit bureau and score on credit-based denials; yearly fairness testing including stand-ins like zip code; vendor data limits; Colorado notice, explanation, 30-day human review, 3-year records; loan officer reviews every decline; drift monitoring and yearly revalidation; change control |
| Ask Coral | Gramm-Leach-Bliley Act; consumer protection against unfair or deceptive practices; Truth in Savings and Truth in Lending disclosures; state chatbot disclosure laws. Excluded: model risk guidance (generative). EU: transparency tier; not applicable | High | Deployer | Tell members it's AI; answer only from approved documents matching official disclosures; vendor contract (no training, retention limits, breach and model-change notice); logged-in member's data only, masked; transcript retention limit; red teaming; escalation of sensitive topics; weekly transcript sampling |
| SentinelFlow | Bank Secrecy Act and the credit union regulator's anti-money-laundering program rules; Gramm-Leach-Bliley Act. Best practice: model risk guidance (predictive, so in scope). Colorado: likely excluded as fraud prevention, to be confirmed with counsel | High | Deployer | Yearly independent validation; documented thresholds and tuning; monitor the rate of alerts that become suspicious activity reports; analyst review of every alert; records kept 5 years; examiner-ready explanation of how alerts are generated; vendor contract; change control |
| Shadow AI | Gramm-Leach-Bliley Act (safeguards and vendor oversight, both missing); state breach notification laws if member data was exposed | High | None formally, but Coral Bay is still responsible for the data | Discover through logs, expenses, and an amnesty survey; provide an approved tool under contract; acceptable use policy and training; block unapproved tools after the alternative exists; assess any exposure as a possible privacy incident |
| MailShield | Gramm-Leach-Bliley Act vendor oversight (it reads member email) | Medium | Deployer | Vendor contract with data limits and model-change notice; documented quarantine and release process; monitor wrongly quarantined email; yearly review |
