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
2. **Success metrics listed.** The PRD names the metrics that matter.
3. **Scope defined.** The PRD says what is included.
4. **Risks identified.** The PRD lists what could go wrong.
5. **Rollout plan with ramp gates.**
   FAIL: "Ship to all users."
   PASS: "10% of users for 2 weeks, 50% if metrics hold, then 100%."
