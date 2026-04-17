# Newton

Reasoning and sparring partner mode for Claude — rigorous, calibrated engagement on any topic. Honest pushback, current-sources research, reuse-before-rebuild checks, and surgical edits. Opt-in by design.

## What it does

Newton reverses some of Claude's defaults when you consciously want them reversed:

- Engages honestly instead of reflexively affirming.
- Searches current authoritative sources before making time-sensitive claims, instead of relying on training knowledge.
- Runs a reuse-before-rebuild check on "how do I build X" requests, instead of generating from scratch.
- Makes surgical edits that trace every changed line to your request, instead of drive-by "improvements".
- Flags its own uncertainty instead of hedging or confabulating.
- Recommends handoff to a different chat, tool, or Claude surface when scope outgrows the current conversation.

Newton is a reasoning *posture*, not a domain expert. It's for moments where you've decided the question deserves care — not every task needs it.

## Invocation

Newton only activates when you explicitly summon it by name. Any of these work:

- `Newton: help me think through [X]`
- `Newton — does this plan hold up?`
- `Newton, research [X] for me`
- `use Newton`, `invoke Newton`, `ask Newton`, `Newton mode`

### Quick-start mode

If you want Newton's principles applied but the visible ceremony skipped, include a quick-start signal. Any of these (or anything that communicates the same intent) trigger quick-start:

- `Newton, quick: what's the current [X]?`
- `Newton — fast`
- `Newton (quick)`
- `Newton jump start — draft a [X]`
- `Newton, skip the preamble`

In quick-start mode Newton still deliberates internally and applies its principles, but skips the planned-approach sentence and suppresses visible reuse-check reports unless the result depends on them.

## Where Newton runs best

Newton leans on a few Claude capabilities to do its work properly. On surfaces where these are unavailable, you'll still get Newton's *posture* — honest engagement, calibrated pushback, self-critique — but the research and reuse-check parts will be shallower.

| Capability | Used for | If unavailable |
|---|---|---|
| Web search | Verifying time-sensitive claims, checking current vendor docs, source ranking | Newton flags which claims are from training knowledge and should be independently verified |
| Past-conversation search | Reuse check — surfacing solutions you've already built | Newton asks whether you've tackled this before instead of checking itself |
| Visualisation / diagram tools | Recommending the right tool for diagram-shaped problems | Newton suggests external tools by name |
| Native skills (docx, pptx, xlsx, pdf, etc.) | Reuse-before-rebuild — recommending built-in skills over custom scripts | Newton falls back to recommending libraries/packages |

If your surface has these disabled and Newton seems thinner than expected, that's why.

## Surfaces this plugin supports

- **Claude Code** — install via the marketplace (see repo root README).
- **Claude Cowork** — install via Cowork's plugin management, pointing at this marketplace.
- **Claude.ai / Claude Desktop (without Cowork)** — install via the Skills settings. Download the file from the [latest release asset](https://github.com/PBNZ/pbnz-skills/releases/latest/download/newton.SKILL.md), or grab `skills/newton/SKILL.md` from the repo tree.
- **Claude API** — register the skill via the Skills API.
- **Other Agent-Skills-compatible tools** (GitHub Copilot, Cursor, OpenAI Codex, Gemini CLI, Windsurf, and others) — the `SKILL.md` follows the open [Agent Skills standard](https://agentskills.io), so point your tool's skill-ingestion mechanism at `plugins/newton/skills/newton/SKILL.md`.

## Licence

Apache-2.0. See the repository's [LICENSE](../../LICENSE) file.

## Contributing

See the repository's [CONTRIBUTING.md](../../CONTRIBUTING.md).
