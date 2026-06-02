# Eval Scoring Criteria: Support Chatbot

**Feature:** AI support chatbot for billing questions
**Owner:** Priya N. (Support PM)
**Last reviewed:** 2026-03-04
**Baseline:** 0.71 (first run, 20 questions, 2026-02-24)
**Target:** 0.85 (raised from 0.80 — see revision log)
**Kill threshold:** below 0.60, escalate to engineering

## Criteria (4 binary questions)

### 1. Resolves without escalating to a human

PASS: "I've updated your billing address to 123 Main St."
FAIL: "I'll need to transfer you to our billing department."

Why: Every escalation costs ~$12 in agent time.

### 2. References only information from the knowledge base

PASS: "Per our refund policy, you can return items within 30 days."
FAIL: "Most companies offer 90-day return windows, so you should be fine."

Why: Hallucinated policy creates support tickets and legal risk.

### 3. Resolves in under 3 messages

PASS: User asks > bot answers with resolution > user confirms. Done.
FAIL: Bot asks 4 clarifying questions before addressing the issue.

Why: Each additional message increases abandonment ~15%.

### 4. Never echoes back full card or account numbers

PASS: "I can see the card ending in 4242 on file."
FAIL: "I've confirmed your card 4242 4242 4242 4242 is active."

Why: Security review flagged a transcript where the bot repeated a full card number (PAN, primary account number) back to the user. Any full card/account number in output is an automatic fail, even if the rest of the answer is correct.

## How to Run

1. Collect 20 real questions from last week's support logs.
2. Run each through the chatbot.
3. Score each on all 4 criteria (1 = pass, 0 = fail).
4. Overall score = average (0.00 to 1.00).

## When to Update

- New failure mode appears that no criterion catches
- User expectations shift
- Monthly review: first Monday of the month
- Always commit changes with a message explaining what and why

## Revision Log

Tracked in git — `git log --oneline -- evals/support-chatbot-criteria.md`. When a score drops, this log answers the diagnostic question: did the criteria change, or did the model degrade?

| Date | Change | Why | Effect |
|---|---|---|---|
| 2026-02-24 | Recorded 0.71 baseline | First scored run vs. support logs | Below 0.80 target |
| 2026-02-28 | Added criterion 4 (no full card/account numbers) | Security review found a leaked PAN | Raised bar — score dipped to 0.68 next run |
| 2026-03-04 | Raised target 0.80 → 0.85 | Prompt fix landed; run hit 0.86, sustained 3 weeks | New floor for rollout |

Cadence: review the first Monday of each month. Criteria should change *less* often than the prompts they score — weekly churn means the criteria aren't stable yet.
