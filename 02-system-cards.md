# Lab 2: System Cards (NIST AI RMF, Map function)

> Coral Bay Credit Union is a fictional company created for this project.

## Module 2 and Lab 2: system cards (deliverable D2)

**Result:** Module 2 reading complete (6 of 6 on the check questions). System cards written for Ask Coral and QuickDecision. A system card is the NIST Map function on paper: what the system is, who it touches, and what could go wrong, written before anyone tests it.

**Module 2 in one line:** Govern sets the rules, Map finds the risks, Measure tests them, Manage fixes them. Govern sits in the center because it never stops running.

**Lessons from building the cards:**

- Name specific tasks and data. "Lower level functions" can't be risk-rated; "checks account balances" can.
- Affected people means humans first: members whose data it can reach, joint account holders, staff. Company losses go in the risk register.
- A chatbot never receives passwords. Online banking verifies the member and passes along only who they are.
- Write down what a system must not output. Ask Coral must never give loan decisions or full account numbers.
- Use "members," not "clients," at a credit union.
- Human oversight happens before, during, and after use, not at one checkpoint.

### System card: Ask Coral (AI-001)

| Question | Answer |
| --- | --- |
| 1. Purpose | Answers common member questions about products, fees, rates, and branch hours, and lets logged-in members check their balances, 24 hours a day. Reduces call center volume so staff can focus on complex member needs. |
| 2. Users | Members, through the website and mobile app. Member service staff handle escalated conversations. The Digital Banking team monitors performance and maintains the content it answers from. |
| 3. Affected people | Any member whose account data it can reach, including joint account holders; anyone who acts on its answers; member service staff who absorb complaints. The credit union faces reputational damage, regulatory findings, and possible fines. |
| 4. Inputs | Member messages, which may include personal information members volunteer; balances for the logged-in member only, through a lookup tool; Coral Bay rate sheets, fee schedules, and policies, through retrieval; verified identity from online banking, never passwords; system instructions. |
| 5. Outputs | Written answers about products, rates, and fees; the logged-in member's balances, with accounts masked to the last four digits; handoffs to staff; stored transcripts. **Must never** issue loan decisions, show full account numbers, or give financial advice. |
| 6. Decisions affected | No formal decisions, but it influences which products members open, whether they apply for loans, and how they manage money to avoid fees. A wrong answer can lead to a costly choice, so accuracy is a consumer protection issue. |
| 7. Model and vendor | Generative AI: a vendor chatbot platform built on a third-party large language model, customized with Coral Bay documents through retrieval. Limited, read-only agent capability (balance lookup). Coral Bay configures it but doesn't build or train the model. |
| 8. Human oversight | Before: Digital Banking approves all source content; testing before launch and after every vendor model change. During: members can request a person anytime; fraud, disputes, hardship, and complaints escalate automatically. After: 25 sampled transcripts reviewed weekly; complaints tracked monthly. Cannot act on accounts; any future action feature requires member confirmation through the banking system. |
| 9. Known limits | Can state wrong information confidently (confabulation). Only knows what's in its approved documents, so stale documents mean stale answers. Can be manipulated by cleverly worded messages (prompt injection). Not built for emotional or complex situations like hardship or fraud. May answer less accurately in Spanish or for members who write in mixed languages, which matters in South Florida. Cannot give personalized financial advice. |
| 10. Who could be harmed, and how | **Valid and reliable:** a member relies on a wrong fee or rate and makes a costly decision. **Secure and resilient:** a prompt injection reveals another member's balance or the system instructions. **Privacy-enhanced:** transcripts holding sensitive details are kept too long or used by the vendor for training. **Accountable and transparent:** members aren't told they're talking to AI. **Fair:** Spanish-speaking members get worse answers than English speakers. |

### System card: QuickDecision (AI-002)

| Question | Answer |
| --- | --- |
| 1. Purpose | Recommends approve, decline, or refer to an underwriter on consumer loan applications (auto, personal, and credit card), with a suggested rate tier. Speeds up decisions and applies criteria consistently. |
| 2. Users | Loan officers and underwriters, who act on its recommendations. The Chief Lending Officer reviews its monthly performance reports. |
| 3. Affected people | Every consumer loan applicant and co-applicant, including members in Colorado; applicants in protected groups if the model treats them unfairly; loan officers whose judgment it shapes. |
| 4. Inputs | Application data (income, employment, debts, loan amount and purpose); credit report and score from a credit bureau; account history at Coral Bay; address, including zip code. **Must exclude** characteristics fair lending law protects, such as race, religion, sex, and marital status. Zip code needs watching because it can stand in for race. |
| 5. Outputs | A recommendation (approve, decline, or refer); a risk score; a suggested rate tier; and the top reasons behind the score, which feed the denial notice. |
| 6. Decisions affected | Whether a member gets credit, and at what rate. This is a consequential decision under Colorado SB 26-189 from January 1, 2027, and the kind of credit-scoring use the EU AI Act rates high risk. |
| 7. Model and vendor | Predictive machine learning model from a vendor, built into the loan origination system. Trained mostly on the vendor's pooled lending data. Coral Bay cannot see how it works inside, so it depends on vendor documentation and its own testing. |
| 8. Human oversight | A loan officer reviews every recommended decline before it becomes final. Approvals under $25,000 book automatically (scenario assumption). Underwriters decide all referrals. Denied members can request reconsideration by a person. Override rates are reported monthly, fairness is tested yearly, and the Chief Lending Officer signs off on both. |
| 9. Known limits | Learned from historical lending, so it can repeat past bias. Less accurate for applicants with little credit history, such as young members and recent immigrants. Can't weigh context outside its data, like late payments caused by a medical emergency. Its reasons are simplified summaries, not a full explanation. Accuracy drifts as the economy changes. |
| 10. Who could be harmed, and how | **Fair:** one group is approved far less often, possibly through a stand-in like zip code. **Explainable:** denial reasons are too vague to meet Regulation B, so members can't understand or fix the problem. **Valid and reliable:** it approves members who can't repay, pushing them into debt. **Accountable and transparent:** members aren't told AI was used, which Colorado's law will require. **Privacy-enhanced:** credit data shared with the vendor is kept or reused without limits. |
