---
name: inbox-digest
description: >
  This skill should be used when the user asks for an "inbox digest", "daily digest",
  "morning digest", "summarize my inbox", "what's in my email", "catch me up on email",
  or "what needs my attention today". It reads the firm's connected email and calendar
  and produces a prioritized, action-oriented summary for a law firm.
metadata:
  version: "0.1.0"
  author: "SixFlow"
---

# Inbox Digest

Produce a prioritized daily digest of a law firm's inbox so the team sees what matters first: new potential clients, time-sensitive matters, and approaching deadlines. Read-only — never send, reply to, or delete anything without explicit user approval.

## Before generating

Load the firm's context from the project's `CLAUDE.md`: practice areas, key people, what the firm treats as "urgent", and any firm-specific rules. Apply those rules when prioritizing. If `CLAUDE.md` is missing key details, proceed with the defaults below and note what was assumed.

## Steps

1. Pull recent messages from `~~email` (default: unread plus everything received in the last 24 hours; adjust to the user's stated window).
2. Pull upcoming events from `~~calendar` for the next 7 days.
3. Classify each message into the priority tiers below.
4. Cross-reference deadlines and court dates against the calendar.
5. Output the digest in the format below.

## Priority tiers (highest first)

1. **New potential clients / leads** — inbound inquiries from people who are not existing contacts: contact-form notifications, referral intros, "do you handle…" questions. Speed-to-lead wins cases, so these come first. Flag how long each has been waiting.
2. **Time-sensitive legal deadlines** — anything referencing a statute of limitations, filing deadline, court date, hearing, or response due date. Cross-check against the calendar and flag conflicts or anything with no calendar entry.
3. **Active client matters** — messages from existing clients needing a response or action.
4. **Opposing counsel / courts / third parties** — communications that affect a matter.
5. **Administrative / low priority** — vendors, newsletters, internal notes. Summarize briefly or group.

## Output format

Open with a one-line situational summary (for example: "3 new leads, 2 deadlines this week, 1 needs a same-day reply").

Then, for each tier that has items:

- **Tier heading**
- For each item: sender, one-line summary, why it matters, and a recommended next action. For leads, include time waiting. For deadlines, include the date and whether it is on the calendar.

End with **"Top 3 actions today"** — the three highest-impact things to do, in order.

## Rules

- Read-only. Do not send, reply, forward, archive, or delete without explicit per-action confirmation.
- Do not fabricate emails, deadlines, or senders. If a date or detail is ambiguous, say so rather than guessing.
- Treat all client information as confidential. Keep it within the firm's connected accounts; never export or transmit it elsewhere.
- Respect the urgency rules defined in the firm's `CLAUDE.md` over these defaults where they conflict.
