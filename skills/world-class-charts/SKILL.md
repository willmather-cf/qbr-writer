---
name: world-class-charts
description: Turn a dataset and the question it answers into one on-brand, accessible chart drawn as a self-contained SVG, built to the standard of the best newsroom and product chart teams.
owner: Will Mather
group: Generic
context:
  - brand/design-system.md
  - voice/writing-guidelines.md
---

# World-Class Charts

A world-class chart answers one question at a glance, labels itself, works
for every reader, and fits the brand. Give this skill the numbers and the
question the chart should answer. It picks the right chart type, writes the
takeaway as the subtitle, labels the data directly, highlights one thing,
and draws it as one static SVG ready for a slide, a doc, or an email, with a
data table alongside. The method comes from the original world-class-charts
library, which studied the FT, the NYT, Datawrapper, Stripe, Apple, and
others; this skill carries its rules into Cloudflare OS.

## When To Use

Use this whenever someone needs a chart, a KPI strip, or a set of charts for
a deck, doc, or report, or when a chart they already have looks flat,
generic, or default.

Trigger phrases:

- "Chart this."
- "Make a chart of these numbers for my QBR."
- "What's the best way to show this data?"
- "This chart looks generic. Make it world class."
- "Turn this table into a visual."

Or the operator runs `/world-class-charts`.

It pairs with `qbr-slide-writer`: that skill names the visual a slide needs;
this skill draws it. For a live, clickable dashboard rather than a static
chart, use `app` and apply this skill's references to the charts inside it.

## Inputs

Collect conversationally. If the operator pastes the data with the request,
extract and confirm rather than re-asking.

- Required:
  - The numbers: pasted, a table, or a file in the workspace.
  - The question the chart should answer, in one sentence ("Are we on pace
    for the quarter?"). If the operator does not give one, propose it and
    confirm.
- Optional:
  - Where it will live (slide, doc, email), which sets the canvas size.
    Default is a 16:9 slide.
  - The takeaway the operator wants the room to see. Without it, write one
    from the numbers and confirm.
  - Targets, goals, prior-period values, or events worth annotating.
  - The source of the numbers, for the source line.

Use only the operator's numbers. If a value is missing, show it as missing
and flag it. Never estimate, smooth over, or invent a data point.

## Context

- `brand/design-system.md` supplies the Cloudflare color tokens, type, and
  the no-go list. Every color in the chart maps to a role in
  `references/svg-and-brand.md`, which is built from these tokens.
- `voice/writing-guidelines.md` sets the voice for the title, subtitle,
  annotations, and source line: plain words, a specific claim, no
  superlatives.

The chart method lives in the references bundled with this skill. Names in
backticks inside them, such as `TrendAreaChart`, are chart patterns from the
original React library; here, draw the pattern as SVG.

## Workflow

The operator supplies the numbers and the question; the steps below happen
on their behalf.

1. **Write the question.** One sentence the chart answers. If one number
   answers it, make a stat (big number, change, comparison) instead of a
   chart.
2. **Pick the chart.** Use `references/chart-choice.md`. If two fit, pick
   the one with fewer marks. When the operator points at an example, match
   it with `references/catalog.md`.
3. **Write the title and takeaway.** The title names the measure ("Quality
   visits by month"). The subtitle says what it means, with a number
   ("Up 20% on last quarter, short of the goal"). State the question, chart
   type, and takeaway back in one line.
4. **Format every number.** Apply `references/formatting.md`: exact in the
   table, compact on axes, true minus sign, year once on time axes, ranges
   with "to".
5. **Label directly.** Apply `references/labeling.md`: series names at line
   ends, value labels on the highlight only, targets and annotations in
   words, a key only when labels cannot fit.
6. **Draw the SVG.** Follow `references/svg-and-brand.md` for canvas, color
   roles, type, marks, and access (`role="img"`, `<title>`, `<desc>`).
   Highlight one mark; ghost the rest.
7. **Score it.** Run `references/qa-checklist.md`. Ship at 9 or more. At 7
   or 8, fix the lowest line and score again. Under 7, rework the chart
   choice. Then write the artifact.

## Output

One SVG saved to the shared outputs folder as `<chart-slug>.svg`, where
`<chart-slug>` is a short slug for the measure (for example
`quality-visits-by-month.svg`). It is self-contained: no script, no external
images, Inter from Google Fonts as the only external reference.

In the chat reply, include:

- The question, chart type, and takeaway in one line.
- A Markdown data table with the same numbers as the chart.
- The QA score, and any flags (missing values, numbers that need a source).

For a set of charts, write one SVG per chart and score each one.

## Quality Bar

- The chart answers one question, and the subtitle states the takeaway with
  a number.
- The chart type is the best fit in `references/chart-choice.md`. No pie
  with more than 3 slices, no 3D, no dual axes, no gauges.
- Bars start at zero. Time runs left to right. Categories are sorted.
- One highlight in brand orange, directly labeled. Everything else follows
  the ghost rule.
- Every color maps to a role in `references/svg-and-brand.md`. Five colors
  at most.
- Numbers follow `references/formatting.md` and match the operator's data
  exactly. Missing is never shown as zero. Nothing is invented.
- Accessible as a static file: title, desc, 4.5:1 text, nothing by color
  alone, no text under 12px, a data table alongside.
- No em dashes or en dashes in chart text. Ranges use "to".
- QA score of 9 or more before delivery.

## References

| File | Purpose |
|------|---------|
| `references/chart-choice.md` | The question the reader asks, the best chart, what is fine, and what to avoid. Read every run. |
| `references/labeling.md` | Direct labels, annotations, reference lines, highlighting one thing, text rules. |
| `references/formatting.md` | Number, axis, and date rules for static charts. |
| `references/svg-and-brand.md` | Canvas sizes, Cloudflare color roles, type, marks, and static accessibility. |
| `references/qa-checklist.md` | Pre-ship checklist and the 0 to 10 rubric for static charts. |
| `references/catalog.md` | Common dashboard patterns, for "make one like that" requests. |
| `references/benchmark-teardown.md` | What the best chart teams do and why each rule exists. |
| `references/sources.md` | Every public source behind the method. |
