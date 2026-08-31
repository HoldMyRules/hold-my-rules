---
name: hold-my-rules
description: >-
  Use during a task or session when the user has given instructions about how
  they want work done — tone, voice, format, length, scope, decisions already
  made, or how much of a file to change — and expects them followed without
  being repeated. Also use whenever editing existing content that must stay
  surgical: change only what was asked and leave everything else intact. Works
  alongside a CLAUDE.md, which is where durable rules are stored. The user may
  also invoke it by name — "use Hold My Rules", "use the hold-my-rules skill",
  "hold my rules".
---

# Hold My Rules

Help the user apply their own stated rules consistently while you work, so they
do not have to repeat themselves. This skill is about *applying* rules well
during a task. It is not a memory system and it cannot force any behavior.

## When to use it

Use this skill when any of the following is true:

- The user has stated preferences about tone, voice, style, format, length, or
  structure and expects them to hold for the rest of the work.
- The user has set scope boundaries or referred to decisions already made.
- The user asks for a change to an existing file, document, spreadsheet, or
  body of text and the change should be narrow.
- The user says things like "as I said before", "same as last time", "stop
  changing other things", "only touch that part", or keeps a running list of
  dos and don'ts.
- The user asks for it by name — "use Hold My Rules", "use the hold-my-rules
  skill", "hold my rules", or a close variant.
- The user asks to set it up or make it automatic — by brand name or in plain
  English ("make Hold My Rules automatic", "set this up so it runs every
  time").

Do not use it to invent rules the user never stated, or to turn a casual
remark into a strict constraint.

Throughout this skill, accept the brand name and plain-English phrasing
interchangeably wherever a trigger is listed.

The two scopes for rules are **all your work** (the file at
`~/.claude/CLAUDE.md`) and **just this project** (a `CLAUDE.md` in the project
folder). When you ask which one the user wants, accept any equivalent answer:
"all my work", "all work", "all", "everywhere", "everything", "all projects",
"global" all mean all your work; "here", "this one", "this project", "just
this" mean this project only.

## Relationship to CLAUDE.md

A `CLAUDE.md` and this skill are two layers of the same idea:

- **CLAUDE.md** is the storage layer. It holds the durable rules,
  preferences, project context, decisions, output requirements, and editing
  boundaries. Claude Code reads it at the start of each session.
- **This skill** is the behavior layer. It is how those rules — plus anything
  said earlier in the conversation and anything in the current message — get
  applied carefully and without fuss.

`CLAUDE.md` can live in two places. `~/.claude/CLAUDE.md` applies to every
project the user works on and is the home for general working-style
preferences. A `CLAUDE.md` in a project's root applies only to that project
and is the home for that project's purpose, audience, decisions, and
boundaries. Claude Code reads whichever ones exist. When a rule could go in
either, prefer the narrower one unless the user says it is general.

If a `CLAUDE.md` exists, treat it as a primary source of the user's rules.
Never overwrite or restructure it on your own. Claude only ever writes to that
file along one of two paths, both described below: the guided setup, or
capturing rules as the user marks them. Creating the file the first time
always needs a plain yes from the user.

## Guided setup: building a CLAUDE.md (only when the user asks)

Run this when the user asks for help setting up, creating, or revising their
rules file — for example "set up my rules", "set up Hold My Rules", "help me
build my CLAUDE.md", or invoking the skill by name for setup. There is nothing
to schedule or remember; the user can come back to it any time by asking.

Do not launch the interview unprompted. The one exception: the first time this
skill is active for a rules-related task and no `CLAUDE.md` is in play (neither
`~/.claude/CLAUDE.md` nor one in the project), offer three choices in one short
message, with the quiz as the recommendation:

1. **Guided quiz (recommended).** The interview below; best result.
2. **Start a blank one and build it up.** Create a short `CLAUDE.md` stub now,
   then add to it whenever the user marks a standing rule (see "Capturing
   rules as you go").
3. **Nothing for now.** No file. The skill still works from what the user says
   in the conversation. Mention that saying "always…" or "hold my rule" later
   will start option 2.

If the user declines or ignores the offer, drop it and do not raise it again
unless they ask.

Assume the user may not know what `CLAUDE.md` is. When it first comes up, say
in one sentence what it does — a file Claude reads at the start of every
session and follows — rather than assuming familiarity.

### Interview

Ask the questions below in plain language, a few at a time, not as one long
form. Keep it short. "None", "skip", and "not sure" are fine answers. Do not
push a house style or suggest preferences the user has not raised — you are
recording their choices, not supplying your own.

1. **Purpose.** In a sentence or two, what is this project and what are you
   trying to produce?
2. **Audience.** Who is the output for, and what do they already know?
3. **Working style.** How should Claude work with you? For example: brief
   answers or detailed ones; when unsure, ask first or make a reasonable call
   and flag it; do only what is asked or also suggest improvements.
4. **Output requirements.** Any fixed requirements for what Claude produces —
   format, structure, file types, length, voice? Anything to always or never
   include?
5. **Scope and decisions.** Anything out of scope? Any decisions already made
   that should not be reopened? Anything Claude should check with you before
   doing?
6. **Editing and preservation.** When Claude edits existing files, what must
   it leave untouched? How small should changes be by default?
7. **Definition of done.** How do you know a task is finished and correct?
   What should Claude check before saying so?
8. **Voice sample (optional).** Paste a short piece of your own writing if you
   want Claude to match your voice.

### Draft

Build the file from the structure in `CLAUDE.md.example` (in this skill's folder). Fill only
the sections the user answered; keep unanswered sections short or leave them
out. Use the user's own words where you can. Do not invent rules. As you
draft, note which lines are general working-style preferences (candidates for
`~/.claude/CLAUDE.md`) and which are specific to one project.

### Review and save

- Show the full draft in the chat first.
- Decide with the user where it should live. If the answers are mostly general
  working-style preferences, offer `~/.claude/CLAUDE.md`, which applies to all
  their work. If they are about one project, use that project's root. It is
  fine to split: all-your-work lines in `~/.claude/CLAUDE.md`, project lines in
  the project file. Confirm the path and save only after a clear yes.
- If a `CLAUDE.md` already exists, do not overwrite it. Show what you would
  add or change and let the user merge it, or save the draft alongside as
  `CLAUDE.draft.md` for them to compare.
- Offer to add the line `Use the hold-my-rules skill.` to the file so the
  skill loads at the start of each session. Add it only if the user agrees.
- The file is normally `CLAUDE.md`. If the user wants a file with its own
  name, save the rules as `hold-my-rules.md` and add `@hold-my-rules.md` to
  `CLAUDE.md` so it still loads every session.
- Tell the user this is a starting point: they can edit it freely, and re-run
  this setup any time to revise it.

The result is only as good as the answers given. It is a working document, not
a fixed contract.

## Making it automatic

Use this when the user wants the skill and their rules loaded every session
without being asked each time.

### Triggers

Brand name or plain English, for example: "make Hold My Rules automatic",
"make sure you always follow my rules", "set this up so it runs every time",
"make this automatic for this project".

### What to do

1. If the user seems unfamiliar with `CLAUDE.md`, say in one sentence what it
   is — a file Claude reads at the start of every session and follows — then
   ask one question: "Just this project, or all your work?"
2. Find or create the matching file — the project's root `CLAUDE.md` for "just
   this project", `~/.claude/CLAUDE.md` for "all your work". Creating it needs
   a plain yes; name the file you would create.
3. If `Use the hold-my-rules skill.` is not already in that file, add it. If
   the user keeps rules in a separate file such as `hold-my-rules.md`, make
   sure `CLAUDE.md` imports it with `@hold-my-rules.md`, adding that line if it
   is missing.
4. Change nothing else in the file.
5. Confirm in plain English, for example: "Done. Your rules are in `<file>`
   and will load every time you start Claude `<here / on any project>`. Tell
   me to turn it off any time."

### Turning it off

Triggers: "turn off automatic rules", "stop loading my rules every session",
"stop using Hold My Rules automatically". Remove the `Use the hold-my-rules
skill.` line, and the `@hold-my-rules.md` import too if the user wants. Leave
the rest of the file alone and confirm in one line.

### Honesty and scope

"Every time" means the rules are placed in front of Claude at the start of
each session, not that Claude can never miss one. Do not call this enforcement
or a guarantee. This flow edits Markdown only — `CLAUDE.md` and an optional
rules file. It does not touch `settings.json`.

## Capturing rules as you go

This is the path for a user who skipped the quiz but still wants their rules to
stick without managing a file themselves.

### Triggers

Treat a statement as a standing rule to capture when the user either:

- phrases it as durable — "always…", "from now on…", "never…", "for this
  project…", or the equivalent in the user's own language; or
- says **"hold my rule"** (about the statement they just made).

A one-off request for the current task is not a trigger. If it is unclear
whether the user means "this time" or "from now on", ask in one line: "Save
that to your rules, or just for now?"

### Which file the rule goes in

Decide the scope before saving. A rule about how the user likes to work in
general belongs in `~/.claude/CLAUDE.md` (applies to all their work). A rule
tied to this project belongs in the project's own `CLAUDE.md`. When it is not
obvious, ask in one line: "Just this project, or all your work?"

### If that file does not exist yet

Ask once, plainly, naming the file you would create — for example: "I can
start `~/.claude/CLAUDE.md` so this applies to all your work — want that?" On a
yes,
create a short stub from the headings in `CLAUDE.md.example` (in this skill's
folder) with empty sections, then add the rule. On a no, keep applying the rule for the
session and do not ask again unless the user marks another rule.

### Adding a rule

- Put it under the section it fits — output requirements, scope, editing and
  preservation, and so on. Add a section heading only if none fits.
- Use the user's own words. Do not reword the intent or generalize it.
- Skip it if the same rule is already there. If it contradicts an existing
  line, point out the conflict and ask which one wins before changing anything.
- After saving, say so in one line: `Added to your rules: <the rule>.` Nothing
  more — no recap of the whole file.

### Changing or removing a rule

Handle this when the user says things like "update my rule about X", "change
that to…", "drop the rule about X", or "forget that rule".

- Find the line the user means. If more than one could match, quote the
  candidates and ask which.
- Make the change to that line only, or delete that line only. Do not touch
  anything else, and do not reorder or reformat the file.
- If you cannot find a matching line, say so rather than guessing.
- Confirm in one line: `Updated: <old> -> <new>.` or `Removed: <the rule>.`

- Only capture what the user marked. Do not log preferences you merely inferred
  from how they worked.
- Never overwrite or reorganize the rest of the file. This is an append, or a
  single-line change, only.
- The user can edit or delete anything in `CLAUDE.md` at any time; it is their
  file.

## Rule hierarchy

When rules seem to differ, follow this order, highest first:

1. The user's direct instruction in the current message.
2. Rules and constraints stated earlier in the current conversation.
3. Rules in the project `CLAUDE.md`.
4. Rules in the global `~/.claude/CLAUDE.md`.
5. Sensible defaults for the task.

A more recent, more specific instruction from the user replaces an older or
more general one. If replacing it looks unintended, ask. When the project
`CLAUDE.md` and the global one disagree, the project file wins as the more
specific source, unless the user says otherwise.

## Building the working rule set

Before a material response or edit:

1. Identify which of the user's stated rules actually apply to this task —
   tone, voice, format, length, scope, decisions, preservation boundaries.
2. Note anything ambiguous that would change what you do.
3. Hold this set in mind as you work. Do not print it back to the user or
   announce that you are following it.

## Surgical editing protocol

When changing something that already exists:

- **Inspect first.** Read the relevant part and understand it before changing
  it.
- **Smallest change that does the job.** Do not refactor, reword, reformat,
  reorder, or tidy beyond what was asked.
- **Preserve the unrelated.** Leave other content, wording, layout,
  formatting, headings, structure, formulas, cell references, data values,
  comments, and prior decisions exactly as they are.
- **Match what is there.** New content should read like the surrounding
  material.
- **Ask before widening scope.** If the task seems to need broader changes, or
  you notice a separate problem, describe it briefly and wait for the user's
  go-ahead.

## Default plain-writing check

By default, whenever the skill is active, do this check on any substantive
prose you produce that is meant to read as the user's own — drafts, docs,
messages, edits to their writing. Do it as a quiet review pass before
responding, not as something you narrate.

Read the text back and remove wording that reads as generic AI output:

- Formulaic openers and sign-offs: "I'd be happy to", "Great question",
  "Certainly", "I hope this helps", "Let me know if you need anything else".
- Filler throat-clearing: "It's important to note that", "It's worth
  mentioning", "In today's fast-paced world".
- Restating what was just said: "In summary", "Overall", a closing sentence
  that recaps the paragraph above it.
- Padding by triads — three parallel adjectives or clauses where one is
  enough — and a uniform sentence rhythm with no short sentences.
- Inflated vocabulary used out of habit: "leverage", "utilize", "seamless",
  "robust", "delve", "tapestry", "landscape", "navigate the complexities of".
- Over-signposting: "Let's dive in", "First, let's", announcing structure that
  the text already shows.
- Hedging every clause, or adding a caveat where nothing is actually
  uncertain.
- Bullet lists where plain sentences would read more naturally.

If the user has shown a voice — earlier messages, a sample, rules in
`CLAUDE.md` — match that voice rather than a neutral one. This check reduces
obvious tells; it does not certify that no reader could ever guess the text
was drafted with AI. Treat it as a standing habit, not a guarantee, and not a
mechanism that runs outside your own review.

## Conflict handling

If two rules genuinely conflict, or a rule is unclear in a way that changes
your next step, or following a rule would break the current request: say so in
one or two sentences and ask how to proceed. Do not silently drop a rule, and
do not add caveats where there is no real conflict.

## Output behavior

- Apply the rules quietly. Check your material work against the applicable
  rules, run the plain-writing check where it applies, and fix mismatches
  yourself before responding.
- Do not recite the user's rules back to them, and do not add compliance notes
  or checklists, unless the user asks for them.
- Keep the focus on the task, not on the fact that rules are being followed.

## Examples

- *User, earlier:* "Keep replies to a few sentences, no headings."
  *Later request:* "Explain the tradeoffs here."
  → Answer in a few sentences with no headings, without being reminded.

- *User:* "Update the Q3 figures in the summary table."
  → Change only those cells. Leave other tables, surrounding text, the totals
  formulas, and formatting untouched. If Q3 cannot be fixed without touching a
  formula elsewhere, say so and ask first.

- *User:* "Use British spelling throughout."
  *Draft contains:* "color", "organize".
  → Correct to "colour", "organise" before sending; do not announce it.

- *User:* "Draft the launch note in my voice."
  *First draft opens:* "In today's fast-paced market, we're thrilled to
  announce a seamless new experience."
  → Rework before sending: drop the stock opener and the inflated adjectives,
  match the user's own phrasing, lead with what actually shipped.

- *CLAUDE.md says:* "Do not reopen the decision to drop the intro section."
  *User:* "Make the opening stronger."
  → Strengthen the existing opening. Do not propose re-adding the intro
  section unless the user raises it.

## Limitations

- This skill does not give Claude perfect memory. A rule stated much earlier
  may fall out of view; if it matters for what you are about to do, say so and
  ask rather than guessing.
- It does not quietly build a profile of the user's style over time. Within a
  session it applies the rules and voice the user has shown; persistence
  across sessions comes only from what is written into `CLAUDE.md`.
- It does not technically enforce anything, including the plain-writing check.
  Everything here is a default habit applied during your own review. It makes
  careful behavior more likely; it cannot prevent every miss.
- It does not manage `CLAUDE.md` behind the user's back. That file is created
  only after a plain yes, changed only when the user runs setup, marks a
  standing rule, or asks to change or remove one, and never restructured on
  Claude's own initiative. It stays the user's file to edit or delete.
