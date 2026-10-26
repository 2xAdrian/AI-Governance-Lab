# AI Governance Program for a Credit Union #
A hands-on project where I built an AI governance program from scratch for a fictional credit union. I found every AI system it uses, rated the risk, checked which laws apply, wrote the policy, attacked an AI app to test the controls, and moved the risk register into a real GRC platform.

I did this to prepare for Security Analyst and GRC (governance, risk, and compliance) roles. My background is bank compliance (anti-money laundering investigations, sanctions screening, and suspicious activity reports) and email security at Sublime Security. AI governance sits right between those two: it needs someone who understands how regulators think and how attackers think.

## At a glance ##

| | |
|---|---|
| **What I built** | A complete AI governance program for a fictional credit union with 5 AI systems |
| **Key findings** | 4 of 5 AI systems rated high risk · an AI app's hidden instructions extracted in 3 attempts · a loan model flagged for fair lending review (0.75 ratio) · 2 vendor contract fixes required |
| **Frameworks** | NIST AI Risk Management Framework, ISO/IEC 42001, ISO 27005, EU AI Act, OWASP Top 10 for LLM Applications |
| **Laws applied** | Regulation B (fair lending), FCRA (credit reporting), GLBA (financial privacy), Colorado's AI law |
| **Tools** | CISO Assistant (GRC platform), Lakera Agent Breaker (AI attack testing), Excel |
| **Skills shown** | Risk assessment · AI inventory · regulatory mapping · policy writing · control testing · vendor risk · fairness testing · GRC platform use |

## Why AI governance? ##

Companies are adopting AI faster than they can control it:

- **Nobody knows what AI is running.** Staff use public chatbots, and vendors quietly add AI to tools the company already owns.
- **AI makes decisions about people.** A loan model that treats one group unfairly is a fair lending problem, even if nobody intended it.
- **AI can be tricked.** Chatbots can be manipulated into leaking data or ignoring their rules.
- **Regulators expect it.** Colorado, the EU, and bank regulators all expect companies to manage AI risk.

> **Note:** Coral Bay Credit Union is a fictional company I created for practice. All systems and numbers are illustrative. The AI attack test in Step 5 was done on a training platform built for that purpose.

## How I approached it ##

```mermaid
flowchart LR
  A[1. Inventory] --> B[2. Map]
  B --> C[3. Laws]
  C --> D[4. Policy]
  D --> E[5. Testing]
  E --> F[6. GRC platform]
```

I worked through six stages in order, because each one depends on the one before it: I couldn't check laws for systems I hadn't found, and I couldn't test controls I hadn't written yet.

**The scenario:** Coral Bay Credit Union has 200 employees and about 40,000 members in Florida, some of whom live in other states. It runs five AI systems: a member chatbot (Ask Coral), a loan decision model (QuickDecision), a money laundering detection model (SentinelFlow), staff using public chatbots without approval (Shadow AI), and an email security filter (MailShield).

# Step 1 - I built the AI inventory #

The first thing I did was list every AI system at Coral Bay, because you can't govern what you don't know exists. For each one I recorded its purpose, a named owner (a person, not a department), the data it uses, the decisions it affects, and whether a human reviews it.

Then I wrote a simple rule to rate risk: a system is **high** if it decides about members' money, acts without a person approving, or sends member data somewhere with no contract. Using that rule, four of the five systems came out high risk and one medium.

This table is the result. Each row is one AI system; the last column is the risk rating from my rule above, and the column before it explains why.

| AI system | What it does | Owner | Why that rating | Risk |
|---|---|---|---|---|
| Ask Coral | Member chatbot that can look up balances | VP of Member Experience | Talks to members and can see account data | High |
| QuickDecision | Recommends loan approvals and denials | Chief Lending Officer | Decides who gets credit | High |
| SentinelFlow | Flags transactions for money laundering | Bank Secrecy Act Officer | Its misses are never seen by a person | High |
| Shadow AI | Staff pasting member data into public chatbots | Information Security Officer | Member data leaves with no contract | High |
| MailShield | Email filter that uses machine learning | Information Security Officer | Reads member email, but its actions can be undone | Medium |

Two ratings took real thought. The money laundering model looked safe because an analyst reviews every alert, but I rated it high: analysts only see what the model flags, so anything it misses is invisible. And the email filter had been listed as "not AI." From my time at Sublime, I knew email security runs on machine learning and quarantines mail on its own, so I corrected the entry. AI hidden inside tools a company already owns is the easiest kind to miss.

I also wrote a plan to find unapproved AI use, combining web logs, expense reports, and an anonymous staff survey.

**Skill shown:** building an AI inventory and rating risk with a consistent, written rule.

# Step 2 - I mapped the riskiest systems with the NIST AI RMF #

Next, I used the NIST AI Risk Management Framework (the U.S. government's guide for managing AI risk), which has four functions: Govern, Map, Measure, and Manage. I focused on **Map**, which means understanding a system and who it could hurt before testing it.

I wrote a one-page system card for the chatbot and the loan model, answering ten questions on each: purpose, users, people affected, inputs, outputs, decisions influenced, vendor, human oversight, known limits, and possible harms. I tied each harm to one of NIST's seven qualities of trustworthy AI, such as fair, secure, or explainable.

This step turned up concrete requirements. The chatbot should never receive member passwords, never give loan decisions, and never show full account numbers. For the loan model, the biggest risks were fairness, since zip code can act as a stand-in for race, and being able to explain why someone was denied.

**Skill shown:** applying the NIST AI Risk Management Framework to real systems.

# Step 3 - I checked which laws apply #

With the systems understood, I classified each one against the laws that apply. I used four questions for every system: What industry rules cover it? Where do the affected people live? Does it decide something important about a person? What personal data does it use?

The loan model carried the most obligations: specific reasons for every denial (Regulation B), credit report disclosures (Fair Credit Reporting Act), protecting member data (Gramm-Leach-Bliley Act), and Colorado's new AI law, which applies because Coral Bay lends to Colorado residents. I also noted that Coral Bay **deploys** vendor AI rather than building it, and that heavily modifying a vendor's model could change that role and bring heavier duties.

**Skill shown:** mapping systems to the regulations that apply and turning them into concrete obligations.

# Step 4 - I wrote the policy and mapped it to ISO 42001 #

Then I wrote the rules. First, a one-page acceptable use policy for all staff: use approved tools only, never put member data in public tools, a person makes the final decision, and report problems without penalty. Second, an AI governance policy that sets up an AI committee, named risk owners, and approval levels based on risk.

Finally, I mapped the program to ISO/IEC 42001, the AI standard outside auditors can certify. I built a Statement of Applicability: for each of the standard's nine control areas, I recorded whether it applies, why, and what evidence proves it. The biggest lesson was that buying AI instead of building it doesn't remove controls. It moves them into vendor reviews.

**Skill shown:** policy writing and mapping a program to a certifiable standard.

# Step 5 - I tested the controls #

Policies only matter if they hold up, so I tested three things.

**I attacked an AI app.** Using Lakera Agent Breaker, a platform built for practicing attacks on AI apps, I tricked an AI coaching app into revealing its hidden instructions. It took 3 attempts. That proved that anything placed in an AI's instructions should be treated as public, which is why my policy keeps secrets out of them entirely.

![Agent Breaker: app owned with a score of 78 out of 100](images/agent-breaker-cycling-coach.png)

**I tested the loan model for fairness.** I compared approval rates between two groups of applicants:

| Group | Applicants | Approved | Approval rate |
|---|---|---|---|
| Group A | 400 | 240 | 60% |
| Group B | 300 | 135 | 45% |

To compare them, I divided the lower rate by the higher one: 45% ÷ 60% = **0.75**. The common screening rule is that anything under 0.80 is a red flag, so I flagged the model for a deeper fair lending review. It's a reason to investigate, not proof of discrimination.

**I reviewed the chatbot vendor.** I sent eight due diligence questions. Two answers were red flags: the vendor may train its model on member conversations, and it won't name the AI provider underneath. I recommended approving the vendor only if the contract fixes both.

**Skill shown:** testing controls, fairness analysis, and third-party (vendor) risk review.

# Step 6 - I moved the risk register into a GRC platform #

Last, I moved the work out of spreadsheets and into CISO Assistant, an open-source GRC platform with more than 220 frameworks built in, including NIST AI RMF and ISO 42001. This is how companies actually run a risk program.

I started from an empty workspace.

![CISO Assistant dashboard before any data was added](images/ciso-assistant-dashboard.png)

I set up Coral Bay as the organization, defined "AI Systems" as the scope, and added the five AI systems as assets. Then I loaded a 5x5 risk matrix based on ISO 27005, the international standard for information security risk management, so every risk is scored the same way.

![Loading the ISO 27005 risk matrix from the CISO Assistant library](images/ciso-assistant-risk-matrix-library.png)

Next, I entered seven risk scenarios. For each one I recorded the current risk, the controls already in place, a treatment decision, the new controls, and the risk left afterward.

Here is the risk register. Scores are **probability × impact**, each from 1 (lowest) to 5 (highest). "Current" is the risk today; "Residual" is the risk after the new controls are in place, so the drop between them shows what each control is worth.

| Risk | AI system | Current | Treatment | New controls | Residual |
|---|---|---|---|---|---|
| Loan model approves one group less often | QuickDecision | 4 × 5 | Mitigate | Fair lending review, re-test without zip code | 3 × 4 |
| Prompt injection leaks data or instructions | Ask Coral | 4 × 4 | Mitigate | No secrets in prompts, output filtering, red-team testing | 2 × 4 |
| Chatbot quotes wrong fees or rates | Ask Coral | 3 × 4 | Mitigate | Document owner, monitoring against the fee table | 2 × 3 |
| Staff paste member data into public chatbots | Shadow AI | 4 × 5 | Mitigate | Acceptable use policy, approved tool, site blocking | 3 × 4 |
| Model drift causes missed money laundering | SentinelFlow | 3 × 5 | Mitigate | Monthly monitoring, yearly validation | 2 × 4 |
| Vendor trains its model on member conversations | Ask Coral | 3 × 4 | Transfer | Contract clause, yearly vendor review | 2 × 3 |
| Email filter wrongly quarantines member email | MailShield | 2 × 2 | Accept | None needed | 2 × 2 |

![Building the loan model risk scenario in CISO Assistant](images/ciso-assistant-risk-scenario.png)

I didn't mitigate everything. I chose to **accept** the email filter risk, because a wrongly quarantined email is low impact and easy to undo. I **transferred** the vendor training risk through a contract clause, while noting that Coral Bay stays accountable for member data either way.

**Skill shown:** running a risk assessment in a GRC platform, including choosing when to mitigate, transfer, or accept a risk.

**Status:** risk scenarios being finalized in CISO Assistant; an ISO 42001 compliance assessment in the platform is next.

## Results ##

- An inventory of five AI systems, with four rated high risk
- System cards, a legal classification, an acceptable use policy, and an ISO 42001 Statement of Applicability
- A real prompt injection finding: hidden instructions extracted in 3 attempts
- A fairness flag (0.75 ratio) and a vendor review with two required contract fixes
- A risk register built in a GRC platform

## Full write-ups ##

- [Step 1 - AI inventory](01-ai-inventory.md)
- [Step 2 - System cards](02-system-cards.md)
- [Step 3 - Legal classification](03-classification-memo.md)
- [Step 4 - Policies and Statement of Applicability](04-policies-and-statement-of-applicability.md)
- [Step 5 - Red-team report](05-red-team-report.md)
- [Step 5 - Vendor review and fairness test](06-vendor-fairness-monitoring.md)

**About me:** Luis Ramirez, Security Analyst. CAMS and CompTIA Security+. [LinkedIn](https://www.linkedin.com/in/luis-ramirez-696336180)
