# Privacy Policy — Hold My Rules

**Effective date:** 2026-08-31

## Summary

Hold My Rules collects nothing, sends nothing, and runs no code of its own. It
is a Claude Code skill: a set of written instructions plus a blank template
file. Everything it does happens locally on your computer, inside your own
Claude Code session.

## What this plugin contains

- `skills/hold-my-rules/SKILL.md` — instructions Claude reads to follow your
  stated rules during a task.
- `skills/hold-my-rules/CLAUDE.md.example` — a blank scaffold you can copy.
- Documentation (`README.md`, `CHANGELOG.md`, `LICENSE`, this file).

It contains **no** executable programs, MCP servers, hooks, background
processes, or bundled binaries.

## Data the plugin accesses

When you ask it to, the skill helps Claude create or edit a `CLAUDE.md` rules
file — either in your project folder or at `~/.claude/CLAUDE.md` — and read
rules you have already written there. These files are created and stored only
on your own computer. The plugin does not copy, upload, or transmit them
anywhere.

The plugin does not access your browser history, credentials, contacts, or any
files other than the `CLAUDE.md` rules files described above.

## Data collection and sharing

- **Collection:** none. The plugin has no analytics, telemetry, logging, or
  usage tracking.
- **Transmission:** none. The plugin makes no network requests.
- **Third parties:** none. No data is shared with the plugin author or anyone
  else, because none is collected.
- **Cookies / identifiers:** none.

## Your Claude Code session

Your conversations with Claude Code — including any rules you type and any file
contents Claude reads while this skill is active — are processed by Anthropic
as part of the Claude Code product, under
[Anthropic's Privacy Policy](https://www.anthropic.com/legal/privacy). That
processing is a function of Claude Code itself, not of this plugin, and is not
changed by installing Hold My Rules.

## Children's privacy

Hold My Rules is a developer tool and is not directed to children under 13. It
collects no personal information from anyone.

## Changes to this policy

If this policy changes, the updated version will be published in this
repository with a new effective date, and the change will be noted in
`CHANGELOG.md`.

## Contact

Questions about this policy: open an issue at
<https://github.com/HoldMyRules/hold-my-rules/issues>.
