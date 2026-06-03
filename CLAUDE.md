<!-- TEMPLATE: replace every [BRACKETED] value with your own. Claude Code loads this
file every session. See examples/claude-md-filled-example.md for a completed version. -->
# CLAUDE.md

## Who I Am
- Role: [YOUR ROLE]
- Company: [YOUR COMPANY]
- Product: [YOUR PRODUCT]
- Team: [X] engineers, [X] designers

## How I Work
- I prototype before I spec.
- I write PLANNING.md in the project repo.
- I commit skill changes only after testing on 3+ inputs.

## Voice
- Direct. No filler. No "I'd be happy to help."
- PRDs: hypothesis first, then metrics with thresholds.
- Data analysis: show the method. Reproducibility matters.

## Current Focus
- [PROJECT 1]: [one line]
- [PROJECT 2]: [one line]

## Rules
- Never commit to GitHub without asking me first.
- Never modify files in evals/ without confirming the change and reason.
- Check skills/ folder when I reference a skill by name.
- Responses under 500 words unless I ask for depth.

## Tools
- Skills: see skills/ folder
- MCPs: [YOUR MCPS]
- CLIs: GitHub CLI, [OTHERS]

---
*Keep this file under 200 lines. Monthly, review what changed and prune: `git log -p -- CLAUDE.md` (or `git diff HEAD~20 -- CLAUDE.md` once you have 20+ commits - it errors on younger repos).*
*Project-specific context goes in project-level CLAUDE.md files, not here (the calendar PR rule that briefly lived here is the example - see the prune commit).*
*On-demand instructions go in skill files, not here.*
