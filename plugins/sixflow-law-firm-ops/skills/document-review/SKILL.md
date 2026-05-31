---
name: document-review
description: >
  This skill should be used when the user asks to "review this document", "review
  this contract", "what's important in this agreement", "pull the key terms", "do a
  legal review", "flag risks in this document", or "summarize this document for me".
  It reads a legal document and surfaces the legally-relevant elements — parties,
  dates and deadlines, obligations, governing law, and risk clauses — for an
  attorney's review.
metadata:
  version: "0.1.0"
  author: "SixFlow"
---

# Document Review

Read a legal document and surface what matters legally so an attorney can review it
quickly. This skill assists a lawyer's review — it does not provide legal advice or
replace professional judgment. Always present findings as items to verify, not
conclusions.

## Before reviewing

1. Identify the **document type** (e.g., contract/agreement, lease, NDA, demand
   letter, pleading, settlement, discovery response, policy). Different types have
   different critical elements.
2. Load firm context from `CLAUDE.md` — practice areas and what the firm treats as
   important. Tailor emphasis to the firm's practice (e.g., a PI firm cares about
   liability releases and medical records; a corporate firm cares about indemnity and
   IP assignment).

## Source of the document

Review a document the user provides by any of:

- An uploaded or attached file (PDF, Word, or text).
- A file path the user gives.
- An attachment from their connected `~~email`.
- A file from their connected `~~documents` store, if one is set up.

Read the full document before summarizing. For long documents, review section by
section so nothing is missed. Never guess at content you have not read.

## What to extract (legal relevance)

Pull and organize the following, citing where each appears (section/page/clause):

1. **Parties** — who is bound, their roles, and any signatories or missing signatures.
2. **Key dates & deadlines** — effective date, term, renewal/auto-renewal, termination
   dates, response or cure deadlines, and any statute-of-limitations or filing dates.
   Flag anything time-sensitive prominently.
3. **Core obligations** — what each party must do, deliver, or pay.
4. **Financial terms** — amounts, payment schedule, interest, penalties, fees.
5. **Governing law, jurisdiction & venue** — and any arbitration / dispute-resolution
   clause.
6. **Risk & protective clauses** — indemnification, limitation of liability, warranties,
   representations, confidentiality, non-compete/non-solicit, assignment, termination
   for cause/convenience.
7. **Red flags** — unusual, one-sided, ambiguous, or unfavorable terms; internal
   inconsistencies; and notably **missing** standard clauses for this document type.
8. **Defined terms** — surface any defined term whose definition materially affects
   how a clause reads.

## Output format

1. **Snapshot** — document type, parties, one-line purpose, and execution status.
2. **Time-sensitive items** — dates and deadlines, most urgent first, each with its
   location and why it matters.
3. **Key terms** — obligations, financial terms, governing law, grouped and cited.
4. **Risks & red flags** — each with its location, why it is a concern, and a suggested
   point for the attorney to examine. Separate "unfavorable terms" from "missing terms".
5. **Questions for the attorney** — ambiguities or items needing human legal judgment.

## Rules

- **Not legal advice.** Frame every finding as something for the attorney to verify and
  decide. Do not state legal conclusions or recommend a course of action as if advising.
- **Cite locations.** Tie each finding to a section, clause, or page so it can be checked.
- **Do not fabricate.** If a clause, date, or party is unclear or absent, say so
  explicitly rather than inferring.
- **Read-only and confidential.** Do not alter, send, or share the document. Treat all
  contents as privileged and confidential; keep them within the firm's own environment.
