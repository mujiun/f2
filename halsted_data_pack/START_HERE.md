# Start here

All companies, people, and figures are fictional. No credit background needed.

## The story in one minute

Northgate, a lending fund, lent $85M to Halsted Industrial Services. The loan has a rule: Halsted's debt can't be more than 5.25x its yearly earnings this quarter. Every quarter Halsted sends a report card: financial statements, a short commentary, and a signed certificate saying it passed.

On Friday, August 14, 2026, Halsted's CFO emailed the Q2 report card. It was forwarded to Adam, F2's AI agent, which read it, redid the math, and compared it with the past. It is now Tuesday morning. Maya, the analyst, is about to open Halsted's workspace.

## What Adam found

1. **Halsted's cushion under the debt limit shrank from 19% to 8%.** Under 10% is amber. About 4 points is the limit tightening on schedule; about 7 is weaker earnings.
2. **Halsted's own numbers disagree with Adam's.** Halsted's signed certificate reports an 11.8% cushion, which would keep it green. The difference is $0.72M of savings from a cost program that started in July, after the quarter ended. Halsted counts those savings; the loan agreement doesn't allow them, so Adam leaves them out. Whether Halsted is green or amber depends on whose number Maya accepts.
3. **Halsted has missed its approved plan for four quarters.** The top risk named when the deal was approved, wage inflation, is what management blames now.

Adam suggests moving Halsted from green to amber. Maya decides.

## How the cushion is worked out

| | Last quarter | This quarter |
| --- | --- | --- |
| Debt limit | 5.50x | 5.25x |
| Halsted's debt ÷ earnings, per Adam | 4.45x | 4.83x |
| Halsted's debt ÷ earnings, per Halsted's certificate | 4.45x | 4.63x |
| Cushion, per Adam | 19.1% | 8.0% |
| Cushion, per Halsted | 19.1% | 11.8% |

Cushion = (limit − debt ÷ earnings) ÷ limit. The data calls it headroom.

## Which data to use for what

The folders follow the story in order. For a working prototype you need folders 2, 3, and 4. Folder 1 is background: how the package arrived. You don't need to design that step.

| Folder | Use it for | Open first |
| --- | --- | --- |
| `1_the_email/` | **Background only.** How the package arrived. Intake is already handled, so you don't need to design it. | `email.json` (the email). `attachments/` holds the two PDFs Halsted sent. |
| `2_workspace_before_this_quarter/` | **The workspace before today.** What F2 already knew about Halsted. | `workspace.json`: loan terms, the debt limit and its schedule, the approved plan, five past quarters, current status (green). `documents/` holds the investment committee memo, the loan agreement, and Maya's review from last quarter. |
| `3_what_adam_found/` | **The workspace after today.** What's new this quarter. | `adam_first_pass.json`. Read its `summary` first: it lists the three findings and the suggested status, and points to the detail behind each. |
| `4_fund_rules/` | **The decision.** When a borrower is green, amber, or red, and what Maya must do when she changes a status. | `credit_policy.json` |

## Where each finding lives

| Finding | Numbers | Source documents to link to |
| --- | --- | --- |
| 1. Cushion 19% → 8% | `adam_first_pass.json` → `covenant_tests`, `headroom_bridge` | Loan agreement p.2 (the limit schedule); financial statements pp.1–2 |
| 2. Halsted's numbers disagree | `adam_first_pass.json` → `certificate_check` | Certificate p.2 (the $720K line); loan agreement p.1 (the rule); financial statements p.3 (July launch date) |
| 3. Behind plan | `adam_first_pass.json` → `variances`, `underwriting_links`; plan in `workspace.json` → `underwriting_case` | Investment committee memo pp.2–3 |

## Conventions

- JSON figures are in USD millions; the PDFs are in USD thousands, as borrowers report.
- "Headroom" in the data means the cushion: (limit − actual) ÷ limit.
- Every figure in `adam_first_pass.json` carries a `sources` entry with the file and page it came from. Use them to show where a number comes from.
- Anything not mentioned above is extra context. Use it if it helps; ignore it if it doesn't.
