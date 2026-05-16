# Contributing

Fork and customize for your workflow. You can also contribute improvements back.

## Exercise PR Template

```
## What I customized
**CLAUDE.md:** [Brief description]
**Skill added:** [Name and what it does]

## What I learned
[One thing from exploring the git history or customizing the repo]
```

## Skill Improvement PR Template

```
## What changed
[What you modified]

## Why
[What problem this fixes or improvement this adds]

## Testing (minimum 3 inputs)

### Test 1: [description]
- Before: [output before change]
- After: [output after change]
- Result: [improvement / no regression]

### Test 2: [description]
### Test 3: [description]
```

## Review Criteria

**Output quality:** Does the change produce better results?
**No regressions:** Still works on previously working inputs?
**Convention adherence:** Follows existing format?
**Commit message:** Explains what changed and why?

## Adding a New Skill

1. Create `skills/your-skill-name/SKILL.md`
2. Include: YAML front matter, instructions, output format, PASS/FAIL examples, edge cases, rules
3. Test on 3+ real inputs
4. Open a PR with example outputs

## Commit Messages

| Good | Bad |
|---|---|
| `prd-reviewer v6: require metric thresholds` | `update` |
| `evals: raise target 0.80 -> 0.85, add revision log table` | `fix` |
| `round 3 - add worked example + lead-with-audience rule (score: 79% -> 90%)` | `wip` |
