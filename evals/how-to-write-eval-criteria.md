# How to Write Eval Scoring Criteria

## The Formula

Every criterion is a binary question with a concrete PASS and FAIL example.

## Step 1: List What Goes Wrong

Before writing criteria, answer: "When my AI feature produces bad output, what specifically is bad?"

Write criteria from failures you have seen, not from imagination.

## Step 2: Turn Failures Into Binary Questions

| Failure Pattern | Binary Criterion |
|---|---|
| Chatbot makes up info | Does the response reference only the knowledge base? |
| Summary too long | Is the summary under 150 words? |
| Search misses attributes | Does the result match ALL specified attributes? |

## Step 3: Write PASS/FAIL Examples

**Good:** Specific.
- PASS: "Per our refund policy, items can be returned within 30 days."
- FAIL: "Most companies allow 90-day returns, so you should be fine."

**Bad:** Vague.
- PASS: "A helpful response."
- FAIL: "An unhelpful response."

## Step 4: Aim for 3-6 Criteria

Fewer than 3: too coarse. More than 6: the model games the checklist.

## Step 5: Test on 20+ Inputs

20 is a floor - use more for higher-variance tasks (the launch-announcement run in `autoresearch/` uses 25). If everything passes, criteria are too easy. If everything fails, too strict.

## Template

```markdown
# Eval Scoring Criteria: [Feature Name]

**Feature:** [one line]
**Owner:** [PM]
**Last reviewed:** [YYYY-MM-DD]
**Baseline:** [X.XX]
**Target:** [X.XX]
**Kill threshold:** [below X.XX, do what?]

## Criteria

### 1. [Binary question]
PASS: [specific example]
FAIL: [specific example]
Why: [one line]

## How to Run
1. Collect [N] real inputs from [source].
2. Run each through [feature].
3. Score (1 = pass, 0 = fail).
4. Overall = average (0.00 to 1.00).

## Revision Log
Tracked in git. Review the first Monday of each month.
```

For the full eval methodology, see [Experimentation: Evals are the new PRD](https://www.news.aakashg.com/p/ankur-goyal-podcast).
