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

This repository was previously a personal [Agent Skills](https://agentskills.io) marketplace whose first plugin was Newton. With Newton's move to a dedicated repository, this marketplace is now empty.

It is kept alive because the marketplace name (`pbnz-skills`) is referenced in older `/plugin marketplace add` instructions floating around in install docs, blog posts, and chat history. Removing the repository would break those install paths silently. Leaving it in place — with an empty plugins array and a clear pointer at the top of this README — gives anyone arriving here a path forward.

If a future plugin is published under the PBNZ org, it will land in its own repository (one repo per plugin), not back here. This repository is not accepting new plugins.

## Repository state

- `.claude-plugin/marketplace.json` — marketplace manifest with an empty `plugins` array.
- `scripts/`, `.github/workflows/` — validation and release tooling, retained so any future maintenance commit can still be checked.
- `CHANGELOG.md`, `LICENSE` (Apache-2.0), `CODE_OF_CONDUCT.md`, `CONTRIBUTING.md`, `SECURITY.md` — governance files.

## Licence

[Apache-2.0](LICENSE). Copyright 2026 PBNZ.
