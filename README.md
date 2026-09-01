# Hold My Rules

A Claude skill for people tired of repeating themselves.

Version 0.1 ·
Source: [github.com/HoldMyRules/hold-my-rules](https://github.com/HoldMyRules/hold-my-rules)

## The problem

You tell Claude how you want something done — "keep it short", "British
spelling", "don't touch the other tabs", "we already decided to skip the
intro" — and a while later it drifts. So you say it again. Over a long task or
a full session, that adds up, and rules you set early are easy to lose.

## The two layers

Hold My Rules has two parts that work together. You can use either one on its
own.

### 1. Your rules file — where your rules live

Claude Code looks for a file named `CLAUDE.md` and reads it at the start of
every session. Whatever is in it becomes the standing instructions for that
session — so a rule you write there is one you never have to type again.

You do not need to know where to put it or what to call it. Ask Claude to "set
up Hold My Rules" and it creates the file, names it, and places it for you
(see Quick start). The rest of this section is background.

Your rules can apply to **all your work** or to **just this project**:

| Applies to | Good for | Where the file goes |
|---|---|---|
| **All your work** — every project | How you like Claude to work: tone, length, formatting, general do's and don'ts | `~/.claude/CLAUDE.md` |
| **Just this project** — and anyone who opens it | Facts and rules about this specific work: its purpose, audience, settled decisions, what not to touch | a `CLAUDE.md` in the project's top folder |

Rule of thumb: rules about how you like Claude to work → make them apply to all
your work; rules about one specific project → save them in that project; not
sure? → Claude asks. If both files exist, Claude reads both.

Hold My Rules setup handles two things for you: **where** your rules apply (all
your work, or just this project), and making the skill **load itself each
session** so you never have to ask.

This project includes a blank scaffold at
[`skills/hold-my-rules/CLAUDE.md.example`](skills/hold-my-rules/CLAUDE.md.example)
if you want to see the structure or fill one in by hand. It has labeled
sections and no opinions of its own.

### 2. The Hold My Rules skill — how the rules get applied

The skill in [`skills/hold-my-rules/`](skills/hold-my-rules/) is the behavior
layer. When it is active, it helps Claude:

- work out which of your stated rules actually apply to the task at hand,
- look before it edits, and make the smallest change that does the job,
- leave unrelated content, formatting, structure, formulas, data, and
  decisions alone,
- check its work against the relevant rules before replying, quietly,
- re-read substantive writing and strip wording that reads as generic AI
  boilerplate, matching your voice where you have shown it,
- raise a short question when two rules genuinely clash or one is unclear,
- save a rule to your `CLAUDE.md` when you mark it with "always…" or "hold my
  rule", so it carries over to later sessions, and change or remove a saved
  rule when you ask.

One layer holds the rules; the other applies them with care.

### Making sure it runs

A skill only loads when Claude judges it relevant, so it can miss the moment
you need it. Two ways to make it load every session:

**Ask in plain English.** Say "make Hold My Rules automatic" or "set this up so
it runs every time". Claude asks whether you mean just this project or all your
work, sets it up for you, and tells you how to turn it off. Nothing to edit
yourself. To undo it later, say "turn off automatic rules".

**Or add one line by hand.** Put this in your `CLAUDE.md`:

```
Use the hold-my-rules skill.
```

Use a project's `CLAUDE.md` for just that project, or `~/.claude/CLAUDE.md` for
all your work. You can also pull the skill in mid-conversation by saying "use
Hold My Rules", "use the hold-my-rules skill", or "hold my rules".

**Prefer a file with its own name?** Keep your rules in `hold-my-rules.md` and
put `@hold-my-rules.md` in `CLAUDE.md`. It loads every session the same way,
and Claude can set this up in plain English too.

## What it does not do

- It is **not perfect memory.** A rule you gave a long time ago can still fall
  out of view. If something matters, it is worth restating.
- It provides **no technical enforcement.** Nothing here blocks Claude from
  making a mistake, and the "does not sound like AI" check is a review habit,
  not a guarantee. The skill makes careful behavior the default.
- It does **not** make Claude recite your rules or show a checklist every
  turn. Ask if you want that.
- It is **not a Google Sheets connector** (yet). It can help you work more
  carefully in a spreadsheet you already have open with Claude, but it does
  not connect to Google Sheets or any other outside service.

## Installation

In Claude Code, run these two commands:

```
/plugin marketplace add HoldMyRules/hold-my-rules
/plugin install hold-my-rules@holdmyrules
```

That is the whole install — nothing to download or move. If the install
summary says "Run /reload-plugins to activate," run that too. To update later,
run `/plugin marketplace update hold-my-rules`.

<details>
<summary>Manual install instead (older Claude Code, or no plugin support)</summary>

Clone the repo and copy the skill folder into your Claude Code skills
directory:

```bash
git clone https://github.com/HoldMyRules/hold-my-rules.git
```

- **For all your work:** copy `skills/hold-my-rules` into `~/.claude/skills/`
- **Just for one project:** copy it into `<that project>/.claude/skills/`

Then start or restart Claude Code.
</details>

## Quick start

1. **Install** using the steps above.
2. **Set up your rules.** The first time the skill comes up and there is no
   `CLAUDE.md`, Claude offers three ways to go. The quiz is recommended.
   - *Guided quiz:* Claude asks a short set of questions about your style and
     boundaries, drafts the `CLAUDE.md` from your answers, shows it to you, and
     saves it once you approve.
   - *Start blank and build up:* Claude creates a short `CLAUDE.md` after you
     say yes, then adds to it as you go (see step 3).
   - *Nothing for now:* no file is created. The skill still works from what you
     say in the conversation.

   You can also trigger the quiz any time by asking Claude to "set up my rules
   with Hold My Rules". Claude never overwrites an existing `CLAUDE.md`, and the
   file is always yours to edit or delete.
3. **Work as normal.** When you give Claude working-style rules, or ask for a
   careful edit, the skill helps it apply what is in your `CLAUDE.md` and what
   you have said in the conversation. Bring it in any time by saying "use Hold
   My Rules", "use the hold-my-rules skill", or "hold my rules".
   - **Make a rule stick:** phrase it as "always…" / "from now on…" /
     "never…", or say "hold my rule". Claude saves that line to your
     `CLAUDE.md` and confirms in one line. If the scope is unclear it asks
     "just this project, or all your work?" and saves to the project file or
     the `~/.claude/CLAUDE.md` file (asking first if that file does not exist
     yet).
   - **Change or drop a rule:** say "update my rule about X" or "forget that
     rule". Claude edits or removes the single line, shows what changed, and
     leaves the rest of the file alone.

## Example use cases

At a glance:

- **Product managers** — keep every draft inside your spec's rules (length,
  scope, settled decisions) without restating them each turn.
- **Writers** — lock a voice once; every revision matches it, and Claude stops
  rewriting lines you didn't ask it to touch.
- **Docs & spreadsheets** — ask for one change and get exactly that; other
  cells, formulas, and formatting stay untouched.

In more detail:

**Product manager.** Your `CLAUDE.md` says specs stay under a page, carry no
engineering estimates, and the mobile app is out of scope for v1. An hour into
a drafting session you ask Claude to expand the "success metrics" section. It
does — within the length limit, with no estimates, and without quietly pulling
mobile back in.

**Writer.** You have set a voice for a piece: first person, dry, contractions
fine, no exclamation marks. As you revise section by section, each new
paragraph Claude writes matches that voice and reads like you wrote it, and it
stops "improving" sentences you did not ask it to change.

**Document or spreadsheet updater.** You ask Claude to update the Q3 numbers in
one table of a report you have open. It changes those cells and nothing else —
other tables, the surrounding text, the totals formulas, and the formatting
all stay as they were. If fixing Q3 properly would mean changing a formula
elsewhere, it tells you and waits for your go-ahead. (This works on a file you
are already editing with Claude; it is not a live Google Sheets integration.)

## A quick walkthrough

1. You install the skill and start Claude in your project. There is no
   `CLAUDE.md` yet, so the first time rules come up Claude offers the quiz.
2. You pick the quiz. Claude asks a few plain questions — what the project is,
   who it is for, how you like to work, anything it must not touch, how you
   know a task is done.
3. Claude shows you a short `CLAUDE.md` built from your answers, in your words.
   You change a line, then say save. It goes in the project's top folder.
4. From then on, each session starts with those rules loaded. When you say
   "from now on, use ISO dates", Claude adds that line and confirms. When you
   ask it to fix one paragraph, it fixes that paragraph and nothing else.

## If it does not seem to be working

- **Check the file name.** It must be exactly `CLAUDE.md` — not `claude.md`,
  not `CLAUDE.md.txt`.
- **Check the location.** A project's file goes in that project's top folder.
  The all-your-work file goes at `~/.claude/CLAUDE.md`, where `~` is your home
  folder. If you are not sure how to create it there, ask Claude to do it for
  you.
- **Start a fresh session.** `CLAUDE.md` is read at the start of a session, so
  changes take effect the next time you start Claude.
- **Add the load line.** If the skill does not seem to engage, put
  `Use the hold-my-rules skill.` in your `CLAUDE.md`.
- **Restate the rule once.** If something important is being missed, say it
  again in the moment, and mark it with "hold my rule" if it should be
  permanent.

## Feedback

This is version 0.1. Bug reports and suggestions are welcome as issues at
[github.com/HoldMyRules/hold-my-rules/issues](https://github.com/HoldMyRules/hold-my-rules/issues).
See [`CHANGELOG.md`](CHANGELOG.md) for what has changed.

## Privacy

Hold My Rules collects nothing, sends nothing, and runs no code of its own —
see [PRIVACY.md](PRIVACY.md).

## License

MIT — see [LICENSE](LICENSE).
