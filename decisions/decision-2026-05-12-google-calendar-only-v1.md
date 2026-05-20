# Decision: Google Calendar only for Calendar Integration v1

**Date:** 2026-05-12
**Status:** Accepted
**Owner:** Jake Torres (Calendar PM)
**Deciders:** Calendar PM, Eng lead, Design lead

*This is the decision-log format the [Team OS](https://www.news.aakashg.com/p/claude-code-team-os) shared repo uses (`decisions/` folder). One file per call, dated, so the "why" survives after the people who made it move on. Referenced by `evals/calendar-integration-criteria.md` and `examples/project-level-claude-md.md`.*

## Context
The natural-language scheduling feature (see `examples/sample-prd.md`) needs a calendar backend. ~74% of our active accounts authenticate with Google Workspace; ~19% use Microsoft 365; the rest are mixed.

## Decision
Ship v1 against the **Google Calendar API only**. Outlook/Microsoft 365 is an explicit non-goal for v1.

## Why
- Covers the largest segment first and lets us validate the core scheduling loop before doubling the integration surface.
- Two calendar backends double the availability-conflict edge cases (the riskiest part of the eval) before we know the feature lands.
- The Graph API calendar model differs enough (recurrence, free/busy) that bolting it on later, once the loop is proven, is cheaper than carrying both now.

## Consequences
- ~19% of accounts can't use the feature at GA. Tracked as the top candidate for v2.
- The eval (`evals/calendar-integration-criteria.md`) scores Google-only flows; add Outlook criteria when v2 starts.
- Revisit when Google-only GA holds its target (0.85) for 3 weeks.
