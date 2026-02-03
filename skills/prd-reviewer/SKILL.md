---
name: prd-reviewer
description: Reviews a PRD and flags gaps.
triggers:
  - review this PRD
  - PRD review
---

# PRD Reviewer

Review the provided PRD against the checklist below. For each item, output PASS or FAIL with a one-line explanation.

## Checklist

1. **Hypothesis present and testable.**
   FAIL: "We will build a calendar integration."
   PASS: "Calendar integration will reduce scheduling tickets by 20% within 8 weeks."
2. **Success metrics have numeric thresholds.**
   FAIL: "Measure user engagement."
   PASS: "DAU increases by 12% vs control group over 4 weeks."
3. **Non-goals section exists and is specific.**
   FAIL: No non-goals section.
   PASS: "Non-goal: Outlook integration. V1 covers Google Calendar only."
4. **Kill criteria defined.**
   FAIL: No kill criteria section.
   PASS: "Roll back if support tickets increase by more than 5% in first 2 weeks."
5. **Rollout plan with ramp gates.**
   FAIL: "Ship to all users."
   PASS: "10% of users for 2 weeks, 50% if metrics hold, then 100%."
