# AGENTS.md

## Learned User Preferences

- Pull business context from the user's GitHub repos, not from model memory of workspace rules; when unsure, fetch the relevant repo first.
- For DISURI Beauty, the source of truth is the Obsidian vault repo `JCDATASCIENTIST/obsidian-vault` (`3-Resources/DISURI-Beauty-Knowledge-Base/`), never remembered context.

## Learned Workspace Facts

- The user's daily working agent app is pm-brain at `~/Documents/projectmanagement/pm-brain`: a Cursor SDK app (CLI `run.ts` + web server `server.ts`) run via `npm run brain -- <context> "<prompt>"`.
- pm-brain layout: `contexts/<company>/` holds per-company brains (every `*.md` plus optional `mcp.json`); `skills/` is a 76-skill library (includes the deanpeters/Product-Manager-Skills pack, attributed in `PM-SKILLS-ATTRIBUTION.md`); `WORKFLOW.md` carries the Team OS operating rules and is loaded on every run.
- The `JCDATASCIENTIST/DISURIBeauty` GitHub repo is a Shopify store ops repo (not Vite+React); its `AGENTS.md` carries the ops facts, and the obsidian-vault knowledge base is linked as a submodule at `reference/kb`.
- CLAUDE.md is always loaded in this workspace; do not duplicate its rules here (e.g. the "KPI, never North Star metric" rule and the Product Growth Team OS workflow already live there).
