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

## If Airtable is not configured

Explain that this skill requires Airtable MCP to be set up. Point to the README for setup instructions.

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
