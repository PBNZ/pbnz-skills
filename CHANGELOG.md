# Changelog

All notable changes to this marketplace and its plugins are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

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

[Unreleased]: https://github.com/PBNZ/pbnz-skills/compare/v0.1.0...HEAD
[0.1.0]: https://github.com/PBNZ/pbnz-skills/releases/tag/v0.1.0
