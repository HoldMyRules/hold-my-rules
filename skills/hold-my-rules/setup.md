# Hold My Rules — setup, saving, and automation

Follow this file when the user wants to create, revise, or automate their
`CLAUDE.md` rules file, or marks a rule to be saved. For applying rules during
ordinary work, stay in `SKILL.md`; you do not need this file for that.

## Scope: two homes for rules

- **All your work** — the file at `~/.claude/CLAUDE.md`. Home for general
  working-style preferences.
- **Just this project** — a `CLAUDE.md` in the project's root. Home for that
  project's purpose, audience, decisions, and boundaries.

Claude Code reads whichever exist. When a rule could go in either, prefer the
project file unless the user says it is general. When you ask which the user
wants, accept any equivalent answer: "all my work", "all work", "all",
"everywhere", "everything", "all projects", "global" all mean all your work;
"here", "this one", "this project", "just this" mean this project only.

Assume the user may not know what `CLAUDE.md` is. The first time it comes up,
say in one sentence what it does — a file Claude reads at the start of every
session and follows.

Never overwrite or restructure an existing `CLAUDE.md` on your own. Creating
the file the first time always needs a plain yes from the user.

## First-use offer

Do not launch the interview unprompted. The one exception: the first time the
skill is active for a rules-related task and no `CLAUDE.md` is in play (neither
`~/.claude/CLAUDE.md` nor one in the project), offer three choices in one short
message, quiz recommended:

1. **Guided quiz (recommended).** The interview below.
2. **Start a blank one and build it up.** Create a short `CLAUDE.md` stub now
   (see "Capturing rules as you go"), then add to it as the user marks rules.
3. **Nothing for now.** No file; the skill still works from what the user says.
   Mention that "always…" or "hold my rule" later will start option 2.

If the user declines or ignores the offer, drop it and do not raise it again
unless they ask.

## Guided setup (quiz)

Trigger: "set up my rules", "set up Hold My Rules", "help me build my
CLAUDE.md", or the skill invoked by name for setup. The user can return to it
any time by asking.

### Interview

Ask in plain language, a few at a time, not one long form. Keep it short.
"None", "skip", "not sure" are fine answers. Do not push a house style or
suggest preferences the user has not raised — you are recording their choices,
not supplying your own.

1. **Purpose.** What is this project and what are you trying to produce?
2. **Audience.** Who is the output for, and what do they already know?
3. **Working style.** How should Claude work with you? e.g. brief vs detailed
   answers; ask first vs make a call and flag it; do only what is asked vs also
   suggest improvements.
4. **Output requirements.** Fixed requirements for what Claude produces —
   format, structure, file types, length, voice? Anything to always or never
   include?
5. **Scope and decisions.** Anything out of scope? Decisions already made that
   should not be reopened? Anything to check before doing?
6. **Editing and preservation.** When editing existing files, what must stay
   untouched? How small should changes be by default?
7. **Definition of done.** How do you know a task is finished and correct?
8. **Voice sample (optional).** A short piece of the user's own writing to
   match their voice.

### Draft

Build from the structure in `CLAUDE.md.example` in this skill's folder. Fill
only the sections the user answered; keep the rest short or omit. Use the
user's own words. Invent nothing. Note which lines are general preferences
(candidates for `~/.claude/CLAUDE.md`) and which are project-specific.

### Review and save

- Show the full draft in chat first.
- Decide with the user where it lives. Mostly general preferences →
  `~/.claude/CLAUDE.md`. About one project → that project's root. Splitting
  across both is fine. Confirm the path; save only after a clear yes.
- If a `CLAUDE.md` already exists, do not overwrite it. Show what you would add
  or change and let the user merge it, or save the draft as `CLAUDE.draft.md`
  for comparison.
- Offer to add `Use the hold-my-rules skill.` to the file so the skill loads
  each session. Add it only if the user agrees.
- The file is normally `CLAUDE.md`. For a self-named file, save the rules as
  `hold-my-rules.md` and add `@hold-my-rules.md` to `CLAUDE.md`.
- Tell the user it is a starting point they can edit freely and re-run any
  time.

The result is only as good as the answers given. It is a working document, not
a fixed contract.

## Making it automatic

Trigger (brand name or plain English): "make Hold My Rules automatic", "make
sure you always follow my rules", "set this up so it runs every time", "make
this automatic for this project".

1. If the user seems unfamiliar with `CLAUDE.md`, say in one sentence what it
   is, then ask: "Just this project, or all your work?"
2. Find or create the matching file — project root `CLAUDE.md` for this
   project, `~/.claude/CLAUDE.md` for all your work. Creating it needs a plain
   yes; name the file you would create.
3. If `Use the hold-my-rules skill.` is not in that file, add it. If the user
   keeps rules in a separate file such as `hold-my-rules.md`, ensure
   `CLAUDE.md` has `@hold-my-rules.md`.
4. Change nothing else.
5. Confirm plainly: "Done. Your rules are in `<file>` and will load every time
   you start Claude `<here / on any project>`. Tell me to turn it off any
   time."

**Turning it off** — "turn off automatic rules", "stop loading my rules every
session": remove the `Use the hold-my-rules skill.` line (and the
`@hold-my-rules.md` import if the user wants). Leave the rest alone; confirm in
one line.

"Every time" means the rules are placed in front of Claude at session start,
not that Claude can never miss one. Do not call it enforcement or a guarantee.
This flow edits Markdown only — never `settings.json`.

## Capturing rules as you go

For a user who wants rules to stick without managing a file.

### Triggers

Capture a statement as a standing rule when the user either:

- phrases it as durable — "always…", "from now on…", "never…", "for this
  project…", or the equivalent in their own language; or
- says **"hold my rule"** about the statement they just made.

A one-off request for the current task is not a trigger. If it is unclear, ask:
"Save that to your rules, or just for now?"

### Which file

General working-style rule → `~/.claude/CLAUDE.md`. Rule tied to this project →
the project's `CLAUDE.md`. Unclear → ask "Just this project, or all your
work?"

### If that file does not exist yet

Ask once, naming the file — e.g. "I can start `~/.claude/CLAUDE.md` so this
applies to all your work — want that?" On a yes, create a short stub from the
headings in `CLAUDE.md.example` and add the rule. On a no, keep applying it for
the session and do not ask again unless the user marks another rule.

### Adding a rule

- Put it under the section it fits; add a heading only if none fits.
- Use the user's own words; do not reword or generalize the intent.
- Skip duplicates. If it contradicts an existing line, name the conflict and
  ask which wins before changing anything.
- Confirm in one line: `Added to your rules: <the rule>.` No file recap.

### Changing or removing a rule

Triggers: "update my rule about X", "change that to…", "drop the rule about X",
"forget that rule".

- Find the line meant. If several could match, quote them and ask which.
- Change or delete that line only. Do not touch, reorder, or reformat anything
  else.
- If no line matches, say so rather than guessing.
- Confirm: `Updated: <old> -> <new>.` or `Removed: <the rule>.`

### Boundaries

- Only capture what the user marked. Do not log preferences you merely
  inferred from how they worked.
- Append or single-line change only — never reorganize the rest of the file.
- The user can edit or delete anything in `CLAUDE.md` at any time; it is their
  file.
