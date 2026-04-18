> [!IMPORTANT]
> **Newton has moved to its own repository: [PBNZ/newton-skill](https://github.com/PBNZ/newton-skill).**
>
> The copy of newton in this marketplace is **frozen at v0.1.0** and will not receive further updates. Please install from the new home — see the [newton-skill README](https://github.com/PBNZ/newton-skill#readme) for current install instructions across Claude Code, Cowork, Claude.ai, and the Claude API.

# pbnz-skills

A personal collection of [Agent Skills](https://agentskills.io) for Claude Code, Claude Cowork, Claude.ai, the Claude API, and other Agent-Skills-compatible tools.

This repository was originally a **plugin marketplace** hosting `newton`. As of 2026-04-19, newton has moved to its own dedicated repository ([PBNZ/newton-skill](https://github.com/PBNZ/newton-skill)) so it can ship independently with its own release cadence, landing page, and analytics. This marketplace is being kept alive as a placeholder for any future plugins, but currently hosts only the frozen v0.1.0 copy of newton.

## Contents

| Plugin | Status | Description |
|---|---|---|
| [`newton`](plugins/newton) | **Deprecated — moved to [PBNZ/newton-skill](https://github.com/PBNZ/newton-skill)** | Frozen at v0.1.0. Install from the new repo for ongoing updates. |

## Install

### Newton (current)

Install Newton from its new home: **[PBNZ/newton-skill](https://github.com/PBNZ/newton-skill)**.

### Newton (frozen v0.1.0 from this marketplace)

If you specifically need the v0.1.0 snapshot from this marketplace — for example to pin to a known historical version — the original install paths still work:

```
/plugin marketplace add PBNZ/pbnz-skills
/plugin install newton@pbnz-skills
```

The Claude.ai-compatible single-file download is still produced as a release asset on every tag: [`newton.SKILL.md`](https://github.com/PBNZ/pbnz-skills/releases/latest/download/newton.SKILL.md).

For all other use cases, prefer the new repo.

## Repository layout

```
.
├── .claude-plugin/
│   └── marketplace.json         # Claude Code marketplace manifest
├── plugins/
│   └── newton/                  # Frozen — see PBNZ/newton-skill for current
│       ├── .claude-plugin/
│       │   └── plugin.json
│       ├── skills/newton/SKILL.md
│       └── README.md
├── .github/
│   ├── ISSUE_TEMPLATE/
│   ├── PULL_REQUEST_TEMPLATE.md
│   └── workflows/
│       ├── validate.yml
│       └── release.yml
├── scripts/                     # Validators
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

For Newton specifically, please open issues and pull requests against [PBNZ/newton-skill](https://github.com/PBNZ/newton-skill) — that's where active development lives.

## Security

See [SECURITY.md](SECURITY.md) for how to report a vulnerability.

## Licence

[Apache-2.0](LICENSE). Copyright 2026 PBNZ.
