---
description: Find a candidate's email address. Use when you have a name and company but need their contact info.
---

# Find email

Find the email address for **$ARGUMENTS** (name and company).

## Approach

Try these methods in order:

### 1. Direct search
Search for:
- "[Name] [Company] email"
- "[Name] contact"
- "[Name] [Company]" site:linkedin.com (check for email in profile)

### 2. Company patterns
Most companies use predictable email formats. Common patterns:
- firstname.lastname@company.com
- firstnamelastname@company.com
- firstname@company.com
- first.last@company.com
- flastname@company.com

### 3. GitHub/personal sites
Check their:
- GitHub profile (email sometimes in commits or profile)
- Personal website (often has contact info)
- Twitter/X bio

### 4. Academic
For researchers:
- University faculty page
- Paper author info
- Google Scholar profile

## Output format

```
## Email search: [Name] at [Company]

**Most likely:**
- [email] - [confidence: high/medium/low] - [source/reasoning]

**Alternatives:**
- [email] - [confidence] - [source]

**Pattern-based guesses** (unverified):
- [email] - based on [Company] using [pattern]

**Couldn't find:**
- [What didn't work]
```

## Confidence levels

- **High** - Found directly on their profile, website, or paper
- **Medium** - Matches company pattern and name is unique
- **Low** - Pattern guess, or common name at large company

## Notes

- If you find both work and personal emails, include both
- Note if an email looks outdated (old company, etc.)
- Don't guess at emails for common names without verification
- If the company has unusual domain(s), note them
