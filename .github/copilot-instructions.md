# Copilot instructions for pbnz-skills

## About this repository

This is a [Claude Code plugin marketplace](https://docs.claude.com) that also distributes Agent Skills under the open [agentskills.io](https://agentskills.io) standard. The repository is primarily configuration and prose — it is not application code. There is no build step and no runtime beyond the Python validation scripts under `scripts/`.

## What's in the tree

- `.claude-plugin/marketplace.json` — marketplace manifest.
- `plugins/<plugin>/.claude-plugin/plugin.json` — plugin manifest.
- `plugins/<plugin>/skills/<skill>/SKILL.md` — skill definition. The YAML frontmatter is metadata for skill matching; the Markdown body is natural-language prompt content consumed directly by the model.
- `plugins/<plugin>/README.md` — human-facing plugin documentation.
- `.github/workflows/validate.yml`, `.github/workflows/release.yml` — CI.
- `scripts/*.py` — Python 3.12 validation scripts used by `validate.yml`. Dependencies: `pyyaml`, `jsonschema`. `check_skill_safety.py` scans every `SKILL.md` body for invisible/bidi Unicode, imperative prompt-injection phrases, and URLs outside `.github/skill-url-allowlist.txt`.
- `.github/skill-url-allowlist.txt` — versioned allowlist of hostnames permitted in SKILL.md bodies. One host per line; `#` comments supported; subdomain matches are implicit.
- Top-level: `README.md`, `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, `SECURITY.md`, `CHANGELOG.md`, `LICENSE` (Apache-2.0).

## Where review effort adds value

Focus comments on:

- **JSON manifests** — required fields, SemVer-shaped `version` values, plugin `source` paths that do not exist on disk, duplicate plugin names, stale references.
- **GitHub Actions workflows** — security concerns (unsafe interpolations, overly broad permissions, untrusted action versions), correctness, and avoidable failure modes. `permissions: contents: write` on `release.yml` is intentional and required — do not flag it.
- **Python scripts** — bugs, edge cases, unsafe file handling. PEP 8 is expected. Python 3.12 is the target.

## Review style

- Prefer one clear comment per real issue over many small ones.
- Skip comments when you are uncertain whether something is actually wrong.
- Link to a concrete line of code, not a general "consider…".

## Out of scope for review

- **Do not rewrite, reword, or "improve" the Markdown body of any `SKILL.md` file.** Body text is prompt content the maintainer has hand-tuned; wording changes almost always regress intent. The YAML frontmatter is fair game for technical checks only (missing fields, invalid YAML, `name` mismatch with directory).
- **Do not suggest stylistic changes to Markdown prose** — word choice, sentence structure, heading level, bullet vs. paragraph, British vs. American spelling. The maintainer controls voice and tone.
- **Do not suggest adding email addresses or personal contact info anywhere in this repository.** This repo deliberately omits email addresses in favour of GitHub-native channels (private vulnerability reporting, issue templates, Discussions). Email addresses in any file are a hard CI failure via `scripts/check_no_private_contact.py` — they are an error, not a style preference.
- **Do not suggest changing the licence, the copyright line, or the reporting channels** in `CODE_OF_CONDUCT.md`, `SECURITY.md`, or issue templates.
- **Do not recommend swapping in third-party GitHub Actions** unless there is a concrete correctness or security problem. `release.yml` intentionally uses only the `gh` CLI and official `actions/*` actions.
- **Do not suggest changes that would introduce Node.js, a bundler, or compiled dependencies.** This repo is intentionally zero-build.

## Conventions worth knowing

- `.editorconfig` is authoritative. JSON / YAML / Markdown: 2-space indent. Python: 4-space indent.
- LF line endings everywhere, enforced by `.gitattributes`.
- [SemVer](https://semver.org/) for plugin and marketplace versions. [`CHANGELOG.md`](../CHANGELOG.md) follows [Keep a Changelog](https://keepachangelog.com/).
- A plugin directory's name must equal its manifest `name`. When a plugin has a single skill of the same name, the skill directory name matches too.
