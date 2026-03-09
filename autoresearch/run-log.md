# Autoresearch Run Log

Loop: optimize `launch-announcement-writer.md` against `eval-criteria.md`.
Started 2026-04-21 02:14 · 25 sample inputs · commit-on-improve, revert-on-drop.

| Round | Change | Score | Verdict |
|---|---|---|---|
| seed | v0 prompt ("make it exciting") | 41% | baseline |
| 1 | require at least one concrete number | 68% | ✅ committed |
| 2 | ban buzzword list | 79% | ✅ committed |
| 3 | add a worked before/after example | 90% | ✅ committed |
| 4 | cap output at 80 words | 82% | ❌ reverted |
| 5 | revert round 4 | 90% | ✅ restored |

**Best: 90%** (after round 3 / round 5).

## What the loop learned

- The single biggest lever was forcing a **concrete number** (+27 points). Vague excitement scored worst.
- Banning buzzwords removed the easy way to fake enthusiasm without saying anything (+11).
- A **worked example** in the prompt pulled the model to the target format (+11).
- Round 4 over-constrained: an 80-word cap forced the model to drop the concrete numbers criterion 1 rewards. The loop caught the drop and reverted automatically. A failed experiment, preserved instead of lost.

## What stays a non-goal

The loop optimizes for the 4 eval criteria only. It does not judge brand voice or legal review — those stay human checks before publishing.
