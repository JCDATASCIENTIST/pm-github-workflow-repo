# Autoresearch Run Log

Loop: optimize `launch-announcement-writer.md` against `eval-criteria.md`.
Started 2026-04-21 02:14 · 25 sample inputs · commit-on-improve, revert-on-drop.

| Round | Change | Score | Verdict |
|---|---|---|---|
| seed | v0 prompt ("make it exciting") | 41% | baseline |
| 1 | require at least one concrete number | 68% | ✅ committed |
| 2 | ban buzzword list | 79% | ✅ committed |
| 3 | add worked example + lead-with-audience rule | 90% | ✅ committed |
| 4 | cap output at 80 words | 82% | ❌ reverted |
| 5 | revert round 4 | 90% | ✅ restored |

**Best: 90%** (after round 3 / round 5).

## What the loop learned

- The single biggest lever was forcing a **concrete number** (+27 points). Vague excitement scored worst.
- Banning buzzwords removed the easy way to fake enthusiasm without saying anything (+11).
- Round 3 made two changes together (a **worked example** plus a "lead with who it's for" rule targeting criterion 3) and jumped +11. Bundling them means the log can't split the credit between the two — a reminder to change one thing per round when you want clean attribution.
- Round 4 over-constrained. On the longer feature specs, an 80-word budget wasn't enough to fit the before/after framing *and* the concrete numbers, so the model dropped the numbers to stay under the cap — and criterion 1 (at least one concrete number) started failing. Net score fell to 82%. The loop caught the drop and reverted automatically. A failed experiment, preserved in the log instead of lost.

## What stays a non-goal

The loop optimizes for the 4 eval criteria only. It does not judge brand voice or legal review — those stay human checks before publishing.
