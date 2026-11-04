---
name: qbr-slide-writer
description: Turn raw campaign data and talking points into executive QBR slide copy calibrated to a named reviewer's voice.
owner: Will Mather
group: Marketing
context:
  - voice/writing-guidelines.md
  - voice/banned-vocabulary.md
---

# QBR Slide Writer

Write executive QBR slide copy that lands in one glance. Feed the skill a
slide's raw numbers and the point you want to make, and it returns a takeaway
headline of ten words or fewer, a one sentence subhead that carries a number,
a date, and a reason, and a single forward recommendation. It produces copy
blocks to paste into an existing deck, not a formatted deck, because the
reviewer owns formatting. Every claim is honest, cause first, and defensible
cold.

## When To Use

Use this when you are drafting or rewriting a slide for a quarterly business
review, a monthly report, or any executive readout where one takeaway per
slide is the standard.

Trigger phrases:

- "Help me write the headline and bullets for this scorecard slide."
- "Turn these campaign numbers into an executive slide."
- "Tighten this slide so it reads like one takeaway."
- "Rework this into the reviewer's voice."

Or the operator runs `/qbr-slide-writer`.

Use it slide by slide. Run one slide to completion, paste the copy, then
start the next. Do not use it to generate a whole formatted deck; the
reviewer's template owns layout, color, and structure. To build the outline
for a whole business review, use `qbr-prep`.

## Inputs

Collect conversationally. If the operator gives everything up front, extract
and confirm rather than re-asking. Ask one plain question at a time for
anything required that is missing. Do not block on optional inputs.

- Required:
  - The slide's subject and what happened, for example, a campaign launched,
    a platform changed, a test ran, or an activity ended.
  - The numbers for the slide, and which are locked versus still under
    investigation.
  - The single takeaway the operator wants the room to leave with.
  - Who reviews the deck and who sits in the room, so tone and context depth
    are calibrated to them.
- Optional:
  - The prior quarter's deck or template, so headline cadence and section
    labels are mirrored, not reinvented. Without one, use the patterns in
    `references/reference-deck-patterns.md`.
  - Naming locks and banned words specific to the account, for example, a
    product's approved name.
  - The deep dive slide a summary line should point to, so a "Details here"
    reference can be added.

If a number cannot be sourced or defended, flag it for the operator and leave
a placeholder rather than inventing a figure.

## Context

- `voice/writing-guidelines.md` supplies the house craft rules the copy
  follows: short sentences carry the point, a clean A/B contrast is the
  primary rhetorical move, plain words beat decoration, and confidence comes
  from specifics rather than superlatives. Read it before drafting and apply
  it to every headline and subhead.
- `voice/banned-vocabulary.md` is the stop list. Read it and screen the copy
  against it, removing hedges, vendor pitch language, and filler before
  delivery.

Layer any account naming locks and banned words the operator provides on top
of these two files.

The skill also bundles `references/reference-deck-patterns.md`: the slide
types, story order, and headline conventions taken from a strong Brand
Marketing QBR. Use it to pick the slide type and mirror the reviewer's
cadence. Where it conflicts with the Quality Bar, the Quality Bar wins.

## Workflow

The operator describes the slide; the steps below happen on their behalf.

1. **Read the slide and name the event.** Classify what happened as Launch,
   Test, Migration, or Retirement. Executive summaries and section breakers
   take no label. Then pick the slide type from
   `references/reference-deck-patterns.md` (for example Executive Summary,
   Goal Attainment, Test, Impact, Campaign Performance, Stats, Study, or Deep
   Dive Table). State the label and slide type back in one line.
2. **Load the voice rules and patterns.** Read `voice/writing-guidelines.md`
   and `voice/banned-vocabulary.md` and hold them as active constraints for
   every line. Read the section of `references/reference-deck-patterns.md`
   for the chosen slide type and follow its structure.
3. **Write the headline.** Ten words or fewer, counting the event label, with
   an active verb and a claim rather than a topic. Lead with the label, then
   the takeaway. Reach for a contrast when the room needs to feel the
   difference. Count the words; if it runs over ten, cut.
4. **Write the subhead.** One sentence, two short ones at most. It carries the
   number, the date, and the reason that make the takeaway true and self
   contained, so the slide stands alone for someone who knows nothing about
   the program.
5. **Place the numbers in the visual.** Name the one table, chart, or set of
   metric boxes that carries the figures. Do not repeat those figures in
   prose. For a Test, structure the body as Hypothesis, Result, and
   Recommendation.
6. **Write the recommendation.** One forward action in a labeled box. Name the
   specific system or partner it depends on.
7. **Run the honesty and firm ground pass.** Lead with the win, state the
   constraint plainly, and force nothing positive. Cut any claim, number, or
   term that cannot be defended cold, or flag it for the operator. Name every
   entity specifically; replace vague labels such as "flagship" or "the
   platform" with the real name.
8. **Reconcile and check.** Confirm the numbers match any adjacent slide,
   remove every em dash and en dash, clear banned words, and add a "Details
   here" reference if the slide points to a deep dive. Then write the slide's
   block to the artifact, appending to the existing file if earlier slides in
   the same topic are already there.

## Output

One Markdown artifact saved to the shared outputs folder as
`qbr-slides-<topic>.md`, where `<topic>` is a short slug for the slide or
section. The file holds one block per slide with labeled fields: Event
label, Slide type, Headline, Subhead, Visual, Recommendation, Footnotes, and
Flags. Each new slide in the same topic is appended as a new block. The operator pastes each field into the
reviewer's formatted deck. Do not produce a formatted deck, a slides file, or
an office binary; the reviewer's template owns layout.

## Quality Bar

- The headline is ten words or fewer including the event label, carries an
  event label where one applies, uses an active verb, and states a claim
  rather than a topic.
- The slide makes exactly one point. If it makes two, split it.
- The subhead carries a number, a date, and a reason, and the slide is self
  contained for a reader with no program context.
- Numbers live in the visual, not duplicated in the prose.
- Every proper noun is named specifically; no vague labels stand in for a
  real entity.
- The recommendation is one forward action that names the system or partner
  it needs.
- The copy is honest: it leads with the win, states the constraint plainly,
  and forces no positivity.
- Firm ground only: no claim, number, or term appears that cannot be defended
  cold. Unknowns are flagged, never fabricated.
- No em dashes or en dashes anywhere. Ranges use "to". No banned vocabulary.
- Numbers reconcile with every adjacent slide that shows the same figure.
- The slide follows the structure of its slide type in
  `references/reference-deck-patterns.md`: a Test has Hypothesis, Result, and
  Recommendation; an Executive Summary has Highlights and Lowlights with
  "Details here" links; headline numbers carry a "(+X% Q/Q)" comparison.
- Unusual numbers and acronyms carry a footnote, and the footer reads
  "<Program> | <FYxxQx> QBR" when the reviewer's template uses one.

## References

| File | Purpose |
|------|---------|
| `references/reference-deck-patterns.md` | Story order, slide types, and headline conventions from a strong Brand Marketing QBR, with placeholder examples. Read when choosing the slide type. |
