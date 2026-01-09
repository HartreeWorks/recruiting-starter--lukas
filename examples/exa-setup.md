# Exa MCP setup for enhanced candidate research

[Exa](https://exa.ai) is an AI-powered search engine that's particularly good at finding information about people, companies, and technical topics. It's better than basic web search for candidate research.

## Why use Exa?

- **Semantic search** - Understands what you're looking for, not just keyword matching
- **Better at finding people** - Good at surfacing LinkedIn profiles, papers, GitHub, etc.
- **Structured results** - Returns clean, relevant content

## Setup

### 1. Get an Exa API key

1. Sign up at [exa.ai](https://exa.ai)
2. Go to your dashboard and create an API key
3. Note: Exa has a free tier for testing, then ~$1/1000 searches

### 2. Install the Exa MCP server

The Exa MCP server allows Claude Code to use Exa for searches.

```bash
npm install -g @anthropic/exa-mcp-server
```

Or check for the latest installation method in the [Exa MCP documentation](https://github.com/exa-labs/exa-mcp-server).

### 3. Configure Claude Code

Add to your `~/.claude.json` (or project `.claude.json`):

```json
{
  "mcpServers": {
    "exa": {
      "command": "npx",
      "args": ["-y", "@anthropic/exa-mcp-server"],
      "env": {
        "EXA_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

Or use environment variables:

```bash
export EXA_API_KEY="your_api_key_here"
```

### 4. Test it

Restart Claude Code and try:

```
/lookup-candidate [Someone's name]
```

If Exa is configured, the lookup will use Exa's AI search for more comprehensive results.

## What Exa helps with

When researching candidates, Exa is particularly good at finding:

- LinkedIn profiles (even without direct LinkedIn API access)
- Academic papers and publications
- GitHub profiles and repositories
- Blog posts and personal websites
- Conference talks and presentations
- News mentions

## Cost considerations

- Free tier: Limited searches for testing
- Paid: ~$1 per 1000 searches (very reasonable for recruiting)
- Each `/lookup-candidate` typically uses 3-5 searches

## Without Exa

The `/lookup-candidate` skill still works without Exa - it falls back to Claude's built-in web search. Exa just provides better, more comprehensive results.
