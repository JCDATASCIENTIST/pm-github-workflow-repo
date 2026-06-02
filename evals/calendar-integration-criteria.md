# Eval Scoring Criteria: Calendar Integration

**Feature:** Natural-language scheduling ("book 30 min with Sarah next week")
**Owner:** Jake Torres (Calendar PM)
**Last reviewed:** 2026-04-13
**Baseline:** 0.72 (first run, 20 requests, 2026-04-13)
**Target:** 0.85 (before rollout to 10%)
**Kill threshold:** below 0.60, pause rollout

This is the eval referenced by `examples/project-level-claude-md.md`. It scores the AI scheduling assistant's output offline, the same way `support-chatbot-criteria.md` does — versioned in git so a score drop can be diagnosed (criteria changed vs. model regressed).

## Criteria (4 binary questions)

### 1. Picks a slot that is actually free for all attendees

PASS: proposes 2pm Tue when every attendee's calendar is open.
FAIL: proposes a slot that conflicts with an existing event.

Why: a double-booking erases all the trust the feature is meant to build.

### 2. Respects working hours and time zone

PASS: "11am your time / 2pm Sarah's time."
FAIL: proposes 6am for an attendee in another time zone.

Why: off-hours suggestions get ignored and the user falls back to manual scheduling.

### 3. Resolves the request in one turn when the intent is unambiguous

PASS: clear request in → single confirmed proposal out.
FAIL: asks a clarifying question when the request already specified person, duration, and window.

Why: every extra turn is a reason to abandon and open the calendar manually.

### 4. Asks before acting when the request is ambiguous

PASS: "Two Sarahs match — Sarah Kim or Sarah Lopez?"
FAIL: silently books with the wrong Sarah.

Why: a confident wrong booking is worse than a question.

## How to Run

1. Collect 20 real scheduling requests from beta logs.
2. Run each through the assistant.
3. Score each on criteria 1 and 2 (they apply to every request). Criteria 3 and 4 are conditional on the request type — score only the one that applies (3 for unambiguous requests, 4 for ambiguous ones) and mark the other N/A. N/A is excluded from that input's denominator; it is not a fail.
4. Overall score = total points earned / total criteria scored (0.00 to 1.00).

## Revision Log

Tracked in git — `git log --oneline -- evals/calendar-integration-criteria.md`. Review the first Monday of each month.
