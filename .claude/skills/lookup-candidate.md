---
description: Research a candidate's background for recruiting outreach. Use when you want to learn about someone before reaching out or personalising an email.
---

# Lookup candidate

Research **$ARGUMENTS** (candidate name, optionally with company) and compile a summary useful for recruiting outreach.

## Search method

### If Exa MCP is available (recommended)

Use Exa's AI-powered search for more comprehensive results. Exa is better at:
- Finding LinkedIn profiles
- Surfacing academic papers
- Locating GitHub profiles
- Finding personal websites and blogs

Run multiple targeted Exa searches:
1. `[Name] [Company] LinkedIn profile`
2. `[Name] research papers publications`
3. `[Name] GitHub developer`
4. `[Name] [Company] interview talk presentation`

### Fallback: Standard web search

If Exa is not available, use standard web search. Results may be less comprehensive.

## What to find

Search for:

1. **Current role** - Where they work, what they do, how long they've been there
2. **Background** - Previous roles, education, career trajectory
3. **Technical work** - Papers, projects, open source contributions, talks
4. **Online presence** - LinkedIn, GitHub, Twitter/X, personal website
5. **Interests & angles** - What they seem to care about, potential connection points

## Output format

Present findings in this structure:

```
## [Name]

**Current:** [Role] at [Company] (since [date if known])

**Background:**
- [Previous role 1]
- [Previous role 2]
- [Education]

**Technical work:**
- [Notable paper/project 1]
- [Notable paper/project 2]

**Online:**
- LinkedIn: [url]
- GitHub: [url]
- Twitter: [url]
- Website: [url]

**Potential angles:**
- [Observation about their interests or work that could be relevant to our roles]
- [Another connection point]

**Notes:**
- [Anything else relevant - recent news, mutual connections, etc.]
```

## Guidelines

- Focus on information useful for personalising outreach
- Note specific projects or papers, not just "extensive research experience"
- Look for connection points to AI safety/security work
- If information is sparse, note what couldn't be found
- Don't make up information - only include what you can verify

## After researching

Offer to save the findings:

- **If Airtable MCP is available**: Create or update a candidate record in Airtable
- **If using local JSON**: Create or update an entry in `pipeline.json` via `/add-candidate` or `/update-candidate`

This keeps research organised and available for drafting outreach later.
