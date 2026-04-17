# pbnz-skills

A personal collection of [Agent Skills](https://agentskills.io) for Claude Code, Claude Cowork, Claude.ai, the Claude API, and other Agent-Skills-compatible tools.

This repository is also a **plugin marketplace** for the Claude surfaces that support plugins (Claude Code and Cowork), so you can install everything here with a single command.

## Contents

| Plugin | Description | Skills |
|---|---|---|
| [`newton`](plugins/newton) | Reasoning and sparring partner mode — honest pushback, current-sources research, reuse-before-rebuild checks, and surgical edits. Opt-in by explicit invocation. | `newton` |

More will land here over time. Each plugin is self-contained under `plugins/<name>/` and ships at least one skill under `plugins/<name>/skills/<skill>/SKILL.md`.

## Install

### Claude Code

Add this repository as a marketplace, then install the plugin you want:

```
/plugin marketplace add PBNZ/pbnz-skills
/plugin install newton@pbnz-skills
```

Once installed, Claude Code will auto-discover the plugin's skills and load them on demand.

### Claude Cowork

Cowork runs inside the Claude desktop app and supports plugin marketplaces the same way Claude Code does. Add this repository as a marketplace through Cowork's plugin management and install `newton` from it. Cowork will then expose the skill automatically.

### Claude.ai and Claude Desktop (without Cowork)

For plain Claude.ai or the Claude desktop app outside of Cowork, upload the skill file directly through the **Skills** section of your Claude settings.

**Download the latest Newton skill file:** [`newton.SKILL.md`](https://github.com/PBNZ/pbnz-skills/releases/latest/download/newton.SKILL.md) (served as a release asset — your browser will save the file instead of displaying it).

If you prefer to grab it straight from the repository tree, the source file lives at `plugins/newton/skills/newton/SKILL.md`.

### Claude API

Register the skill through the [Skills API](https://docs.claude.com) using the same `SKILL.md` file.

### Other Agent-Skills-compatible tools

This repository's skills follow the open [Agent Skills standard](https://agentskills.io), so they work with any tool that supports the standard — including GitHub Copilot, Cursor, OpenAI Codex, Gemini CLI, Windsurf, and others. Point your tool's skill-ingestion mechanism at the relevant `SKILL.md` file.

## Repository layout

```
.
├── .claude-plugin/
│   └── marketplace.json         # Claude Code marketplace manifest
├── plugins/
│   └── <plugin>/
│       ├── .claude-plugin/
│       │   └── plugin.json      # Plugin manifest
│       ├── skills/
│       │   └── <skill>/
│       │       └── SKILL.md     # Skill definition (Agent Skills standard)
│       └── README.md            # Plugin-level docs
├── .github/
│   ├── ISSUE_TEMPLATE/
│   ├── PULL_REQUEST_TEMPLATE.md
│   └── workflows/validate.yml
├── CHANGELOG.md
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── LICENSE                      # Apache-2.0
├── README.md
└── SECURITY.md
```

## Versioning

This marketplace and each plugin follow [Semantic Versioning](https://semver.org/). Notable changes are recorded in [`CHANGELOG.md`](CHANGELOG.md).

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). All interactions in this project are governed by the [Code of Conduct](CODE_OF_CONDUCT.md).

## Security

See [SECURITY.md](SECURITY.md) for how to report a vulnerability.

## Licence

[Apache-2.0](LICENSE). Copyright 2026 PBNZ.
