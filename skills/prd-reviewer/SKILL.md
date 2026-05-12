---
name: prd-reviewer
description: Reviews a PRD against a completeness checklist and flags gaps before a human reviews it. Use when asked to "review this PRD" or for a "PRD review".
---

# PRD Reviewer

Review the provided PRD against the checklist below. This is a **document-completeness checklist** — it asks "is each section present and specific?" It is not an eval scoring function (those score AI *output* and stay at 3-6 criteria; see `evals/how-to-write-eval-criteria.md`). For each item, output PASS or FAIL with a one-line explanation, then an overall verdict.

## Checklist

Checks 1-5 apply to every PRD. Each check targets a different section, so a PRD can pass one and fail another.

1. **Hypothesis present and testable** (Hypothesis section).
   FAIL: "We will build a calendar integration." (a feature, not a hypothesis)
   PASS: "Calendar integration will reduce scheduling tickets by 20% within 8 weeks." (states expected effect + timeframe)
2. **Success metrics have numeric thresholds** (Success Metrics section).
   The number must appear in the Success Metrics section itself, not only restated from the hypothesis.
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

## AI Feature Criteria

Apply checks 6-7 **only if the feature is AI-powered** — i.e. a model generates, ranks, or classifies the output (chatbot, summarizer, recommender, search). If the feature is deterministic (a form, a setting, a CRUD screen), skip 6-7 and note "N/A — not an AI feature."

6. **Behavior contract with examples.**
   5+ input/output examples showing expected behavior, including 2+ edge cases.
   FAIL: "The AI should respond helpfully."
   PASS: Three user queries with expected responses, one ambiguous input with fallback, one adversarial input with refusal.

7. **Eval criteria defined.**
   Binary scoring criteria for measuring output quality offline.
   FAIL: "We'll evaluate quality manually."
   PASS: "4 criteria: resolves without escalation, references only knowledge base, resolves in under 3 messages, never echoes full card numbers. Target: 0.85." (see `evals/support-chatbot-criteria.md`)

## Output Format

```
## PRD Review: [PRD title]

| # | Check | Verdict | Note |
|---|-------|---------|------|
| 1 | Hypothesis testable | PASS/FAIL | [one line] |
| ... | ... | ... | ... |

**Score:** [N] of [5 or 7] checks pass.
**Verdict:** pick the first that matches, top-down:
- **NOT READY** — any of checks 1, 2, or 4 fail, OR 3+ checks fail total.
- **NEEDS WORK** — 1-2 checks fail and none of them are 1, 2, or 4.
- **SHIP-READY** — all checks pass.

**Top fix:** [the single most important gap to close first.]
```

## Edge Cases

**No metrics anywhere:** Fail check 2. Do not infer a threshold the author didn't write.
**Hypothesis and metric are the same sentence:** Pass 1, fail 2 — the threshold must live in the Success Metrics section so it survives edits to the framing.
**Unsure if AI-powered:** Ask one clarifying question before scoring 6-7. Do not guess.
**PRD is a one-pager / pre-PRD:** Note it, score only the sections that exist, and say which are missing rather than failing the whole doc.

## Rules

- Quote the PRD when you fail a check. No vague "could be clearer."
- A missing section is a FAIL, not a pass-with-caveat.
- Checks 1, 2, and 4 are the load-bearing ones — failing any of them means NOT READY regardless of the others.
- Don't rewrite the PRD. Flag gaps; the author fixes them.
