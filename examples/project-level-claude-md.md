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
- Tag @jake-torres on every PR and link this folder's PLANNING.md. (Lived in the global CLAUDE.md briefly, then pruned here — see that prune commit.)
- All API calls cached 5 minutes minimum
- Tests use data/test-events.json — synthetic events only. Real attendee data is PII; keep it in data/exports/ (git-ignored), never in a commit.
- Screenshot every UI change for PR description
