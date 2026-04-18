# Changelog

All notable changes to this marketplace and its plugins are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.3.0] — 2026-04-19

Newton has moved to its own dedicated repository, [`PBNZ/newton-skill`](https://github.com/PBNZ/newton-skill), with the custom install domain <https://newton.mystuffonline.org/>. This release removes Newton from `pbnz-skills` entirely and converts the repository into a pointer at its new home.

This is a breaking change for anyone currently installing Newton via `/plugin install newton@pbnz-skills`. The top of `README.md` documents the migration path.

### Removed

- `plugins/newton/` tree — `plugin.json`, `SKILL.md`, and the plugin-level `README.md`. Newton's canonical home is now [`PBNZ/newton-skill`](https://github.com/PBNZ/newton-skill); this repository's copy was a duplicate and was being maintained in the wrong place (the attribution work that should have shipped with `newton-skill` v0.2.0 landed here as this repository's `0.2.0` release — see that entry for the incident the move corrects).
- `NOTICE.md` — the Apache-2.0 attribution file existed solely to preserve upstream MIT attribution for material adapted into Newton's `SKILL.md`. With Newton gone, no third-party material remains in this repository that requires a `NOTICE`. The attribution chain (Andrej Karpathy → `multica-ai/andrej-karpathy-skills` by Jiayuan → PBNZ) has been ported verbatim to the canonical Newton repository's [`NOTICE.md`](https://github.com/PBNZ/newton-skill/blob/main/NOTICE.md) and travels with the skill from there.
- `.github/skill-url-allowlist.txt`: `x.com` host entry and its explanatory comment block. The allowlist only exists to gate URLs in `SKILL.md` bodies, and `x.com` was listed only to permit Newton's Credits footer. With no `SKILL.md` files in this repository, the entry has no remaining referent.

### Changed

- `README.md` — rewritten as a pointer to `https://newton.mystuffonline.org/` with the migration command block at the top. The previous Contents table, multi-surface install instructions, and repository-layout section have been removed; they applied to a marketplace that carried a plugin, which this one no longer does.
- `.claude-plugin/marketplace.json` — `plugins` array emptied; marketplace `metadata.version` bumped `0.2.0` → `0.3.0`.
- `scripts/validate_marketplace.py` — the `plugins must be a non-empty array` check relaxed to `plugins must be an array`. An empty marketplace is a coherent state (deprecation, between releases, deliberate pointer repository); the original non-empty check was too strict and would have made this release impossible to validate.
- `.github/PULL_REQUEST_TEMPLATE.md`, `.github/ISSUE_TEMPLATE/bug_report.md` — removed the Newton-specific examples from the "affected plugin" placeholder. Generic examples now.
- `.github/workflows/release.yml` — made asset collection robust to the no-`plugins/` and no-`SKILL.md` cases. The previous version assumed `plugins/` existed and that `release-assets/*.SKILL.md` would always glob to at least one file; with Newton gone, both assumptions broke and the v0.3.0 release run failed on the first attempt. The workflow now creates the GitHub release with whatever assets are present (zero or more), so a pointer-repo release tag is a valid release.

### Notes

- The v0.2.0 GitHub release on this repository carries a deprecation banner pointing at `PBNZ/newton-skill` v0.2.1, which is where the same attribution work landed properly.
- No `v0.3.0` plugin or skill is being published from this repository; the `0.3.0` tag exists to mark the removal event in the marketplace manifest history.

## [0.2.0] — 2026-04-19

### Added

- `NOTICE.md` at repo root — attribution and MIT licence preservation for material adapted from [`multica-ai/andrej-karpathy-skills`](https://github.com/multica-ai/andrej-karpathy-skills) by Jiayuan (`forrestchang`), which distils [Andrej Karpathy's public observations](https://x.com/karpathy/status/2015883857489522876) on LLM coding pitfalls. Includes a section-by-section breakdown of what Newton derives from upstream and a three-layer attribution structure (originator of ideas → upstream author → integrator).
- Newton skill: new **"Attribution when building on others' work"** principle in the Core principles section, covering licence obligations, community norms even without a licence, specificity about what was borrowed, placement that survives redistribution, and distinguishing the three layers of credit. Framed as the second half of *Reuse before reinvention*.
- Newton skill: self-evaluation gate item 10 — mandatory attribution check for any work that incorporates or builds on third-party material before delivery.
- Newton skill: Credits footer at the end of `SKILL.md` — names `andrej-karpathy-skills` as the source of the *Simplicity in what's produced* and *Editing existing work — surgical changes only* sections, with an absolute GitHub URL to `NOTICE.md` so attribution travels with the skill when distributed as a release asset.
- Plugin README (`plugins/newton/README.md`): "Related work and influences" section pointing at `NOTICE.md` via a relative link for repo-tree readers.

### Changed

- Newton skill grew a behavioural principle and a pre-delivery gate check — Newton now attributes derived work as part of normal operation, not just documents that it should. Frontmatter, name, description, and trigger rules are unchanged; invocation behaviour is identical.
- `plugin.json` and `marketplace.json` versions bumped to `0.2.0`.

## [0.1.0] — 2026-04-17

### Added

- Initial marketplace scaffolding (`.claude-plugin/marketplace.json`).
- First plugin: `newton` — reasoning and sparring partner mode.
  - Plugin manifest at `plugins/newton/.claude-plugin/plugin.json`.
  - Skill at `plugins/newton/skills/newton/SKILL.md`.
  - Plugin-level README at `plugins/newton/README.md`.
- Apache-2.0 licence.
- Repository documentation: `README.md`, `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, `SECURITY.md`.
- GitHub issue templates and pull request template.
- CI validation workflow (`.github/workflows/validate.yml`) — validates the marketplace manifest, plugin manifests, skill frontmatter, absence of private contact info, and skill-body safety (invisible/bidi Unicode, imperative prompt-injection phrases, URL hosts outside the allowlist).
- Skill-body safety scanner (`scripts/check_skill_safety.py`) and versioned URL host allowlist (`.github/skill-url-allowlist.txt`) — a mechanical second line of defence against malicious content in contributed skills, complementing human review.
- Release workflow (`.github/workflows/release.yml`) — on every `v*.*.*` tag push, creates the GitHub release and attaches every `SKILL.md` as a downloadable asset (e.g. `newton.SKILL.md`), so users on Claude.ai or Claude Desktop can install the skill with a single click.
- GitHub Copilot custom instructions: a repo-wide file at `.github/copilot-instructions.md` and a path-scoped file at `.github/instructions/skill-files.instructions.md` that together scope Copilot code review away from prose and SKILL.md bodies and towards the JSON manifests, Actions workflows, and Python scripts where review actually adds value.

[Unreleased]: https://github.com/PBNZ/pbnz-skills/compare/v0.3.0...HEAD
[0.3.0]: https://github.com/PBNZ/pbnz-skills/releases/tag/v0.3.0
[0.2.0]: https://github.com/PBNZ/pbnz-skills/releases/tag/v0.2.0
[0.1.0]: https://github.com/PBNZ/pbnz-skills/releases/tag/v0.1.0
