# pbnz-skills

> **Looking for Newton?** Newton has moved to its own home: **<https://newton.mystuffonline.org/>** (canonical repo: [`PBNZ/newton-skill`](https://github.com/PBNZ/newton-skill)).
>
> Update your install:
>
> ```
> /plugin marketplace remove pbnz-skills
> /plugin marketplace add PBNZ/newton-skill
> /plugin install newton@newton-skill
> ```
>
> The version of Newton previously distributed from this repository (up to `0.2.0`) is **deprecated in place**. New attribution work, fixes, and releases land in `PBNZ/newton-skill` only.

---

This repository is a personal [Agent Skills](https://agentskills.io) marketplace. Every plugin
lives in its own canonical repository (one repo per plugin — the lesson from Newton's move) and is
listed here as a **reference entry**: a marketplace source pointing at the canonical repo, never a
copy. One `/plugin marketplace add PBNZ/pbnz-skills` surfaces all of them, while each plugin keeps
exactly one maintained home.

The marketplace name (`pbnz-skills`) is also referenced in older `/plugin marketplace add`
instructions in install docs, blog posts, and chat history — keeping this repository alive keeps
those install paths working.

## Plugins

| Plugin | What it does | Canonical home |
|--------|--------------|----------------|
| `repokit` | Scaffold standard-compliant repos (`/new-repo`) and apply the RepoKit repo standard while you work | [`PBNZ/repo-kit`](https://github.com/PBNZ/repo-kit) |

Install:

```
/plugin marketplace add PBNZ/pbnz-skills
/plugin install repokit@pbnz-skills
```

Newton is the exception: it predates reference entries and is installed from its own marketplace —
see the banner above.

## Repository state

- `.claude-plugin/marketplace.json` — the marketplace manifest; plugins are reference entries pointing at their canonical repositories.
- `scripts/`, `.github/workflows/` — validation and release tooling.
- `CHANGELOG.md`, `LICENSE` (Apache-2.0), `CODE_OF_CONDUCT.md`, `CONTRIBUTING.md`, `SECURITY.md` — governance files.

## Licence

[Apache-2.0](LICENSE). Copyright 2026 PBNZ.
