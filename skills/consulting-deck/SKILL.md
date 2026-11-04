---
name: consulting-deck
description: Build a consulting-grade internal deck as a Cloudflare slides file, storyline first, with insight copy layered on by qbr-slide-writer, charts drawn by world-class-charts, and a human-copy finish.
owner: Will Mather
group: Generic
context:
  - voice/writing-guidelines.md
  - voice/banned-vocabulary.md
  - facts/company.json
  - facts/network.json
  - brand/design-system.md
  - mappings/icon-catalog.json
---

# Consulting Deck

Build a whole deck the way a strategy consultant would: decide what the room
must conclude, write the argument as a run of one-line assertions, prove each
one with a single piece of evidence, and only then build slides. The skill
runs in three passes (understand, structure, visualize) and then layers on two
specialist skills: `qbr-slide-writer` sharpens the insight copy on every
results slide, and `world-class-charts` draws every chart. `human-copy` runs
last. The result is a Cloudflare slides file that opens in the slides viewer
with PPTX and PDF export, plus a short notes file with the storyline, sources,
chart placements, and open gaps. It never invents a number.

## When To Use

Use this when someone needs a full deck that has to persuade or support a
decision: a QBR or business review, a recommendation to leadership, a
strategy or market readout, a program proposal, or an internal solution deck.

Trigger phrases:

- "Build me a deck on this."
- "Turn this research into a consulting-style deck."
- "Make the QBR deck from these numbers."
- "I need slides that get leadership to approve this."

Or the operator runs `/consulting-deck`.

Use `slides` for a customer-facing Cloudflare prospect pitch, `account-plan`
for an account strategy deck, and `qbr-prep` for a QBR outline without
slides. Use `qbr-slide-writer` alone when the reviewer's own template owns the
deck and only paste-ready copy is needed for a slide or two.

## Inputs

Collect conversationally. If the operator gives everything up front, extract
and restate it rather than re-asking. Ask one plain question at a time for
anything required that is missing.

- Required, the deck definition (write these down before any slide exists):
  - Audience: who reads or watches it.
  - Decision: the judgement the deck has to support.
  - Objective: what the deck must achieve.
  - Core question: the one question the deck answers.
  - Final message: the one sentence the room should remember.
  - Evidence standard: how much proof this audience expects (see
    `references/argument-discipline.md`).
  - The source material: numbers, research, notes, a prior deck, or links.
- Optional:
  - Where the deck ends up: the Cloudflare slides viewer (default) or the
    reviewer's own template. Ask rather than assume.
  - A prior deck to mirror for story order and headline cadence.
  - Account naming locks and banned words.
  - A target length.

If the operator wants to move fast, state your assumptions for any missing
definition item in the notes file and on the executive summary slide, so a
reader can correct them cheaply.

## Context

- `voice/writing-guidelines.md` and `voice/banned-vocabulary.md` govern every
  title, subtitle, and item. Read both before writing the storyline.
- `facts/company.json` and `facts/network.json` are the only source for
  Cloudflare metrics. Never hardcode a Cloudflare number from memory.
- `brand/design-system.md` supplies the brand colors the charts use and the
  look the slides viewer renders. Do not restyle the deck by hand.
- `mappings/icon-catalog.json` is the only source of icon names. Use icons
  sparingly; an icon on every card is a machine-made signature.

The skill also bundles three references, listed at the end. Where a reference
conflicts with the Quality Bar, the Quality Bar wins.

## Workflow

The operator describes the deck; the steps below happen on their behalf.

### Pass 1: Understand

1. **Define the deck.** Confirm the six definition answers and the
   destination. Name the evidence standard from
   `references/argument-discipline.md`, because a deck built to the wrong
   standard fails even when each slide is good.
2. **Sort the evidence.** Read all source material. Tag every claim as Fact
   (supplied or verifiable, with a source), Inference, Hypothesis, or
   Recommendation. Where a needed number is missing, write `DATA REQUIRED:
   <what>`; where a claim needs checking, write `TO BE VALIDATED: <what>`.
   Pull Cloudflare metrics only from the facts files.

### Pass 2: Structure

3. **Pick the skeleton.** Choose the closest storyline skeleton from
   `references/narrative-patterns.md` (business review, recommendation,
   research readout, or solution). Use a framework such as SWOT or a 2x2 only
   where it organizes real evidence; drop it the moment it creates empty
   cells.
4. **Write the storyline.** One assertion per slide, in order. Push every
   significant number down the "so what?" ladder until it reaches a decision.
   Where a claim needs more than two slides, coin a short countable or
   pronounceable running thesis and repeat it verbatim across the run. Then
   read the titles alone, in order, as prose. If they read as a list of
   topics rather than an argument, rewrite before going further.
5. **Spec every slide.** One row per slide: number, purpose, message title,
   evidence and source, visual form, takeaway, claim type, and the layer it
   needs (Insight, Chart, both, or none). Delete rows that repeat a point.
   Show the operator the storyline and spec for approval before building.

### Pass 3: Visualize, then layer

6. **Layer the insights with `qbr-slide-writer`.** For every slide that
   reports a result, a test, a launch, a migration, or a retirement, load the
   `qbr-slide-writer` skill and run its workflow on that slide, steps 1 to 7,
   using the spec row as the input. Take its Headline as the slide title, its
   Subhead as the subtitle, its Recommendation as the forward action, and its
   Footnotes as the source line. If the operator already has a
   `qbr-slides-<topic>.md` file, reuse those blocks instead of rewriting
   them. Do not write that skill's artifact again; the copy goes straight
   into the deck.
7. **Layer the charts with `world-class-charts`.** For every slide whose
   visual form is a chart, load the `world-class-charts` skill and run its
   workflow with the slide's numbers, its message title as the takeaway, and
   the 1200x675 slide canvas. Ship only charts that score 9 or more on its QA
   checklist. Name each file `<deck-slug>-s<NN>-<chart-slug>.svg` so it maps
   to its slide. On the slide itself, carry the headline number in a
   `statCallout` or `stats` layout, or give the chart a slide of its own with
   the takeaway as the title, and record the placement in the notes file.
8. **Build the slides file.** Map each spec row to a layout using
   `references/slidedata-mapping.md`: numbered `section` dividers with a
   one-line scope statement, a `statCallout` big stat once per section right
   after the densest slide, `comparison` for the before and after gap,
   `timeline` for a three-beat mechanism or plan, and `actionPlan` for next
   steps. Vary layout only when the information structure changes. Validate
   the file against the checks in that reference.

### Finish

9. **Run `human-copy`.** Load the `human-copy` skill and run its rewrite on
   every title, subtitle, and item in one pass. Keep every `DATA REQUIRED`
   and `TO BE VALIDATED` marker exactly as written.
10. **Run the review gates.** Title-only read again, then per-slide logic
    (what question, what answer, what proof, why the next slide follows),
    then a red team (weakest claim, conclusion that outruns its evidence,
    redundant slide, correlation read as cause, where an executive would ask
    "so what?"). Then scan for machine-made signatures: identical card
    grids, the same layout many slides in a row, bullets that restate the
    title, icon walls, false precision. Fix before saving.
11. **Save and report.** Write the slides file and the notes file, then reply.

## Output

Primary artifact: `shared/<deck-slug>.slides.json`, written as
`{ "type": "slides", "slides": SlideData[] }`. The slides viewer renders it in
Cloudflare brand with PPTX and PDF export from its toolbar.

Companion: `shared/<deck-slug>-deck-notes.md` with these sections:

- **Deck definition:** the six answers, the evidence standard, and any
  stated assumptions.
- **Storyline:** the slide titles in order, as one paragraph of prose.
- **Slide spec:** the approved spec table.
- **Chart placements:** each SVG file name, the slide it belongs on, and its
  QA score. Insert each SVG on its slide after export if the viewer does not
  place it.
- **Sources:** every figure and where it came from.
- **Flags:** every `DATA REQUIRED`, `TO BE VALIDATED`, and Hypothesis, with
  the slide number.
- **Red team:** the weakest points found and what was done about each.

The chart SVGs are written by `world-class-charts` into the same folder.

Reply with the saved paths, the slide count, the storyline in two or three
sentences, and the open flags. No office binaries and no hand-styled HTML.

## Quality Bar

- The six definition answers are written down before any slide is built,
  and the deck meets the evidence standard for its audience.
- The titles alone, read in order, form a coherent argument rather than a
  list of topics.
- One message per slide, at most five supporting items, and any line longer
  than about 80 characters becomes a chart, a table, or a footnote.
- Every significant number is interpreted down to a decision; no chart is
  left for the room to decode.
- Every slide with a figure has a source line, including the operator's own
  data.
- Fact, Inference, Hypothesis, and Recommendation stay distinct. Gaps are
  marked `DATA REQUIRED` or `TO BE VALIDATED`, never filled with an invented
  statistic, quote, customer, or result.
- Cloudflare metrics come only from the facts files; icon names only from
  the icon catalog.
- Every results slide carries `qbr-slide-writer` copy: a headline of ten
  words or fewer stating a claim, and a subtitle with the number, the date,
  and the reason.
- Every chart came from `world-class-charts`, scored 9 or more, and its file
  name maps to its slide.
- One big stat per section at most, and a running thesis, when used, is
  repeated verbatim.
- `human-copy` has run on all copy. No em dashes or en dashes; ranges use
  "to". No banned vocabulary.
- The deck shows none of the machine-made signatures listed in
  `references/argument-discipline.md`.
- The slides file passes every validation check in
  `references/slidedata-mapping.md`.

## References

| File | Purpose |
|------|---------|
| `references/argument-discipline.md` | Deck definition, evidence standards, the "so what?" ladder, claim types, chart choice, review gates, and machine-made signatures. Read at Pass 1 and again at the review gates. |
| `references/narrative-patterns.md` | Storyline skeletons (business review, recommendation, research, solution) and the recurring slide modules: big stat, running thesis, build then assemble, three-beat mechanism, visible gap, value table. Read at Pass 2. |
| `references/slidedata-mapping.md` | How each slide module maps to a Cloudflare slides layout, the field rules, chart handling, and validation checks. Read at step 8. |
