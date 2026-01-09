---
description: Write a personalised recruiting outreach email. Use after researching a candidate with /lookup-candidate.
---

# Draft outreach

Write a personalised outreach email for **$ARGUMENTS** (candidate name).

## Before drafting

1. **Check for existing research** - If we haven't looked up this candidate yet, run `/lookup-candidate` first
2. **Check Airtable** (if available) - Look for existing notes on this candidate
3. **Read templates** - Review `templates/initial-outreach.md` for structure

## Writing the email

Use the candidate research to personalise the message. Follow the guidelines in CLAUDE.md.

Key principles:
- Reference something **specific** about their work
- Be **direct** about why you're reaching out
- Be **honest** about the role and organisation
- Keep it **short** (under 150 words)
- One clear **ask** (usually: a 20-minute call)

## Output format

```
**To:** [email if known, or "TBD"]
**Subject:** [subject line]

---

[Email body]

---

**Notes:**
- [Why this personalisation angle was chosen]
- [Any concerns or things to adjust]
```

## After drafting

Offer these options:
1. **Revise** - Make changes based on feedback
2. **Create Gmail draft** - If Gmail MCP is available, create a draft in Gmail
3. **Update Airtable** - If Airtable is available, update candidate status to "Outreach Sent" and log the email

## What NOT to do

- Don't use generic praise ("your impressive background")
- Don't be overly enthusiastic ("We're SO excited!")
- Don't write long emails
- Don't include attachments or links in first email
- Don't copy template language verbatim - adapt it
