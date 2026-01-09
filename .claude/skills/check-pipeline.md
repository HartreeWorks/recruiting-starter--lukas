---
description: Review your recruiting pipeline and see who needs attention. Use daily to stay on top of follow-ups.
---

# Check pipeline

Review the recruiting pipeline and identify candidates who need attention.

## What to show

### 1. Needs follow-up (priority)
Candidates where:
- Status is "Outreach Sent" or "Responded"
- Next Action date is today or earlier

Show: Name, status, days since last contact, last note

### 2. Upcoming
Candidates where:
- Next Action date is in the next 7 days

Show: Name, status, next action date, brief context

### 3. Pipeline summary
Count of candidates by status:
```
Researching:     X
Outreach Sent:   X
Responded:       X
Scheduled:       X
Interviewing:    X
Offer:           X
```

### 4. Stale candidates
Candidates where:
- Status is active (not Declined/Not Interested/Hired)
- Last Contact is >14 days ago
- No Next Action set

## Output format

```
## Pipeline check - [Date]

### Needs attention now
1. **[Name]** - [Status] - [X days since contact]
   Last: [brief note]

2. **[Name]** - [Status] - [X days since contact]
   Last: [brief note]

### Coming up this week
- [Name] - [Next Action date] - [Context]
- [Name] - [Next Action date] - [Context]

### Summary
| Status | Count |
|--------|-------|
| Researching | X |
| Outreach Sent | X |
| ... | ... |

### Going stale (no recent activity)
- [Name] - [X days] - Consider: follow up or close out?
```

## Data source

### Option 1: Airtable (if MCP is configured)

Query the Candidates table in Airtable.

### Option 2: Local JSON (fallback)

If Airtable MCP is not available, read from `pipeline.json` in the project root:

1. Read `pipeline.json`
2. Parse the `candidates` array
3. Calculate days since `lastContact` for each candidate
4. Filter and sort according to the criteria above
5. Display in the same format

The JSON structure:
```json
{
  "candidates": [
    {
      "name": "Jane Smith",
      "email": "jane@example.com",
      "company": "Anthropic",
      "role": "ML Engineer",
      "status": "Outreach Sent",
      "lastContact": "2025-01-09",
      "nextAction": "2025-01-16",
      "notes": "Found via GitHub.",
      "source": "GitHub"
    }
  ]
}
```

### If neither is available

If `pipeline.json` doesn't exist or is empty, explain that no candidates are being tracked yet. Suggest:
- `/add-candidate [Name]` to start tracking someone
- See README for Airtable setup if they want a more robust solution

## Actions to offer

After showing the pipeline:
1. `/draft-followup [Name]` - For candidates needing follow-up
2. `/lookup-candidate [Name]` - To research before outreach
3. `/update-candidate [Name] [Status]` - To update status

## Optional filters

If the user provides arguments:
- `/check-pipeline outreach` - Only show "Outreach Sent" candidates
- `/check-pipeline scheduled` - Only show "Scheduled" candidates
- `/check-pipeline stale` - Only show stale candidates
