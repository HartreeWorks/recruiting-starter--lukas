# Recruiting assistant

A Claude Code project with skills to automate recruiting workflows. Clone it, configure it for your setup, and iterate.

## What's included

**Skills:**
- `/lookup-candidate` - Research a candidate's background
- `/draft-outreach` - Write a personalized recruiting email
- `/draft-followup` - Write a follow-up email
- `/find-email` - Find a candidate's email address
- `/check-pipeline` - Review your candidate pipeline
- `/update-candidate` - Update a candidate's status in Airtable

**Templates:**
- `templates/initial-outreach.md` - Example cold outreach email
- `templates/follow-up.md` - Follow-up email templates

**Examples:**
- `examples/airtable-schema.md` - Suggested Airtable base structure

## Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed and working

## Optional: Airtable MCP setup

The pipeline management skills (`/check-pipeline`, `/update-candidate`) work best with Airtable. Here's how to set it up.

### 1. Create an Airtable base

Create a new base with a "Candidates" table. See `examples/airtable-schema.md` for the recommended schema.

### 2. Get your Airtable credentials

1. Go to [airtable.com/create/tokens](https://airtable.com/create/tokens)
2. Click "Create new token"
3. Give it a name like "Claude Code"
4. Add scopes:
   - `data.records:read`
   - `data.records:write`
   - `schema.bases:read`
5. Add access to your recruiting base
6. Create the token and copy it

Also note your Base ID - you can find it in the URL when viewing your base:
```
https://airtable.com/appXXXXXXXXXXXXXX/...
         ^^^^^^^^^^^^^^^^^^
         This is your Base ID
```

### 3. Install the Airtable MCP server

```bash
# Using npx (no install needed)
npx -y @airtable/mcp-server
```

### 4. Configure Claude Code

Add to your `~/.claude.json` (or project `.claude.json`):

```json
{
  "mcpServers": {
    "airtable": {
      "command": "npx",
      "args": ["-y", "@airtable/mcp-server"],
      "env": {
        "AIRTABLE_API_KEY": "your_token_here"
      }
    }
  }
}
```

Or use environment variables:

```bash
export AIRTABLE_API_KEY="your_token_here"
```

### 5. Test it

Restart Claude Code and try:
```
/check-pipeline
```

If Airtable is configured correctly, it will query your candidates table.

## Optional: Gmail setup

If you want `/draft-outreach` to create Gmail drafts directly, set up the Google Workspace MCP server. See the [Google Workspace MCP documentation](https://github.com/anthropics/anthropic-quickstarts/tree/main/mcp-server-google-workspace).

Without Gmail MCP, the skills will just output the email text for you to copy.

## Customisation

**Edit these files to match your needs:**

1. **`CLAUDE.md`** - Update the organisation context, tone guidelines, and any specific instructions
2. **`templates/`** - Customise the email templates for your roles and voice
3. **`examples/airtable-schema.md`** - Adjust the schema if you need different fields

## Usage examples

```bash
# Research a candidate
/lookup-candidate Jane Smith

# Find their email
/find-email Jane Smith Anthropic

# Draft an outreach email
/draft-outreach Jane Smith

# Check who needs follow-up
/check-pipeline

# Update a candidate's status
/update-candidate Jane Smith "Scheduled" "Call booked for Friday"

# Send a follow-up
/draft-followup Jane Smith
```

## Tips

- Start with `/lookup-candidate` to research someone before reaching out
- The skills work without Airtable - you just won't have pipeline tracking
- Edit templates based on what gets responses
- Add notes to candidate records to help with future personalisation
