---
description: Add a new candidate to your pipeline. Use after researching someone you want to track.
---

# Add candidate

Add **$ARGUMENTS** (candidate name) to the pipeline.

## Information to gather

Before adding, collect:
- **Name** (required)
- **Email** (if known)
- **Company** (current employer)
- **Role** (current title)
- **Source** (how you found them)
- **Notes** (any context from research)

If information is missing, ask for it or note as "Unknown".

## Adding to pipeline

### If Airtable MCP is available

Create a new record in the Candidates table with:
- Name, Email, Company, Role
- Status: "Researching"
- Source
- Notes
- Last Contact: null (haven't reached out yet)

### If using local JSON (pipeline.json)

1. Read `pipeline.json` from the project root
2. Add a new entry to the `candidates` array:

```json
{
  "name": "[Name]",
  "email": "[Email or null]",
  "company": "[Company]",
  "role": "[Role]",
  "status": "Researching",
  "lastContact": null,
  "nextAction": null,
  "notes": "[Notes from research]",
  "source": "[Source]"
}
```

3. Write the updated JSON back to `pipeline.json`

## Output format

```
✓ Added [Name] to pipeline
  Company: [Company]
  Role: [Role]
  Status: Researching
  Source: [Source]

Next: /lookup-candidate [Name] to research, or /draft-outreach [Name] when ready
```

## If candidate already exists

Check if a candidate with the same name already exists:
- If yes, ask if they want to update the existing record or add a duplicate
- Suggest `/update-candidate` for existing records

## Workflow integration

After adding a candidate, suggest:
1. `/lookup-candidate [Name]` - Research their background
2. `/find-email [Name] [Company]` - Find their contact info
3. `/draft-outreach [Name]` - When ready to reach out
