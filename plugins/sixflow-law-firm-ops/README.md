# SixFlow Law Firm Ops

An AI operations assistant for law firms. It turns a connected inbox and calendar into a
prioritized daily brief that surfaces new client leads first, flags time-sensitive
deadlines, and tells the team the top actions for the day - delivered to their inbox
automatically each morning. It also reviews legal documents to surface what matters.

Built by SixFlow - https://sixflow.ai

## What it does

- **Automatic morning brief** - emails the firm a daily briefing (today's schedule +
  prioritized inbox digest + top actions) at a set time each morning.
- **Inbox digest** - on-demand prioritized summary of the inbox and calendar.
- **Document review** - reads a legal document and surfaces parties, dates and deadlines,
  key terms, and risk clauses for an attorney's review.
- **Guided onboarding** - step-by-step setup that connects the firm's tools, imports
  context from their previous AI, and tailors the assistant to how the firm works.

## Components

| Type  | Name              | What it does                                                          |
| ----- | ----------------- | -------------------------------------------------------------------- |
| Skill | `onboarding`      | First-time setup: profile, AI-context import, connect tools, schedule. |
| Skill | `morning-brief`   | Compile day's schedule + inbox digest and email it to the firm daily.|
| Skill | `inbox-digest`    | On-demand prioritized digest of the inbox and calendar.              |
| Skill | `document-review` | Surface legally-relevant elements and risks from a document.         |

## Setup

1. Install the plugin.
2. Run **onboarding** (type `/onboarding` or say "onboard me").
3. Load your firm profile, import your previous AI's context, and connect email + calendar.
4. Set your morning brief time and recipients.

## Usage

- "Onboard me" / `/onboarding` - run first-time setup.
- "Send my morning brief" - generate and email the daily brief now.
- "Give me my inbox digest" - on-demand digest.
- "Review this document" - legal document review.

## Customization

Personalized per firm through a `CLAUDE.md` file in the firm's workspace - firm name,
practice areas, key people, priorities, urgency rules, and the morning-brief recipients.
Tool references use category placeholders (`~~email`, `~~calendar`, `~~documents`) so the
plugin works with whichever providers the firm connects. See `CONNECTORS.md`.

## Privacy

The assistant is read-only on email, calendar, and documents. The single exception is the
Morning Brief, which is emailed only to the firm's own pre-approved internal recipients.
It never sends, replies, forwards, or deletes anything else without explicit per-action
approval, and client data stays within the firm's own connected accounts.
