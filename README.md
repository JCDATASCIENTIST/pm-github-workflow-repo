# PM GitHub Workflow Repo

**Practice repo from [GitHub for PMs: Version Control for Everything You Build With AI](https://www.news.aakashg.com/).**

Fork it, customize it, use it.

## Quick Start (5 minutes)

**1. Fork.** Click "Fork" in the top right corner.

**2. Clone your fork.**
```bash
git clone git@github.com:YOUR-USERNAME/pm-github-workflow-repo.git
cd pm-github-workflow-repo
```

**3. Explore the history.**
```bash
git log --oneline
```
The history is the lesson. A PRD reviewer skill evolving v1 → v7, a CLAUDE.md growing, eval criteria tightening across dated commits, and a full autoresearch run (41% → 90%, with one failed experiment reverted).

**4. Open in Claude Code.**
```bash
claude
```

## What's Inside

```
├── CLAUDE.md                              ← PM workspace config (customize)
├── skills/
│   ├── prd-reviewer/SKILL.md              ← PRD review, 7 versions in git
│   ├── competitor-scan/SKILL.md           ← Competitor analysis
│   └── feedback-synthesizer/SKILL.md      ← User feedback synthesis
├── evals/
│   ├── support-chatbot-criteria.md        ← Worked eval, versioned in git
│   └── how-to-write-eval-criteria.md      ← Write your own
├── autoresearch/                          ← Sample optimization run (read the git log)
│   ├── launch-announcement-writer.md      ← The prompt the loop optimized
│   ├── eval-criteria.md                   ← What it scored against
│   └── run-log.md                         ← 41% → 90%, one reverted experiment
├── examples/
│   ├── claude-md-filled-example.md        ← Filled-in CLAUDE.md
│   ├── project-level-claude-md.md         ← Project-specific CLAUDE.md
│   └── good-vs-bad-commits.md             ← Commit message examples
├── docs/
│   └── which-repo-decision-guide.md       ← Printable decision guide
├── .gitignore                             ← PM-configured
├── LICENSE                                ← MIT
└── CONTRIBUTING.md                        ← PR templates
```

## The Four Workflows

**1. Skill Versioning:** `git log --oneline -- skills/prd-reviewer/SKILL.md`

**2. CLAUDE.md Pruning:** `git log --oneline -- CLAUDE.md`

**3. Autoresearch Tracking:** `git log --oneline -- autoresearch/` — scores in the commit messages show what the loop discovered, including the experiment it reverted.

**4. Eval Versioning:** `git log --oneline -- evals/support-chatbot-criteria.md` — baseline → new criterion → raised target, each dated.

## Coming From PM OS?

```bash
cd ~/your-pm-os-folder
git init && git add . && git commit -m "initial commit: existing PM OS setup"
```

Push to GitHub. Done. The [Team OS](https://www.news.aakashg.com/p/claude-code-team-os) `/upgrade-to-team-os` command assumes your PM OS is already in a git repo.

## The Exercise

1. Fork this repo
2. Replace CLAUDE.md with your context (see `examples/claude-md-filled-example.md`)
3. Add one skill to `skills/`
4. Commit with a descriptive message (see `examples/good-vs-bad-commits.md`)
5. Push
6. Open a PR back to this repo

## Related

- [PM OS](https://www.news.aakashg.com/p/pm-os) · [Team OS](https://www.news.aakashg.com/p/claude-code-team-os) · [Claude Skills](https://www.news.aakashg.com/p/10-laws-claude-skills)
- [Experimentation: Evals are the new PRD](https://www.news.aakashg.com/p/ankur-goyal-podcast) · [Autoresearch Guide](https://www.aibyaakash.com/p/autoresearch-guide) · [Ship Your First PR](https://www.news.aakashg.com/p/pm-guide-ship-production)
- [Hannah's GitHub 101](https://hannahstulberg.substack.com/p/tool-school-github-101)

MIT License. Fork it. Make it yours.
