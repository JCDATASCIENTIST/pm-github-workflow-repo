# Autoresearch Run (Sample)

This folder is a **worked example of the autoresearch experiment-tracking workflow** (Workflow 3 in the newsletter). It is not a skill you invoke — it's a record of an optimization loop, frozen so you can read the git history.

## What happened

An overnight optimization loop (the "Karpathy loop" — an automated test-mutate-keep-if-better cycle; see the [Autoresearch Guide](https://www.aibyaakash.com/p/autoresearch-guide)) ran against `launch-announcement-writer.md` — a prompt that drafts product launch announcements. Each round:

1. Mutated the prompt.
2. Scored the output against the eval in `eval-criteria.md` (4 binary checks, 25 sample inputs).
3. **Committed** if the score improved, **reverted** if it dropped.

When you wake up, the git log *is* the experiment log.

## Read the run

```bash
git log --oneline -- autoresearch/
```

You'll see the rounds, newest first (commit hashes on the left will differ in your fork — read the messages):

```
round 5 - revert word-count cap (82% -> 90%, restored best)
round 4 - cap at 80 words [EXPERIMENT] (score: 90% -> 82%)
round 3 - add worked example + lead-with-audience rule (score: 79% -> 90%)
round 2 - ban buzzword list (score: 68% -> 79%)
round 1 - require concrete numbers (score: 41% -> 68%)
autoresearch: seed launch-announcement-writer v0 (score: 41%)
```

Read it bottom-up: 41% → 68% → 79% → 90%, then round 4 tries an 80-word cap, drops to 82%, and round 5 reverts it back to the 90% prompt. The failed experiment stays in the log instead of vanishing.

See every change the loop made to the prompt, diff by diff (no hash to copy — this walks the whole file's history):

```bash
git log -p -- autoresearch/launch-announcement-writer.md
```

## The point

Without version control you'd have the final prompt and no idea how it got there. With it, every winning change is documented and every failed experiment (round 4) is caught and explained — not silently lost. `run-log.md` mirrors the commit history in one place.

## The one rule

Write the score into the commit message format inside your loop config.
`round 3 - add worked example (score: 79% -> 90%)` teaches you something.
`update` teaches you nothing.
