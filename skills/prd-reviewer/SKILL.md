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

1. **Hypothesis present.** The PRD states what you believe will happen.
2. **Success metrics listed.** The PRD names the metrics that matter.
3. **Scope defined.** The PRD says what is included.
4. **Risks identified.** The PRD lists what could go wrong.
5. **Timeline included.** The PRD has a delivery estimate.
