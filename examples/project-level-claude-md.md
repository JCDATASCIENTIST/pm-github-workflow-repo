# Example: Project-Level CLAUDE.md

*Goes inside a project folder. Claude reads both root CLAUDE.md AND this file.*

---

# Calendar Integration Project

## Context
- PRD: see PLANNING.md in this folder
- Status: In development, targeting June 15 launch
- Engineer lead: Jake Torres (prefers detailed tickets with acceptance criteria)

## Technical Constraints
- Google Calendar API only (no Outlook in v1)
- Rate limit: 10 requests/user/minute
- Must work with existing OAuth flow
- Store in UTC, display in user's local timezone

## Eval Criteria
- See evals/calendar-integration-criteria.md
- Baseline: 0.72
- Target: 0.85 before rollout to 10%

## Rules (project-specific)
- All API calls cached 5 minutes minimum
- No mock data in commits, use data/test-events.json
- Screenshot every UI change for PR description
