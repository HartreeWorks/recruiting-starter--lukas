# Recruiting assistant

A Claude Code project with skills to automate recruiting workflows. Clone it, configure it for your setup, and iterate.

## What's included

**Skills:**
- `/lookup-candidate` - Research a candidate's background
- `/draft-outreach` - Write a personalised recruiting email
- `/draft-followup` - Write a follow-up email
- `/find-email` - Find a candidate's email address
- `/add-candidate` - Add someone to your pipeline
- `/check-pipeline` - Review your candidate pipeline
- `/update-candidate` - Update a candidate's status

**Templates:**
- `templates/initial-outreach.md` - Example cold outreach email
- `templates/follow-up.md` - Follow-up email templates

**Examples:**
- `examples/airtable-schema.md` - Suggested Airtable base structure
- `examples/exa-setup.md` - Enhanced research with Exa AI search

**Data:**
- `pipeline.json` - Local candidate tracking (no setup required)

## Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed and working

## Pipeline tracking

Two options for tracking candidates:

### Option 1: Local JSON (no setup required)

The repo includes `pipeline.json` - a simple JSON file that stores your candidates locally. The skills automatically use this if Airtable isn't configured.

```bash
# Add a candidate
/add-candidate Jane Smith

# Check your pipeline
/check-pipeline

# Update status
/update-candidate Jane Smith "Outreach Sent"
```

The JSON file is human-readable and you can edit it directly if needed. Good for getting started or if you prefer keeping data local.

### Option 2: Airtable (more features)

For a more robust setup with views, filters, and collaboration, use Airtable.

#### 1. Create an Airtable base

Create a new base with a "Candidates" table. See `examples/airtable-schema.md` for the recommended schema.

#### 2. Get your Airtable credentials

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

#### 3. Install the Airtable MCP server

```bash
# Using npx (no install needed)
npx -y @airtable/mcp-server
```

#### 4. Configure Claude Code

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

#### 5. Test it

Restart Claude Code and try:
```
/check-pipeline
```

If Airtable is configured correctly, it will query your candidates table.

## Optional: Gmail setup

Two options for sending emails directly from Claude Code:

### Option 1: Send-email skill (recommended)

The easiest approach - takes ~5 minutes to set up. Uses Gmail's SMTP servers.

1. Clone the skill into your `.claude/skills/` folder:
   ```bash
   git clone https://github.com/HartreeWorks/skill--send-email.git .claude/skills/send-email
   ```
2. Follow the setup instructions in that repo to configure Gmail SMTP credentials

Then you can use `/send-email` to send emails directly.

### Option 2: Google Workspace MCP

A more comprehensive integration that also gives you calendar, drive, and other Google services. Takes ~20 minutes to set up.

See the [Google Workspace MCP setup guide](https://wow.pjh.is/journal/claude-code-google-workspace-mcp).

### Without email integration

The skills will just output email text for you to copy and paste into Gmail.

## Optional: Enhanced research with Exa

The `/lookup-candidate` skill works with standard web search, but you can get much better results with [Exa](https://exa.ai) - an AI-powered search engine that's particularly good at finding information about people.

With Exa configured, candidate research will find:
- LinkedIn profiles more reliably
- Academic papers and publications
- GitHub profiles and open source work
- Conference talks and presentations

Setup takes ~10 minutes. See `examples/exa-setup.md` for instructions.

## Customisation

**Edit these files to match your needs:**

1. **`CLAUDE.md`** - Update the organisation context, tone guidelines, and any specific instructions
2. **`templates/`** - Customise the email templates for your roles and voice
3. **`examples/airtable-schema.md`** - Adjust the schema if you need different fields

## Usage examples

```bash
# Research a candidate
/lookup-candidate Jane Smith

# Add them to your pipeline
/add-candidate Jane Smith

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
- Pipeline tracking works out of the box with `pipeline.json` - no setup required
- Upgrade to Airtable later if you want views, filters, and collaboration
- Edit templates based on what gets responses
- Add notes to candidate records to help with future personalisation
