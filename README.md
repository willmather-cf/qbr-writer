# Will Mather's skills

Writing skills for the team, staged here until they are added to the shared
skills library. The folder layout matches the library, so the files can be
copied over as they are.

Owner: Will Mather (Marketing)

## The skills

### QBR Slide Writer

Turns a slide's raw numbers and the point you want to make into executive QBR
slide copy you can paste straight into your deck:

- **Headline:** ten words or fewer, one clear claim
- **Subhead:** one sentence with the number, the date, and the reason
- **Visual:** which chart, table, or metric boxes should carry the numbers
- **Recommendation:** one next step, naming who or what it depends on
- **Flags:** anything that cannot be backed up yet, so nothing gets made up

It writes the words only. Your deck template still owns the layout.

### Human Copy

Strips the patterns that make writing read as AI-generated: tell-tale words
("delve", "leverage", "robust"), rule-of-three lists, "serves as" instead of
"is", flat sentence rhythm, vague claims, and em dashes. Seven passes, then a
short audit:

- **Flags:** every pattern it caught, quoted, with severity
- **Rewrite:** the cleaned copy
- **Change summary:** what changed, and any gaps you need to fill
- **Second pass:** anything that survived

Say "flag without rewriting" if you only want the audit. It never makes up
numbers: if a claim needs a real figure, it leaves a `[NEEDS SPECIFIC: ...]`
placeholder for you.

Run it last, on anything you are about to publish, including QBR Slide Writer
output.

## How to use them (for now)

Until these are in the shared skills library, use them by pasting:

1. Open the skill's `SKILL.md` and copy everything in it (the copy icon at
   the top right of the file works). Then copy the files in its
   `references` folder too.
   - QBR Slide Writer: [`SKILL.md`](skills/qbr-slide-writer/SKILL.md) and
     [`reference-deck-patterns.md`](skills/qbr-slide-writer/references/reference-deck-patterns.md)
   - Human Copy: [`SKILL.md`](skills/human-copy/SKILL.md) and
     [`seven-passes.md`](skills/human-copy/references/seven-passes.md)
2. Start a new chat with your AI assistant and paste them in.
3. Underneath, write **"Use this skill on the below"** and add your content:
   - **QBR Slide Writer:** what happened, the numbers (and which are final),
     the one takeaway, and who reviews the deck. One slide at a time.
   - **Human Copy:** the text to clean, and who it is for.

## Once they are in the shared library

Nobody will need to paste anything. In any chat, describe what you need, for
example *"Turn these campaign numbers into an executive slide"* or *"Human
check this"*, or type `/qbr-slide-writer` or `/human-copy`.

## What is in this repo

| Path | What it is |
|------|------------|
| `skills/qbr-slide-writer/SKILL.md` | QBR Slide Writer |
| `skills/qbr-slide-writer/references/reference-deck-patterns.md` | Slide types, story order, and headline conventions from a strong Brand Marketing QBR (placeholder numbers only) |
| `skills/human-copy/SKILL.md` | Human Copy |
| `skills/human-copy/references/seven-passes.md` | The full seven passes and word lists |
| `skills/human-copy/references/eval-checklist.md` | Test inputs and pass/fail checks for Human Copy |
| `.opencode/commands/` | The `/qbr-slide-writer` and `/human-copy` commands, used once the skills are in the library |

## Suggesting changes

Open an issue in this repo, or message Will.
