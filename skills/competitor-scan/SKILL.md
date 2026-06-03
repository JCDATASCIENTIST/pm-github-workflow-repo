---
name: competitor-scan
description: Researches a competitor and produces a structured, evidence-backed analysis. Use when asked to "analyze a competitor", "run a competitor scan", do "competitive analysis", or "research [company name]".
---

# Competitor Scan

Research the specified competitor. Use web search for current information. Focus on verifiable facts.

## Process

1. Search for website, pricing page, G2 profile, Capterra profile, recent news.
2. If private or pre-revenue, note what is unavailable rather than guessing.
3. Check user review sites (G2, Capterra, Reddit) for real sentiment.
4. Compare to our product only if CLAUDE.md has company context loaded.

## Output Format

```
## Competitor Analysis: [Company Name]
**Date:** [today]
**Sources:** [list every URL referenced]

### Overview
[What they do. Founded, funding, headcount if available. Customer segment.]

### Product
- Core features: [list]
- Recent launches (last 6 months): [list with dates]
- Pricing: [exact tiers and prices, or "not public" if unavailable]

### Strengths (3-5, evidence-backed)
1. [Strength] — Evidence: [specific review, metric, or feature]

### Weaknesses (3-5, evidence-backed)
1. [Weakness] — Evidence: [specific complaint, missing feature]

### User Sentiment
- G2 rating: [X.X/5, N reviews]
- Common praise: [top 2-3 themes]
- Common complaints: [top 2-3 themes]

### Relevance to Us
- Overlap: [where we compete]
- Features they have that we don't: [list]
- Features we have that they don't: [list]
```

## Good vs Bad Output

GOOD: "Pricing: Pro tier $49/user/mo (pricing page, accessed 2026-05). G2: 4.4/5 across 212 reviews; top complaint: slow support."
BAD: "They're pretty expensive and people seem to like them." (no source, no number, no date)

## Edge Cases

**Private company (no public pricing):** Write "Pricing: not publicly available."
**Very new (few reviews):** Note the count. "G2: 4.2/5 but only 12 reviews."
**Multiple products:** Ask which product before proceeding.
**Cannot find info:** Say what you looked for and where. No speculation.

## Rules
- Cite every claim with a URL.
- Use actual pricing from the pricing page, not from blog posts.
- Save as `competitor-[name]-[YYYY-MM-DD].md` in the project folder.
- Saved with the dated name above, the file is git-ignored by default (the ignore rule keys off the YYYY-MM-DD date; drop the date and it is NOT protected). It can hold competitive detail you may not want public. To version a reviewed copy, use `git add -f <file>`.
