# Airtable schema for recruiting

Create a base called "Recruiting" with a table called "Candidates".

## Fields

| Field | Type | Notes |
|-------|------|-------|
| Name | Single line text | Full name (primary field) |
| Email | Email | Work or personal email |
| Personal Email | Email | Optional backup |
| Company | Single line text | Current employer |
| Role | Single line text | Current job title |
| LinkedIn | URL | LinkedIn profile link |
| Status | Single select | Pipeline stage (see options below) |
| Last Contact | Date | Date of most recent interaction |
| Next Action | Date | When to follow up |
| Notes | Long text | Conversation notes, research, context |
| Source | Single select | How you found them |
| Priority | Single select | High / Medium / Low |
| Created | Created time | Auto-populated |

## Status options

Configure the Status field with these options:

- **Researching** - Looking into them, haven't reached out
- **Outreach Sent** - Initial email sent, awaiting response
- **Responded** - They replied, conversation started
- **Scheduled** - Call or meeting booked
- **Interviewing** - In active interview process
- **Offer** - Offer extended
- **Hired** - Accepted and starting
- **Declined** - They declined to proceed
- **Not Interested** - We decided not to pursue
- **On Hold** - Timing not right, revisit later

## Source options

- Referral
- LinkedIn
- Conference
- Paper/Publication
- GitHub
- Twitter/X
- Job Application
- Other

## Views to create

**1. Pipeline (Kanban)**
- Group by Status
- Useful for seeing overall pipeline health

**2. Needs Follow-up**
- Filter: Status is "Outreach Sent" or "Responded"
- Filter: Next Action is on or before today
- Sort by Next Action (ascending)

**3. Active Conversations**
- Filter: Status is not "Declined", "Not Interested", "Hired", "On Hold"
- Sort by Last Contact (descending)

**4. Research Queue**
- Filter: Status is "Researching"
- Sort by Created (ascending)

## Tips

- Set "Next Action" when you send an email (typically 5-7 days out)
- Update Notes after every interaction
- Use the "Needs Follow-up" view daily
- Archive (mark "Not Interested") rather than delete - you might want the record later
