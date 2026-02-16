# PM GitHub Workflow Repo

**Practice repo from [GitHub for PMs: Version Control for Everything You Build With AI](link-newsletter).**

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
10 commits showing a PRD reviewer skill evolving v1 to v7, a CLAUDE.md growing, and eval criteria being tightened.

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
│   ├── support-chatbot-criteria.md        ← Worked eval example
│   └── how-to-write-eval-criteria.md      ← Write your own
├── examples/
│   ├── claude-md-filled-example.md        ← Filled-in CLAUDE.md
│   ├── project-level-claude-md.md         ← Project-specific CLAUDE.md
│   └── good-vs-bad-commits.md             ← Commit message examples
├── docs/
│   └── which-repo-decision-guide.md       ← Printable decision guide
├── .gitignore                             ← PM-configured
└── CONTRIBUTING.md                        ← PR templates
```

## The Four Workflows

**1. Skill Versioning:** `git log --oneline -- skills/prd-reviewer/SKILL.md`

**2. CLAUDE.md Pruning:** `git log --oneline -- CLAUDE.md`

**3. Autoresearch Tracking:** Scores in commit messages show what the loop discovered.

**4. Eval Versioning:** `git log --oneline -- evals/`

## Coming From PM OS?

```bash
cd ~/your-pm-os-folder
git init && git add . && git commit -m "initial commit: existing PM OS setup"
```

Push to GitHub. Done. The [Team OS](link-internal-team-os) `/upgrade-to-team-os` command assumes your PM OS is already in a git repo.

## The Exercise

1. Fork this repo
2. Replace CLAUDE.md with your context (see `examples/claude-md-filled-example.md`)
3. Add one skill to `skills/`
4. Commit with a descriptive message (see `examples/good-vs-bad-commits.md`)
5. Push
6. Open a PR back to this repo

## Related

- [PM OS](link-internal-pm-os) · [Team OS](link-internal-team-os) · [CLAUDE.md Deep Dive](link-internal-claudemd-deep-dive)
- [Experimentation](link-internal-experimentation) · [Ship Your First PR](https://www.news.aakashg.com/p/pm-guide-ship-production)
- [Hannah's GitHub 101](https://hannahstulberg.substack.com/p/tool-school-github-101)

MIT License. Fork it. Make it yours.
