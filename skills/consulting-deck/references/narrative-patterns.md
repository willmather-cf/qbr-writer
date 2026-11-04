# Narrative patterns and slide modules

Storyline skeletons and the recurring slide modules a strong consulting deck is
built from. Adapted from the `consulting-deck` skill by BotTony329 (MIT
license; see `argument-discipline.md` for the notice), which drew them from a
78-slide market research report and a 51-slide solution bid. The business
review and recommendation skeletons are added for Cloudflare use. All examples
are placeholders.

## Skeleton A: business review (QBR)

Around 12 to 25 slides. Mirror the story order in
`qbr-slide-writer/references/reference-deck-patterns.md` when that skill is
installed; in short:

```
Cover                       <Program> | <FYxxQx> QBR
Executive summary           Highlights and Lowlights, each with "Details here"
Goal attainment             goal, result, (+X% Q/Q), one line on cause
1  Results                  section divider + scope line
   ├─ big stat              the quarter's defining number
   ├─ results slides        one per event: Launch, Test, Migration, Retirement
   └─ test slides           Hypothesis, Result, Recommendation
2  What we learned          the "so what?" for the quarter
3  Next quarter             plan as a three-phase timeline
Asks                        actionPlan: action, owner, date
Get involved                how others can help or reuse the work
```

## Skeleton B: recommendation to leadership

Around 8 to 15 slides. Answer first, then the proof.

```
Cover
Executive summary           the recommendation, three to five reasons, impact
1  The situation            what is true now, with one big stat
2  The problem              what it costs if nothing changes
3  Options                  two or three, compared on the same criteria
4  Recommendation           the chosen option and why it wins
   ├─ how it works          three-beat mechanism
   ├─ visible gap           today vs after
   └─ value table           capability, how, value
5  Risks and mitigations
Plan and asks               timeline + actionPlan
```

## Skeleton C: research or market readout

Around 30 to 80 slides. Four numbered chapters that build to the conclusion.

```
Cover
1  Background               why the question was asked, how the market is
                            defined, how money is made, where it is in its cycle
2  External forces          one sub-section per force that matters (policy,
                            economy, customers, technology); skip empty ones
   └─ synthesis             one line per force, then the implication
3  Competitive landscape    value chain, who plays where, a deep dive on the
                            leader, what is working
4  Synthesis                opportunities vs threats, then the recommendation
Closing
```

## Skeleton D: internal solution or program deck

Around 15 to 40 slides. Moves the reader from "why now" to "why us". For a
customer-facing Cloudflare pitch, use the `slides` skill instead.

```
Cover
Why now                     one paragraph, three external statistics with sources
Big stat                    the macro number
Where it applies            one slide per affected team or function
The solution, named         product or program name + one-line promise
   ├─ how it works          three-beat mechanism
   ├─ per-capability        need, capability, action, output, value
   ├─ visible gap           after each capability cluster
   └─ value table           all capabilities in one view
Proof                       two-slide case studies (before, then after)
Why us                      credentials, then proof specific to this work
Plan and asks
```

## The running thesis

The most distinctive move. When a claim needs more than two slides:

1. Compress the whole claim into a short formula that is countable ("one
   large market, one high growth rate, one low price, three tiers" tells the
   reader five things are coming) or pronounceable (an acronym that is also a
   word and doubles as the agenda).
2. Use that identical line as the title of every slide in the run, verbatim.
3. Under it, unpack exactly one component, with its own evidence and source.
4. Keep the section label constant across the run.

Five slides sharing one formula read as one sustained argument. Five slides
with five titles read as five facts. The formula is also what the room repeats
after you leave. A formula that is only a summary sentence will not survive
repetition; skip the device rather than force it.

## Recurring slide modules

**Message, evidence, source.** Section label, the assertion as the title, up
to five supporting items, a chart or table, a source line. The default slide.

**Big stat.** One figure, very large, with one sentence under it. About one per
section, placed straight after the densest slide to give the room a breath.

**Build, then assemble.** Several slides each prove one attribute with one
piece of evidence, then one slide pulls every attribute together. The room
watches the conclusion get built, so they own it when it lands.

**Three-beat mechanism.** Input, then what the system or team does with it,
then the output, left to right. Use the same structure on every mechanism
slide so the room learns the grammar once.

**Visible gap.** Today's process on one side, tangled and long; the new process
on the other, short and clean; one line on time or cost saved. Repeat it after
each capability cluster rather than once at the end, so the claim feels
structural rather than anecdotal.

**Value table.** Rows are capabilities; columns are what it is, how it works,
and what it is worth. The slide the economic buyer photographs.

**Case study pair.** Slide one: who, how big, and the problem in their words.
Slide two: what was done and the measured result, with the source. A case
study squeezed onto one slide loses the "before", which is where the
credibility lives. Only cite customers the operator supplies or the library's
`proof/case-studies-index.md` lists.

**Numbered section divider.** Number, section name, and a one-line scope
statement saying what this section examines.

## Evidence compression

The most common repair: raw material pasted onto slides, unreadable at
thumbnail size. Replace the pile with one slide carrying:

- the assertion as the title, with the key phrase being the claim;
- one chart carrying the quantity the pile was meant to prove;
- two or three short verbatim quotes with attribution;
- one representative example.

Everything cut goes to an appendix, referenced by slide number. The test: can
it be read from the back of the room? If not, it is texture, and texture
belongs in the appendix.

## Density limits

- One message per slide. Two messages means two slides.
- At most five supporting items under the assertion.
- A line over about 80 characters wants to become a chart, a table, or an
  appendix slide.
- Every figure has a source line, including the operator's own data.
