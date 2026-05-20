# PRD: Natural-Language Scheduling

*A deliberately incomplete PRD — run the `prd-reviewer` skill on it and watch the checklist fire. It passes some checks and fails others on purpose.*

---

## Hypothesis
Letting users schedule meetings in plain language ("book 30 min with Sarah next week") will cut the time-to-schedule and reduce scheduling support tickets.

## Problem
Scheduling across calendars is the #2 source of support tickets (1,240 last quarter). Users bounce between the calendar grid and email; 38% of scheduling attempts are abandoned mid-flow (product analytics, Q1).

## Solution
An AI assistant that parses a natural-language request, checks attendee availability via the Google Calendar API, and proposes a slot to confirm. One screen, one confirm.

## Success Metrics
- Scheduling abandonment drops from 38% to under 20% within 6 weeks of GA.
- Median time-to-schedule under 30 seconds.

## Rollout
Ship behind a flag to the internal dogfood group first.

<!--
On purpose, this PRD is MISSING:
- Non-goals (no scope boundary — e.g. is Outlook in or out?)
- Kill criteria (when do we roll back?)
- A complete rollout plan with ramp gates (only "dogfood", no % gates)
- For the AI feature: a behavior contract with examples, and eval criteria
Run prd-reviewer and it should flag these and return NOT READY (check 4 fails).
-->
