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

Every line below is a real commit from this repo — run `git log --oneline` to find each one:

```
prd-reviewer v6: require metric thresholds, not just metric names
CLAUDE.md: add voice/style section and prototyping workflow preference
evals: raise target 0.80 -> 0.85, add revision log table
CLAUDE.md: prune calendar PR rule (belongs in project CLAUDE.md)
```

## For Autoresearch Runs (include the score)

These are the *actual* commits from this repo's `autoresearch/` run — run `git log --oneline -- autoresearch/` to confirm they match (use ASCII `->`, since git messages aren't Unicode):

```
round 1 - require concrete numbers (score: 41% -> 68%)
round 2 - ban buzzword list (score: 68% -> 79%)
round 3 - add worked before/after example (score: 79% -> 90%)
round 4 - cap at 80 words [EXPERIMENT] (score: 90% -> 82%)
round 5 - revert word-count cap (82% -> 90%, restored best)
```

## The Pattern

**What** changed + **why** (or the result).

Run `git log --oneline` on your repo right now. If you can't tell what happened from the messages alone, start writing better ones today.
