---
description: Update a candidate's status in your pipeline. Use after sending an email, having a call, or when their status changes.
---

# Update candidate

Update the record for **$ARGUMENTS** (candidate name, new status, and optionally notes).

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

## Data source

### Option 1: Airtable (if MCP is configured)

Update the record in the Candidates table.

### Option 2: Local JSON (fallback)

If Airtable MCP is not available, update `pipeline.json`:

1. Read `pipeline.json`
2. Find the candidate by name (case-insensitive match)
3. Update the fields:
   - `status`: new status value
   - `lastContact`: today's date (ISO format: "2025-01-09")
   - `nextAction`: calculated based on status (see above)
   - `notes`: append new notes to existing (with date prefix)
4. Write the updated JSON back to `pipeline.json`

Example notes format:
```
"notes": "Previous notes...\n\n[2025-01-09] New note added here"
```

## Output format

```
✓ Updated [Name]
  Status: [Old] → [New]
  Last Contact: [Date]
  Next Action: [Date or "cleared"]
  Notes: [Added note if any]
```

## Error handling

If the candidate isn't found:
1. Search for similar names (typos, partial matches)
2. Offer to create a new record with `/add-candidate`
3. If creating, ask for required fields (email, company)
