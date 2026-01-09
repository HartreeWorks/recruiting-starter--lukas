---
description: Update a candidate's status in Airtable. Use after sending an email, having a call, or when their status changes.
---

# Update candidate

Update the Airtable record for **$ARGUMENTS** (candidate name, new status, and optionally notes).

## Expected input format

```
/update-candidate [Name] [Status] [Notes (optional)]
```

Examples:
- `/update-candidate Jane Smith "Outreach Sent"`
- `/update-candidate Jane Smith "Scheduled" "Call booked for Friday 2pm"`
- `/update-candidate Jane Smith "Declined" "Not interested in government work"`

## Valid status values

- Researching
- Outreach Sent
- Responded
- Scheduled
- Interviewing
- Offer
- Hired
- Declined
- Not Interested
- On Hold

## What to update

1. **Status** - Update to the new status
2. **Last Contact** - Set to today's date
3. **Notes** - Append any new notes (don't overwrite existing)
4. **Next Action** - Set based on status:
   - Outreach Sent → +7 days
   - Scheduled → date of call
   - Responded → +3 days (to reply)
   - Other statuses → clear or leave as-is

## If Airtable is not configured

Explain that this skill requires Airtable MCP to be set up. Point to the README for setup instructions.

## Output format

```
✓ Updated [Name]
  Status: [Old] → [New]
  Last Contact: [Date]
  Next Action: [Date or "cleared"]
  Notes: [Added note if any]
```

## Error handling

If the candidate isn't found in Airtable:
1. Search for similar names (typos, partial matches)
2. Offer to create a new record
3. If creating, ask for required fields (email, company)
