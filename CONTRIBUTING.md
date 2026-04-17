# Contributing to pbnz-skills

Thanks for your interest in contributing. This is a personal skills collection, but outside contributions are welcome — especially bug reports, portability fixes, and small improvements to existing skills.

Please read this guide before opening an issue or pull request.

## Ground rules

- **Be kind.** All interactions are governed by the [Code of Conduct](CODE_OF_CONDUCT.md).
- **Small, focused changes.** One concern per PR. If a change touches multiple plugins or mixes refactors with features, split it.
- **Match existing style.** Follow the structure and tone of existing skills and documentation.
- **No surprise scope.** If your PR introduces a new dependency, a new plugin, or a change to the marketplace manifest beyond what's described in the issue, flag it in the PR description.

## Ways to contribute

### Report a bug

Open an issue using the **Bug report** template. Include:

- The skill or plugin affected.
- The Claude surface (Claude Code, Claude.ai, Claude Desktop, API, or another Agent-Skills-compatible tool) and its version if you know it.
- What you expected and what happened instead.
- A minimal reproduction if possible.

### Suggest a feature or new skill

Open an issue using the **Feature request** template. For a proposed new skill, include:

- What problem the skill solves and for whom.
- Why it belongs in this marketplace rather than a standalone repo.
- A rough sketch of the skill's invocation patterns and scope.

### Submit a pull request

1. Fork the repo and create a feature branch off `main`.
2. Make your change.
3. Ensure the validation workflow would pass locally (see **Validation** below).
4. Update [`CHANGELOG.md`](CHANGELOG.md) under the `Unreleased` section.
5. Open a PR against `main` using the pull request template.

## Adding a new skill to an existing plugin

Place the skill under the plugin's `skills/` directory:

```
plugins/<plugin>/skills/<skill-name>/SKILL.md
```

`SKILL.md` must have YAML frontmatter with at least:

```yaml
---
name: <skill-name>
description: <one-sentence description used for skill matching>
---
```

Match the name in the frontmatter to the skill directory name. Keep the description specific enough that it triggers cleanly on relevant requests.

## Adding a new plugin to this marketplace

1. Create a new directory under `plugins/<plugin-name>/`.
2. Add `plugins/<plugin-name>/.claude-plugin/plugin.json` with the plugin manifest.
3. Add at least one skill under `plugins/<plugin-name>/skills/<skill>/SKILL.md`.
4. Add a `plugins/<plugin-name>/README.md` documenting the plugin.
5. Register the plugin in the top-level `.claude-plugin/marketplace.json`.

The manifest must validate against the Claude Code plugin schema. CI will check this on every PR.

## Validation

The repository has a validation workflow that runs on every PR. It checks:

- `.claude-plugin/marketplace.json` is valid JSON and conforms to the marketplace schema.
- Each `plugins/*/.claude-plugin/plugin.json` is valid JSON and conforms to the plugin schema.
- Each `SKILL.md` has valid YAML frontmatter with the required fields.
- No email addresses or other private contact info are committed anywhere in the tree.
- No `SKILL.md` body contains invisible/bidi Unicode, imperative prompt-injection phrases, or URLs outside the allowlist at `.github/skill-url-allowlist.txt`.

You can run the same checks locally before pushing — see `.github/workflows/validate.yml` for the exact commands.

## Security review of contributed skills

Skill files are prompt content: whatever lands in a `SKILL.md` body is read by Claude as instructions when the skill activates. PRs that add or modify skills are reviewed for this explicitly, not just for style or correctness.

Before opening a PR that touches a `SKILL.md`:

- **Write in plain prose.** No zero-width, bidi, or steganographic Unicode anywhere in the body. If your editor inserts them invisibly, the CI safety scan will reject the PR.
- **No prompt-injection phrases.** Avoid paraphrases of "ignore previous instructions", "disregard the above", "you are now in developer mode", jailbreak references, and the like — even inside quoted examples or code fences. If you need to discuss these patterns in a skill, describe them at a distance rather than writing them literally.
- **No instructions to override safety, exfiltrate data, or reveal system prompts.** Skills are meant to extend Claude's helpfulness, not to reshape its safety posture.
- **Only link to allowlisted hosts.** New trusted hosts can be added to `.github/skill-url-allowlist.txt` in the same PR, with a short comment explaining why the host is needed.

Contributions that fail the safety scan are blocked by CI. Contributions that pass the scan but still raise reviewer concern (e.g. social-engineering framing, misleading descriptions) will be held for discussion before merge.

## Licence

By contributing, you agree your contributions will be licensed under the [Apache-2.0 licence](LICENSE).
