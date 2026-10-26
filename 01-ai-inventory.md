# Lab 1: AI Inventory

> Coral Bay Credit Union is a fictional company created for this project.

## Lab 1: AI inventory (deliverable D1)

**Result:** five AI systems inventoried. Four are high risk, one is medium risk, and one is running without approval. Two findings matter most: an email security tool nobody had listed as AI, and staff sending member data to public chatbots.

**Objective:** build Coral Bay's register of every AI system, with an accountable owner, the data each one touches, the decisions it affects, and a risk tier. Every later lab (classification, policy, risk register) builds on this list.

**Tools:** a spreadsheet with two tabs, AI Inventory and Shadow AI Plan.

**Tiering rule used:**

| Tier | Rule |
| --- | --- |
| High | Makes or materially influences a decision about a member's money, credit, or account; **or** acts on its own in ways that affect members without a person approving; **or** sends member data to a third party with no approved contract (applies until the system is approved or shut down) |
| Medium | Touches member personal data or talks to members, but decides nothing about them |
| Low | Internal use only, no member data, no decisions about people |

When a system fits two tiers, it takes the higher one. The third High condition was added during the lab, after the shadow AI row showed the first draft of the rule missed it. That gap is a finding of its own.

## AI inventory

How to read this table: go down one column to see everything about one AI system. Go across one row to compare all five systems on the same question. The "owner" rows always name a job title that one specific person holds, so there's always someone to call when something goes wrong.

| Field | AI-001 Ask Coral | AI-002 QuickDecision | AI-003 SentinelFlow | AI-004 Shadow AI | AI-005 MailShield (corrected) |
| --- | --- | --- | --- | --- | --- |
| Business purpose | Answers member questions on products, fees, and hours; looks up balances after login | Recommends approve or decline on consumer loan applications | Scores transactions and raises anti-money-laundering alerts for analyst review | Staff using free public chatbots to draft emails and summarize member files | Scans all email and automatically quarantines phishing and malware |
| Business owner | Vice President of Member Experience | Chief Lending Officer | Bank Secrecy Act Officer | Information Security Officer (accountable for finding and stopping it) | Information Security Officer |
| Technical owner | Digital Banking Manager | Loan Systems Manager | Compliance Systems Analyst | None: no one maintains it, which is the problem | Systems Administrator |
| Vendor or in-house | Vendor chatbot platform on a third-party large language model | Vendor model inside the loan origination system | Vendor model inside the transaction monitoring platform | Public chatbot providers with no contract | Vendor email security service |
| AI type | Generative, with an agent tool (balance lookup) | Predictive (score and recommendation) | Predictive (risk score) | Generative | Predictive (machine learning classifier) |
| Data used | **Yes, member personal data:** balances and anything members type | **Yes, member personal data:** income, employment, debts, credit report, account history, address and zip code | **Yes, member personal data:** transactions, counterparties, account and identity details | **Yes, member personal data:** whatever staff paste, possibly names, account numbers, loan files | **Yes, member personal data:** every inbound and outbound email and attachment |
| Who uses it / affected | Members (about 40,000 eligible); staff handle escalations | Loan officers; every consumer loan applicant | Anti-money-laundering analysts; members whose activity is flagged | Unknown number of staff; members whose data is pasted | All staff; members and outside senders whose mail can be quarantined |
| Decisions it affects | None directly, but members act on its answers about fees and rates | Credit approval or denial, and pricing | Which activity is investigated; can lead to suspicious activity reports or account closure | None directly; risk is data exposure | Which emails are delivered, quarantined, or deleted |
| Human review? | Partial: staff only when the member asks | Partial: loan officers review recommended declines; approvals under $25,000 book automatically (scenario assumption) | Yes: an analyst reviews every alert before action | No | Partial: quarantine is reviewed only when someone asks for a missing email |
| Laws that may apply | Gramm-Leach-Bliley Act; consumer protection rules on accurate disclosures | Equal Credit Opportunity Act and Regulation B; Colorado SB 26-189 for Colorado members from 1 January 2027; Fair Credit Reporting Act | Bank Secrecy Act; model risk guidance as best practice; likely outside Colorado's rules (fraud prevention exclusion), to confirm with counsel | Gramm-Leach-Bliley Act; possible breach notification duties | Gramm-Leach-Bliley Act vendor oversight |
| Risk tier | **High** | **High** | **High** | **High** | **Medium** |
| Tier reason | Talks to members, reaches account data through a tool, and can give wrong fee or rate answers members rely on | Directly decides members' access to credit; fair lending exposure and Colorado's law | Materially influences account decisions; a missed detection is a Bank Secrecy Act failure | Member data sent to third parties with no contract, no visibility, and no controls | Reads member data and acts on its own, but its actions are reversible and decide nothing about members' money |
| Status and next review | In production; every 6 months and after any vendor model change | In production; every 6 months, plus annual fairness test | In production; annual validation and quarterly tuning review | Unapproved; contain within 30 days, then review monthly | In production; annually and after vendor model updates |

## Tier decisions

Ask Coral and QuickDecision were easy calls; SentinelFlow and Shadow AI are the two most people underrate.

- **QuickDecision, High.** It decides who gets credit. It is the clearest example of a consequential decision under every framework: fair lending law, Colorado's new law, and the EU AI Act's credit-scoring category.
- **Ask Coral, High.** It talks to members and has a tool that reaches account data. A wrong fee answer becomes a consumer complaint; a leak becomes a privacy incident.
- **SentinelFlow, High.** It is tempting to rate it Medium because an analyst reviews every alert. But humans review only what the model flags: a missed pattern is never seen by anyone. Reviewing alerts does not catch misses.
- **Shadow AI, High.** The first draft of the rule rated it Medium, because it decides nothing. That was wrong. Member data leaving with no contract is the highest privacy exposure on the list, so the rule gained a third High condition.
- **MailShield, Medium.** It reads every email and acts without approval, but a quarantine is reversible and affects no member's money.

**Prediction check:** the expected prediction was QuickDecision and Ask Coral as High. Missing SentinelFlow or Shadow AI is the common mistake, and both follow the same lesson: **rate risk by what can go wrong, not by how much the system does.**

## Break and fix: MailShield

The submitted row understated the risk at every step, because it treated a security product as "not AI."

| # | Field | As submitted | Corrected | Why it was wrong |
| --- | --- | --- | --- | --- |
| 1 | AI type | Not AI, it's a security tool | Predictive (machine learning classifier) | Modern email security scores every message with machine learning models. AI hidden inside tools the company already owns is the most common inventory gap |
| 2 | Business owner | IT | Information Security Officer | A team cannot be accountable. Someone has to sign off on the risk, by name |
| 3 | Data used | None | Yes, member personal data: every email and attachment | It reads all mail, including member messages with account details and documents |
| 4 | Decisions / human review | None / Yes | Quarantines or deletes email automatically; humans review only on request | It acts on its own. "Yes" for human review was false |
| 5 | Risk tier and reason | Low, "it's just a filter" | Medium: reads member data and acts autonomously, but actions are reversible | A Low rating would exempt it from vendor and model-change reviews it needs |

**Smaller fixes:** the purpose was too vague to audit; the laws cell should name Gramm-Leach-Bliley vendor oversight; the status needed a review date.

## Shadow AI discovery plan

No single method finds all shadow AI, so Coral Bay combines log evidence, spending records, and asking staff directly.

| Method | What it finds | Owner | How often |
| --- | --- | --- | --- |
| Web proxy and domain name lookup logs for known AI sites | Which staff visit public chatbots, and how often | Information Security Officer | Monthly |
| Single sign-on and app permission reviews in the email and office suite | AI apps staff connected to their work accounts, and what data those apps can read | Identity and Access Administrator | Monthly |
| Data loss prevention alerts on member data sent to AI sites | Actual member data leaving, not just visits | Information Security Officer | Continuous, reviewed weekly |
| Expense reports and company card statements | Paid AI subscriptions bought outside procurement | Controller | Quarterly |
| Browser extension inventory from endpoint management | AI writing and meeting assistants installed on work computers | Systems Administrator | Quarterly |
| Vendor contract and renewal reviews | AI features vendors quietly added to tools Coral Bay already uses | Vendor Management Lead | At every renewal |
| Anonymous staff survey with an amnesty window | Use that logs miss, such as personal phones, and why staff turned to these tools | Information Security Officer with Human Resources | Twice a year |

**When shadow AI is found:** Coral Bay treats it first as a signal of unmet need, not a discipline problem. Staff use public chatbots because they save time. So the response is: (1) open a 30-day amnesty so staff report use without penalty; (2) provide an approved tool under a contract that bans training on Coral Bay data; (3) roll out the acceptable use policy with training; (4) only then block unapproved sites. If member personal data was pasted, it is handled as a possible privacy incident and assessed for notification duties.

## Explain it back

**Why is the inventory the first control in every AI program?** Every other control depends on it. You cannot assess, test, monitor, or write contracts for a system you don't know exists. Regulators and auditors ask for the list first. And the inventory itself uncovers risk: in this lab it found an unlisted AI tool and unapproved member data flows before any assessment began.

**Predictive vs. generative, with Coral Bay examples:** a predictive model outputs a score or a label from data, like QuickDecision's approve or decline and SentinelFlow's risk score. Its main risks are wrong or unfair decisions and drift. A generative model produces new content, like Ask Coral writing answers. Its main risks are false answers, data leakage, and prompt injection. The two types need different tests: fairness and accuracy testing for predictive, red teaming and output checks for generative.

**Defending Shadow AI as High to a skeptical chief financial officer:** "It doesn't make decisions, but it's the one place where member data leaves our building with no contract, no limit on how the provider uses it, and no record of what was sent. Under Gramm-Leach-Bliley we're responsible for that data regardless. One incident means investigation, possible member notification, and examiner findings. The fix is cheap: an approved tool with the right contract costs less than one incident response."

## Interview story (60 seconds)

"In my AI governance lab, I built the AI inventory for a credit union. The obvious systems were a member chatbot and a loan model, and both rated high risk. Two findings were less obvious. The email security tool had been listed as 'not AI' with no data, but it scores every email with machine learning and quarantines mail on its own, so I corrected it to medium risk with a named owner. And staff were pasting member data into public chatbots. My first tiering rule rated that medium because it decides nothing, so I rewrote the rule: any member data going to a provider with no contract is high risk until it's contained. Then I built a discovery plan combining logs, expense data, and an amnesty survey, and put an approved alternative in place before blocking anything."

**Next:** Lab 3 classification memo and the acceptable use policy (Thursday).
