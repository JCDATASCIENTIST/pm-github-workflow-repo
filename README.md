# PM GitHub Workflow Repo

**Practice repo from the [Product Growth newsletter](https://www.news.aakashg.com/) (GitHub for PMs: Version Control for Everything You Build With AI).**

Fork it, customize it, use it.

## Before you start (first time only)

If you've never used Git or Claude Code, do this once:

1. **Install Git.** [git-scm.com/downloads](https://git-scm.com/downloads). On Windows, this gives you **Git Bash** — run all commands below in Git Bash, not PowerShell, so the Unix-style commands work.
2. **Install Claude Code.** [code.claude.com/docs](https://code.claude.com/docs/en/overview).
3. **Tell Git who you are** (otherwise your first commit aborts with "Author identity unknown"):
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "you@example.com"
   ```

New to Git entirely? [Hannah's GitHub 101](https://hannahstulberg.substack.com/p/tool-school-github-101) walks through setup with screenshots.

## Quick Start

> **Windows users:** run every command below in **Git Bash** (installed with Git), not PowerShell — the `cp`, `mkdir -p`, and `&&` syntax here is Unix-style.

**1. Fork.** Click "Fork" in the top right corner.

**2. Clone your fork.** HTTPS works out of the box — no SSH key needed:
```bash
git clone https://github.com/YOUR-USERNAME/pm-github-workflow-repo.git
cd pm-github-workflow-repo
```
(Prefer SSH? `git clone git@github.com:YOUR-USERNAME/pm-github-workflow-repo.git` — but only if you've already added an SSH key to GitHub.)

**3. Explore the history.** This is the whole point — the history is the lesson:
```bash
git log --oneline
```
You'll see a PRD reviewer skill evolving v1 → v7 (then hardened with later fixes), a CLAUDE.md growing then getting pruned, eval criteria tightening, and a full autoresearch run (41% → 90%, with one failed experiment reverted). Plain `git log` also includes the repo's own maintenance commits — to read each story cleanly, one file at a time, use the per-file commands in [The Four Workflows](#the-four-workflows) below.

**4. Activate a skill (required before Claude will use it).** Claude Code auto-loads skills from `.claude/skills/`, but they ship in `skills/` so they're easy to read and version. Copy one over:
```bash
mkdir -p .claude/skills && cp -r skills/prd-reviewer .claude/skills/
```
Without this copy, asking Claude to "review this PRD" just gets a generic answer — the skill never fires. **IMPORTANT: the `.claude/skills/` copy is a one-time snapshot — editing the source in `skills/` does nothing until you re-run the `cp` command above.** The copy is git-ignored, so you only ever version the one source in `skills/`. (Windows PowerShell, if you're not in Git Bash: `New-Item -ItemType Directory -Force .claude/skills; Copy-Item -Recurse skills/prd-reviewer .claude/skills/`.)

**5. Open in Claude Code.**
```bash
claude
```
Now try it: type `review the PRD in examples/sample-prd.md`. To leave Claude and return to your terminal, type `/exit` (or press Ctrl+C twice). If you see `command not found: claude`, re-open your terminal after installing, or see [code.claude.com/docs](https://code.claude.com/docs/en/overview).

## What's Inside

```
├── CLAUDE.md                              ← PM workspace config (customize)
├── skills/
│   ├── prd-reviewer/SKILL.md              ← PRD review, v1→v7 plus later fixes in git
│   ├── competitor-scan/SKILL.md           ← Competitor analysis
│   └── feedback-synthesizer/SKILL.md      ← User feedback synthesis
├── evals/
│   ├── support-chatbot-criteria.md        ← Worked eval, versioned in git
│   ├── calendar-integration-criteria.md   ← Second worked eval (used by the project-level CLAUDE.md)
│   └── how-to-write-eval-criteria.md      ← Write your own
├── autoresearch/                          ← Sample optimization run (read the git log)
│   ├── README.md                          ← Start here: how to read the run
│   ├── launch-announcement-writer.md      ← The prompt the loop optimized
│   ├── eval-criteria.md                   ← What it scored against
│   └── run-log.md                         ← 41% → 90%, one reverted experiment
├── examples/
│   ├── claude-md-filled-example.md        ← Filled-in CLAUDE.md
│   ├── project-level-claude-md.md         ← Project-specific CLAUDE.md
│   ├── good-vs-bad-commits.md             ← Commit message examples
│   └── sample-prd.md                      ← Incomplete PRD to test prd-reviewer on
├── decisions/
│   └── decision-2026-05-12-google-calendar-only-v1.md   ← Team OS decision-log example
├── docs/
│   └── which-repo-decision-guide.md       ← Printable decision guide
├── .gitignore                             ← PM-configured (secrets + PII)
├── .gitattributes                         ← LF line endings (cross-platform diffs)
├── LICENSE                                ← MIT
└── CONTRIBUTING.md                        ← PR templates
```

## The Four Workflows

**1. Skill Versioning:** `git log --oneline -- skills/prd-reviewer/SKILL.md`

**2. CLAUDE.md Pruning:** `git log -p -- CLAUDE.md` — watch a project-specific rule get added, then pruned back out in the very next commit that touches the file.

**3. Autoresearch Tracking:** `git log --oneline -- autoresearch/` — scores in the commit messages show what the loop discovered, including the experiment it reverted.

**4. Eval Versioning:** `git log --oneline -- evals/support-chatbot-criteria.md` — baseline → new criterion → raised target, each dated.

## Coming From PM OS?

```bash
cd ~/your-pm-os-folder
cp /path/to/pm-github-workflow-repo/.gitignore .   # run `pwd` inside your clone to find this path
git init && git branch -M main
git add . && git status --ignored          # check nothing you wanted is being ignored; git add -f <file> to override
git commit -m "initial commit: existing PM OS setup"
# create an empty repo on github.com first, then:
git remote add origin https://github.com/YOUR-USERNAME/your-pm-os.git
git push -u origin main
```

Copy the `.gitignore` in *before* `git add .` — otherwise a stray `.env` or data export can land in your first commit. The [Team OS](https://www.news.aakashg.com/p/claude-code-team-os) upgrade flow assumes your PM OS is already in a git repo, so this is the prerequisite step.

## The Exercise

1. Fork this repo (and clone it — see Quick Start).
2. Create a branch: `git checkout -b my-customization` (keeps `main` clean and makes the PR reviewable).
3. Replace `CLAUDE.md` with your context (see `examples/claude-md-filled-example.md`).
4. Add one skill to `skills/`.
5. Stage and commit (a commit is two steps — stage, then commit with a message; see `examples/good-vs-bad-commits.md` for what makes a good one):
   ```bash
   git add CLAUDE.md skills/
   git commit -m "customize CLAUDE.md and add my-skill"
   git log --oneline -1   # confirm it landed — your message should be at the top
   ```
6. Push the branch: `git push -u origin my-customization`.
7. Open a PR back to this repo, using the **Exercise PR Template** in [CONTRIBUTING.md](CONTRIBUTING.md).

It's a PM-artifact PR, not a code PR — that's the point.

## Related

- [PM OS](https://www.news.aakashg.com/p/pm-os) · [Team OS](https://www.news.aakashg.com/p/claude-code-team-os) · [Claude Skills](https://www.news.aakashg.com/p/10-laws-claude-skills)
- [Experimentation: Evals are the new PRD](https://www.news.aakashg.com/p/ankur-goyal-podcast) · [Autoresearch Guide](https://www.aibyaakash.com/p/autoresearch-guide) · [Ship Your First PR](https://www.news.aakashg.com/p/pm-guide-ship-production)
- [Hannah's GitHub 101](https://hannahstulberg.substack.com/p/tool-school-github-101)

MIT License. Fork it. Make it yours.
