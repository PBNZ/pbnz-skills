# Changelog

All notable changes to this marketplace and its plugins are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

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

[Unreleased]: https://github.com/PBNZ/pbnz-skills/compare/v0.2.0...HEAD
[0.2.0]: https://github.com/PBNZ/pbnz-skills/releases/tag/v0.2.0
[0.1.0]: https://github.com/PBNZ/pbnz-skills/releases/tag/v0.1.0
