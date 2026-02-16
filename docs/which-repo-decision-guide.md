# Which Repo? Decision Guide

*Print this. Pin it next to your monitor.*

---

## Three Repos, One PM

| | Your Workspace | Your Shared Tools | Your Projects |
|---|---|---|---|
| **Visibility** | Private | Public or Team | Per-initiative |
| **Changes** | Daily | When skills improve | Per feature lifecycle |
| **Who uses it** | Just you | Your team or public | Project collaborators |
| **Lifespan** | Permanent | Permanent | Archive when shipped |

---

## What Goes Where

| File Type | Which Repo | Why |
|---|---|---|
| Your CLAUDE.md (personal) | Workspace | Has your company info and preferences |
| A skill you built for yourself | Workspace | Has your workflow baked in |
| A skill others can use (stripped) | Shared Tools | Designed to be forked |
| Eval scoring criteria | Project | Versioned with the feature |
| PLANNING.md | Project | Lives next to the code |
| Autoresearch configs | Workspace | Personal optimization setup |
| Shared templates | Shared Tools | Fork, customize, improve |
| API keys, passwords | NEVER | .env + .gitignore |

---

## Edge Cases

**Shared eval criteria (across features):** Shared Tools repo, `evals/` folder.

**Skills referencing company context:** Workspace. Strip specifics for a Shared Tools version.

**Decision log entries (Team OS):** Shared Tools repo, `decisions/` folder.

**Prototype repos:** Still a Project repo. Archive when killed.

---

## When to Create New vs Add to Existing

**New repo:** Different people need access. Different lifecycle. Would push CLAUDE.md past 200 lines.

**Add to existing:** Same content type. Same collaborators. Shares context.

---

## Enterprise Notes

**Branch protection:** Settings > Branches > Require PR reviews.
**CODEOWNERS:** Require specific approvals for specific files.
**Access controls:** Private by default. Add collaborators individually.
**Audit trail:** Git log tracks every change, by whom, with reasoning.
**Check with IT** before making repos public or adding external collaborators.

---

## The Monday Check

```bash
cd ~/pm-workspace
git log --oneline -10
```

Monthly: `git diff HEAD~20 CLAUDE.md` to prune.

---

*From [GitHub for PMs](link-newsletter) · [PM OS](link-internal-pm-os) · [Team OS](link-internal-team-os)*
