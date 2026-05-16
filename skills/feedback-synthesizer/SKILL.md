---
name: feedback-synthesizer
description: Synthesizes user feedback from multiple sources into ranked, actionable themes. Use when asked to "synthesize feedback", "analyze user feedback", run a "feedback synthesis", or "what are users saying".
---

# Feedback Synthesizer

Analyze provided user feedback and produce a structured synthesis. Works with interviews, surveys, support tickets, NPS responses, app reviews, or any combination.

## Process

1. Read all provided sources.
2. Extract observations: direct quotes, pain points, feature requests, workarounds, positive signals.
3. Group into themes by frequency and severity.
4. Rank by signal strength (sources x severity x consistency).

## Output Format

```
## Feedback Synthesis
**Date:** [today]
**Sources:** [list type and count]
**Observations extracted:** [count]

### Top Themes (ranked by signal strength)

#### Theme 1: [3-5 word name]
- **Signal:** [X] / [total] mentioned — severity: [low/medium/high/critical]
- **Summary:** [2-3 sentences]
- **Quotes:**
  - "[exact quote]" — [source identifier]
  - "[exact quote]" — [source identifier]
- **Implication:** [one sentence]

### What to Build
[Features supported by 2+ high-signal themes. Confidence level for each.]

### What NOT to Build
[Low-signal requests. Why each is a non-goal right now.]

### Open Questions
[What needs validation. Specific next steps.]

### Quote Bank
[Up to 15-20 strongest quotes by theme, copy-paste ready for PRDs. Fewer is fine for small inputs — never pad or invent to hit a count.]
```

## Edge Cases

**Fewer than 5 sources:** Flag low confidence. Recommend 5+ more before decisions.
**Contradictory feedback:** Report the split. "Power users (4/8) want more automation, new users (3/8) find existing automation confusing."
**Pre-PMF (before product-market fit):** Focus on problem validation, not feature requests. "7/8 described the problem. Signal is real."

## Rules
- Never invent quotes. Every quote must come verbatim from sources.
- Count honestly. 1/8 is "1/8," not "several."
- Save as `feedback-synthesis-[YYYY-MM-DD].md` in the project folder.
