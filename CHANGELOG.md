# Changelog

Notable changes to Hold My Rules are recorded here. Newest first.

## 0.1.2 — 2026-08-31

- Add `PRIVACY.md` (the plugin collects nothing, sends nothing, runs no code
  of its own) and link it from the README.
- Add `keywords` and a `homepage` link to the plugin manifest for
  discoverability.
- Add an "at a glance" use-case list to the README.

## 0.1.1 — 2026-08-31

- Add `displayName: "Hold My Rules"` to the plugin manifest so the `/plugin`
  UI shows the proper casing instead of the auto-formatted "Hold my rules".

## 0.1 — 2026-08-31

First release.

- **`skills/hold-my-rules/SKILL.md`** — the behavior layer: when to use it, the
  relationship to `CLAUDE.md` (all your work vs project), rule hierarchy,
  building a working rule set, the surgical editing protocol, a default
  plain-writing check, conflict handling, output behavior, examples, and
  limitations. Plus a guided setup quiz; flows for capturing, changing, and
  removing rules as you go; and a plain-English flow for making the skill load
  every session. Triggers accept the brand name or plain-English phrasing.
- **`skills/hold-my-rules/CLAUDE.md.example`** — a blank, non-opinionated
  scaffold that works as an all-your-work or a project `CLAUDE.md`, with
  copy-in example lines held in comments.
- **Plugin packaging** — `.claude-plugin/plugin.json` and
  `.claude-plugin/marketplace.json` so the skill installs with
  `/plugin marketplace add HoldMyRules/hold-my-rules` and
  `/plugin install hold-my-rules@holdmyrules`.
- **`README.md`** — overview, the two-layer model, how to make the skill load
  every session, setup paths, use cases, a walkthrough, and troubleshooting.
- **`LICENSE`** — MIT.
