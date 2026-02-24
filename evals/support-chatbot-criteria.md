# Eval Scoring Criteria: Support Chatbot

**Feature:** AI support chatbot for billing questions
**Owner:** Priya N. (Support PM)
**Last reviewed:** 2026-03-03
**Baseline:** 0.71 (first run, 20 questions, 2026-03-03)
**Target:** 0.80
**Kill threshold:** below 0.60, escalate to engineering

## Criteria (3 binary questions)

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

## How to Run

1. Collect 20 real questions from last week's support logs.
2. Run each through the chatbot.
3. Score each on all 3 criteria (1 = pass, 0 = fail).
4. Overall score = average (0.00 to 1.00).

## When to Update

- New failure mode appears that no criterion catches
- User expectations shift
- Monthly review: first Monday of the month
- Always commit changes with a message explaining what and why

## Revision Log

Track in git. When scores drop, `git log` on this file answers: did the criteria change, or did the model degrade?
