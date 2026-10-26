# Lab 4: AI Policies and ISO/IEC 42001 Statement of Applicability

> Coral Bay Credit Union is a fictional company created for this project.

## Module 4 and Lab 4: ISO 42001 and policy (deliverables D4 and D5)

**Result:** an acceptable use policy for all staff, a short AI governance policy, and a Statement of Applicability covering all nine Annex A areas.

**Module 4 key points:**

- ISO 42001 is certifiable; clauses 4 to 10 follow plan (4–6), do (7–8), check (9), act (10).
- Clause 9 is where you prove the program works: monitoring results, internal audit, leadership review minutes.
- Annex A: 38 controls in 9 areas, A.2 to A.10. A.3 is the inside voice (staff reporting concerns); A.8 is the outside voice (telling members).
- The Statement of Applicability is the answer sheet for the auditor's checklist: for each control, does it apply, why, and how it's met with proof. Every exclusion needs its own reason.
- Buying AI instead of building it doesn't remove controls; it moves many of them into vendor due diligence.

### Acceptable use of AI (all staff)

1. **Approved tools only.** Use AI tools on the approved list. Request new ones through the Information Security Officer.
2. **Protect member data.** Never enter member or confidential information into public AI tools.
3. **A person decides.** AI may assist, but a person makes the final decision on loans, accounts, hiring, and complaints.
4. **You own the output.** Check AI-generated content for accuracy before using or sending it.
5. **Be transparent.** Never present AI as a human to members.
6. **Report problems.** Report errors, data exposure, or misuse right away. Good-faith reports are never penalized.
7. **Training and enforcement.** Complete AI training yearly. Violations fall under the disciplinary policy.

### AI governance policy (summary)

| Section | Rule |
| --- | --- |
| Purpose and scope | Covers every AI system Coral Bay uses, buys, or builds, including AI inside vendor tools, from proposal to retirement |
| Roles | The board approves this policy and sets risk appetite. An AI committee (Chief Risk Officer as chair, with lending, compliance, information security, and legal) approves high-risk systems. Every system has a named business owner who accepts its residual risk |
| Risk tiers | High, medium, low, using the Lab 1 tiering rule. High-risk systems need committee approval; medium need owner and information security approval; low need registration only |
| Before launch | Inventory entry, system card, legal classification, vendor review, and testing matched to the risk (fairness, accuracy, red teaming) |
| After launch | Monitoring matched to the risk; review at least yearly and after any vendor model change; incidents handled through incident response |
| Exceptions | Written, time-limited, approved by the AI committee, and tracked to closure |
| Review | Policy reviewed every year by the AI committee and approved by the board |

### Statement of Applicability

| Area | Applies? | Why | How it's met (evidence) |
| --- | --- | --- | --- |
| A.2 Policies | Yes | Coral Bay needs rules for all AI use | Board-approved AI governance policy and acceptable use policy; yearly review record |
| A.3 Internal organization | Yes | Owners and a way for staff to raise concerns are needed for every system | Named owners in the inventory; AI committee charter; reporting channel with no penalty for good-faith reports |
| A.4 Resources | Yes | Each system depends on data, tools, vendors, and people | Inventory columns for vendor, data, and owners; staff training records |
| A.5 Impact assessment | Yes | QuickDecision and Ask Coral affect members directly | Impact assessments on the system cards; yearly fairness test results |
| A.6 Lifecycle | Partly | Coral Bay doesn't build models, but controls every stage it touches | Approval records, pre-launch test reports, risk owner sign-offs, logs, monitoring reports, retirement checklist. Design and development covered by vendor controls (A.10) |
| A.7 Data | Partly | Vendors train the models; Coral Bay controls data going in and out | Vendor questionnaire on training data; data limits for inputs; transcript retention limit; fairness checks for stand-ins like zip code |
| A.8 Information for interested parties | Yes | Members are affected by AI | Ask Coral discloses it's AI; denial notices with specific reasons; Colorado notices from 2027; complaint process |
| A.9 Use of AI systems | Yes | Staff use AI every day: loan officers act on QuickDecision's recommendations, analysts review SentinelFlow alerts, and all staff may use approved tools | **Controls:** acceptable use policy; loan officer reviews every recommended decline (AI recommends, a person decides); systems used only for approved purposes; yearly training. **Evidence:** signed policy acknowledgments, training records, override logs, monitoring reports |
| A.10 Third parties | Yes | Every Coral Bay AI system is bought | Contract terms: no training on member data, retention limits, breach and model-change notice, audit rights; yearly vendor reviews |
