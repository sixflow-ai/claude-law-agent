---
name: morning-brief
description: >
  This skill should be used when the user says "morning brief", "daily brief",
  "daily rundown", "send my morning brief", and it is the skill run by the scheduled
  daily briefing task. It compiles the day's calendar and a prioritized inbox digest
  into one briefing and emails it to the firm's designated internal recipients.
metadata:
  version: "0.1.0"
  author: "SixFlow"
---

# Morning Brief

Compile a single daily briefing - the day's schedule plus a prioritized inbox digest -
and email it to the firm's designated internal recipients. Designed to run automatically
each morning via a scheduled task, and also on demand.

## Before running

Load the firm's CLAUDE.md: practice areas, urgency rules, and the "Daily brief settings"
(recipients and send time). If no brief recipients are set, ask the user once, then save
them to CLAUDE.md before sending anything.

## Build the brief

1. Calendar (~~calendar): pull today's events - court dates, hearings, filing deadlines,
   meetings. Flag conflicts and anything that has no preparation time blocked.
2. Inbox (~~email): apply the inbox-digest prioritization - new potential clients first,
   then time-sensitive deadlines, active client matters, then the rest.
3. Cross-reference any deadlines found in email against the calendar; flag mismatches.

## Compose

Write a clean, skimmable email:

- Subject: "[Firm] Morning Brief - <today's date>"
- One-line situational summary (e.g., "2 court dates today, 3 new leads, 1 needs a same-day reply").
- **Today's schedule** - times, what each is, and any prep needed.
- **Deadlines this week** - date, matter, and whether it is on the calendar.
- **New leads** - sender, summary, and how long they have been waiting.
- **Needs a response today** - existing client matters that are time-sensitive.
- **Top 3 actions** - the highest-impact things to do, in order.

Plain English, skimmable, no legalese.

## Deliver by email

Send the brief by email to ONLY the recipients listed under "Daily brief settings" in
CLAUDE.md.

- This is the one sanctioned automated send. It sends only the brief, and only to these
  pre-approved internal firm addresses.
- Never send to clients, opposing parties, or any address not on the approved list.
- Never reply to, forward, or modify any client email. Compose a brand-new internal
  brief email only.
- If the connected email account is read-only and cannot send, post the brief in the
  workspace instead and tell the user how to enable sending.

## Rules

- Read-only on all sources except the single outbound brief email to approved recipients.
- Do not fabricate events, deadlines, or leads. Where a detail is unclear, flag it.
- Confidential: keep all content within the firm's own accounts; recipients are limited
  to the approved internal list.
