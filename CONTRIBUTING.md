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

## Before You Enable Review Gating

If you fork this for a team: edit `.github/CODEOWNERS` and replace `@YOUR-USERNAME` with real GitHub handles, then turn on branch protection (Settings → Branches → Require review from Code Owners). Until you do, CODEOWNERS is inert. The `.github/workflows/gitleaks.yml` secret scan runs automatically - but org-owned repos need a free `GITLEAKS_LICENSE` secret (see the comment in that file).

## Review Criteria

**Output quality:** Does the change produce better results?
**No regressions:** Still works on previously working inputs?
**Convention adherence:** Follows existing format?
**Commit message:** Explains what changed and why?

## Adding a New Skill

1. Create `skills/your-skill-name/SKILL.md`
2. Include: YAML front matter, instructions, output format, examples (PASS/FAIL for a checker skill like prd-reviewer; a good-vs-bad output sample for a generative skill like competitor-scan), edge cases, rules
3. Test on 3+ real inputs
4. Open a PR with example outputs

## Commit Messages

| Good | Bad |
|---|---|
| `prd-reviewer v6: require metric thresholds` | `update` |
| `evals: raise target 0.80 -> 0.85, add revision log table` | `fix` |
| `round 3 - add worked example + lead-with-audience rule (score: 79% -> 90%)` | `wip` |
