# Good vs Bad Commit Messages

## Bad (tells you nothing in 3 months)

```
update
fix
changes
wip
stuff
final version
```

## Good (tells you what changed and why)

```
prd-reviewer v6: require metric thresholds, not just metric names
CLAUDE.md: add voice/style section and prototyping workflow preference
evals: tighten resolution threshold from 5 to 3 messages (abandonment data)
competitor-scan: add G2/Capterra check
```

## For Autoresearch Runs (include the score)

```
round 1 - require concrete numbers (score: 41% → 68%)
round 2 - ban buzzword list (score: 68% → 79%)
round 3 - add worked CTA example (score: 79% → 90%)
round 4 - tighten word count [REVERTED, score dropped to 82%]
```

## The Pattern

**What** changed + **why** (or the result).

Run `git log --oneline` on your repo right now. If you can't tell what happened from the messages alone, start writing better ones today.
