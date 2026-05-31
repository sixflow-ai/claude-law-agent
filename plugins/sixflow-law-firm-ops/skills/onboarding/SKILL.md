---
name: onboarding
description: >
  This skill should be used when the user types "/onboarding", or says "onboard me",
  "set up", "get started", "connect my tools", "first time setup", or "help me get
  this running". It walks a law firm through loading their firm profile, importing
  context from their previous AI, connecting their email and calendar, and producing
  a first inbox digest.
metadata:
  version: "0.2.0"
  author: "SixFlow"
---

# Onboarding

Guide a law firm through first-time setup of the SixFlow Law Firm Ops assistant. The
user is a busy, likely non-technical legal professional. Keep every step plain-language,
short, and reassuring. Do one step at a time and wait for confirmation before moving on.

## Goal

By the end, the firm will have: their firm profile loaded, useful context imported from
their previous AI tool, email and calendar connected, and one inbox digest produced.

## Run these steps in order

### Step 1 - Welcome and set expectations

Greet the user. Explain setup takes about five to ten minutes and has a few parts: load
their firm profile, bring over what their old AI already knows, connect email and
calendar, and run a first digest. Reassure them the assistant is read-only by default
and never sends or deletes anything without their explicit approval. Then begin.

### Step 2 - Load the firm profile

SixFlow prepares a tailored firm profile (a CLAUDE.md) for each firm.

- If a CLAUDE.md is already present in the workspace, open it and confirm the details
  with the user.
- If it is not present, ask the user to paste the firm profile text SixFlow sent them,
  then save it to the workspace as CLAUDE.md.
- If they have nothing to paste, fall back to asking a few short questions (firm name,
  practice areas, key people, what counts as "urgent") and write the answers to CLAUDE.md.

### Step 3 - Import context from your previous AI

Explain the benefit plainly: "If you have used another AI tool (like ChatGPT, Gemini,
Copilot, or Claude), we can bring over what it already knows about your firm so this
assistant starts up to speed instead of from scratch."

Give the user this exact message to copy and paste into their current AI tool. Present
it verbatim in a code block so they can copy it:

```
Please give me a complete, high-level summary of everything you know about me and my
business - pulling from your saved memory and our past conversations. Include: who I am
and my role, my company and what it does, our main goals and current priorities,
ongoing projects, the tools and systems we use, key people I work with, how I prefer to
communicate and work, and any recurring issues or important context you have saved. Lay
it out in clear sections so I can hand it to another AI assistant to get up to speed.
```

Tell them to run that in their old AI, copy the response, and paste it back here.

When they paste it:

- Pull out the details that help this assistant do its job - firm facts, priorities,
  key people, tools, recurring issues, and work/communication preferences.
- Ignore anything irrelevant or sensitive-personal that does not serve the firm's operations.
- Show the user the items you plan to keep, get their confirmation, and append them to
  CLAUDE.md under a clearly marked "## Imported context" section.

If the user skips this step, continue - it is optional.

### Step 4 - Connect email (~~email)

Explain the assistant needs read access to their inbox to build the daily digest, and
that it only reads - never sends or deletes without explicit approval. Direct them to
connect their email connector in Cowork:

- Open the connectors / tools settings in the Cowork app.
- Search for their email provider (for example, Gmail or Outlook).
- Authorize access when prompted.

Do not attempt to connect, authenticate, or enter credentials on the user's behalf. The
user completes the authorization themselves through the provider's official sign-in.
Once they say it is connected, confirm by listing a few recent message subjects
(read-only). If it fails, help them recheck the connection.

### Step 5 - Connect calendar (~~calendar)

Explain that calendar access lets the digest flag court dates, filing deadlines, and
meetings. Direct them to connect their calendar connector the same way. Confirm by
reading the next few upcoming events (read-only).

### Step 6 - Produce a first digest

Run the inbox-digest skill once against their connected inbox so they see real output.
Walk through it and ask whether the prioritization matches how their firm thinks about
urgency. Adjust the rules in CLAUDE.md based on their feedback.

### Step 7 - Set up the automatic morning brief

Offer to have the assistant email a Morning Brief automatically each day - the day's
schedule plus the inbox digest.

- Confirm the send time (default 8:00 AM).
- Confirm who should receive it. These must be the firm's own internal addresses. Save
  them under "Daily brief settings" in CLAUDE.md.
- Create a scheduled task that runs the morning-brief skill at that time.
- Reassure them: the brief is emailed only to these approved internal recipients - never
  to clients or anyone else - and nothing else is ever sent automatically.

## Guardrails

- Never enter passwords or complete sign-in flows for the user. Connections are
  authorized by the user directly through the provider's official screen.
- The assistant reads email and calendar data. It must never send, reply, delete, or
  modify anything without explicit per-action confirmation.
- Treat imported context and all client data as confidential. Keep it within the firm's
  own workspace and connected accounts; do not export or transmit it elsewhere.
