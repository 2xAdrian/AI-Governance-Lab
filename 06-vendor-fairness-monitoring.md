# Lab 6: Vendor Review, Fairness Test, and Monitoring

> Coral Bay Credit Union is a fictional company created for this project.

## Module 6 and Lab 6: vendors, fairness, monitoring (deliverables D7 and D8)

**Result:** the Ask Coral vendor gets a conditional approval with two contract fixes, and QuickDecision fails the four-fifths screen (ratio 0.75), which triggers a fair lending review.

**Module 6 key points:**

- Most AI is bought, so most AI governance happens in vendor due diligence. Add AI questions to the existing vendor review instead of building a separate process.
- Fourth-party risk: your vendor's vendor, such as the model provider under a chatbot platform.
- Green-flag answers are specific, in writing, and come with proof. Vague promises are non-answers.
- Adverse impact ratio: lower approval rate divided by the higher one. Under 0.80 means investigate. A flag isn't proof of discrimination, and a pass isn't proof of fairness. Watch for stand-ins like zip code.
- Monitor each system for the risks you assessed. A near-zero override rate is a warning sign of automation bias.
- Handle AI incidents through the existing incident response plan, with AI steps added.

### Vendor review: Ask Coral platform (D7)

| # | Question | Vendor's answer | Rating |
| --- | --- | --- | --- |
| 1 | Do you train on our data? | "We may use customer conversations to improve our models" | 🚩 Red flag |
| 2 | How long do you keep our data? | 30 days | ✅ Green |
| 3 | Where is data stored? | United States data centers (to confirm in contract) | ✅ Green, pending contract |
| 4 | Notice before model changes? | 60 days for major changes | ✅ Green |
| 5 | Testing evidence? | Security report shared; fairness results requested | Follow up |
| 6 | Other companies processing our data? | "Our model provider is a third party we don't disclose" | 🚩 Red flag |
| 7 | Breach notice timeframe? | Requested in contract: 72 hours or less | Follow up |
| 8 | Audit rights or reports? | Independent security audit report available | ✅ Green |

**Recommendation: conditional approval.** Sign only if the contract (1) prohibits training on Coral Bay data, with the setting confirmed off in writing, and (2) names the model provider, includes its data terms, and requires notice before switching providers. Also require breach notice within 72 hours and fairness test results. Reassess yearly and after any model change.

### Fairness test: QuickDecision (D8)

| Group | Applicants | Approved | Approval rate |
| --- | --- | --- | --- |
| Group A | 400 | 240 | 60% |
| Group B | 300 | 135 | 45% |

**Adverse impact ratio:** 45% ÷ 60% = **0.75**, below the 0.80 threshold. **Flagged for review; not proof of discrimination.**

**Next steps:** escalate to compliance and the Chief Lending Officer; run deeper statistical analysis controlling for income, debt, and credit history; re-test without zip code and other possible stand-ins; request the vendor's fairness testing and the factors behind the gap; add human review of Group B declines during the investigation; document every step as examiner evidence.

### Incident example: Ask Coral quotes the wrong overdraft fee

1. **Contain:** turn off fee answers and send fee questions to staff until fixed.
2. **Investigate:** check the fee document Ask Coral retrieves from, likely outdated, and pull transcripts to find every affected member.
3. **Make members whole:** contact affected members and refund fees they paid because of the wrong answer.
4. **Fix and prevent:** update the document, add a named owner who updates it whenever fees change, and add a monitoring check comparing answers to the official fee table.
5. **Document:** record it as an AI incident, update the risk register, and report it to the AI committee.
