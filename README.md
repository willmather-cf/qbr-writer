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

### Be More Ambitious

Takes a prompt or a recurring chore that feels small and rewrites it into a
deeper version an agent can still finish and something outside the model can
still check. It asks three questions:

- **Altitude:** what should happen after this is done? ("Fix this crash"
  becomes "keep the app crash-free".)
- **Depth:** how would the best expert do it, with what raw data, tools, and
  hard number?
- **Range:** what job does this deliverable really do, and which other
  fields already do that job well?

It also checks what data and tools the agent can actually reach, and names
an outside check so the model never grades its own work. You get one block to
paste into an agent, plus what was cut and why. Built on Felix Rieseberg's
essay "How to be more ambitious: A tutorial for humans with models".

Use it before work starts, not to do the work.

### World-Class Charts

Give it your numbers and the question the chart should answer. It picks the
right chart type, writes the takeaway as the subtitle, labels the data
directly, highlights the one thing that matters, and draws it in Cloudflare
brand colors as an image (SVG) you can drop into a slide or doc. You also get
a data table with the same numbers, and a 0 to 10 quality score. It never
fills in missing numbers.

Pairs with QBR Slide Writer: that skill names the visual a slide needs, this
one draws it. The original React component library, with live interactive
charts and a full test harness, lives at
github.com/willmather95/world-class-charts.

## How to use them (for now)

Until these are in the shared skills library, use them by pasting:

1. Open the skill's `SKILL.md` and copy everything in it (the copy icon at
   the top right of the file works). Then copy the files in its
   `references` folder too.
   - QBR Slide Writer: [`SKILL.md`](skills/qbr-slide-writer/SKILL.md) and
     [`reference-deck-patterns.md`](skills/qbr-slide-writer/references/reference-deck-patterns.md)
   - Human Copy: [`SKILL.md`](skills/human-copy/SKILL.md),
     [`seven-passes.md`](skills/human-copy/references/seven-passes.md), and
     [`detect-protocol.md`](skills/human-copy/references/detect-protocol.md)
   - Be More Ambitious: [`SKILL.md`](skills/be-more-ambitious/SKILL.md) and
     [`worked-example.md`](skills/be-more-ambitious/references/worked-example.md)
   - World-Class Charts: [`SKILL.md`](skills/world-class-charts/SKILL.md),
     [`chart-choice.md`](skills/world-class-charts/references/chart-choice.md),
     [`svg-and-brand.md`](skills/world-class-charts/references/svg-and-brand.md),
     and [`qa-checklist.md`](skills/world-class-charts/references/qa-checklist.md)
2. Start a new chat with your AI assistant and paste them in.
3. Underneath, write **"Use this skill on the below"** and add your content:
   - **QBR Slide Writer:** what happened, the numbers (and which are final),
     the one takeaway, and who reviews the deck. One slide at a time.
   - **Human Copy:** the text to clean, and who it is for.
   - **Be More Ambitious:** the prompt or task, and what data or tools the
     agent can reach, if you know.
   - **World-Class Charts:** the numbers, the question the chart answers,
     and where it will go (slide or doc).

## Once they are in the shared library

Nobody will need to paste anything. In any chat, describe what you need, for
example *"Turn these campaign numbers into an executive slide"*, *"Human
check this"*, or *"Am I thinking too small?"*, or *"Chart this"*, or type
`/qbr-slide-writer`, `/human-copy`, `/be-more-ambitious`, or
`/world-class-charts`.

## What is in this repo

| Path | What it is |
|------|------------|
| `skills/qbr-slide-writer/SKILL.md` | QBR Slide Writer |
| `skills/qbr-slide-writer/references/reference-deck-patterns.md` | Slide types, story order, and headline conventions from a strong Brand Marketing QBR (placeholder numbers only) |
| `skills/human-copy/SKILL.md` | Human Copy |
| `skills/human-copy/references/seven-passes.md` | The full seven passes and word lists |
| `skills/human-copy/references/detect-protocol.md` | How Human Copy decides AI or human in review-only mode, and what never to flag |
| `skills/human-copy/references/eval-checklist.md` | Test inputs and pass/fail checks for Human Copy |
| `skills/be-more-ambitious/SKILL.md` | Be More Ambitious |
| `skills/be-more-ambitious/references/worked-example.md` | A full before-and-after: weekly ads report to standing ad-health system (illustrative numbers) |
| `skills/be-more-ambitious/references/routing-checks.md` | Requests that should and should not trigger it |
| `skills/world-class-charts/SKILL.md` | World-Class Charts |
| `skills/world-class-charts/references/` | Chart choice, labeling, formatting, SVG and brand rules, QA rubric, pattern catalog, benchmark teardown, sources |
| `.opencode/commands/` | The `/qbr-slide-writer`, `/human-copy`, `/be-more-ambitious`, and `/world-class-charts` commands, used once the skills are in the library |

## Suggesting changes

Open an issue in this repo, or message Will.
