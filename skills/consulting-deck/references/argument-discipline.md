# Argument discipline and evidence review

The layout rules decide how a slide looks. This file decides whether the slide
earns its place. Read it when defining the deck, whenever a slide shows data
without making a point, and again at the end as the review checklist.

Adapted from the `consulting-deck` skill by BotTony329 (MIT license, notice at
the end of this file). The method is kept; the PowerPoint engine is not, and
examples are rewritten with placeholders.

## Define the deck before building it

Write six answers down before any slide exists. If the operator has not given
them, ask. They change the deck more than any styling choice.

| Item | Question it answers |
|------|---------------------|
| Audience | Who reads or watches this? |
| Decision | What judgement does it have to support? |
| Objective | What must the deck achieve? |
| Core question | What one question does it answer? |
| Final message | What one sentence should the room remember? |
| Evidence standard | How much proof does this audience expect? |

Evidence standards differ more than people expect:

| Audience | What they need to see |
|----------|-----------------------|
| Executive | problem, evidence, options, recommendation, impact |
| Business review (QBR) | goal, result against goal, cause, what changes next quarter |
| Investor or finance | size, traction, differentiation, unit economics, scale |
| Customer or partner | situation, diagnosis, solution, value, path to adopt |
| Technical review | is it built, does it hold under load, what breaks |

## Spec the slides before building them

Between the storyline and the file, write one row per slide:

```
#   Purpose            Message title                          Evidence           Form     Takeaway                        Claim   Layer
6   size the result    Launch: <Program> beat goal by <X>%     <system>, <dates>  column   goal was set too low or beat     Fact    Insight + Chart
7   qualify the result Growth came from one channel, not all   channel split      bar      the win is narrow, not broad     Infer.  Chart
```

Redundancy shows up here. Deleting a row costs nothing; deleting a built slide
costs an argument.

## The "so what?" ladder

The most reliable way to turn data into advice. Push each significant piece of
evidence down the ladder until it reaches a decision.

```
EVIDENCE   <Metric> grew <X>% between <period> and <period>.
so what?   The category is expanding quickly.
so what?   Growth on that scale draws competitors and squeezes margin.
so what?   Growth alone is not a reason to invest; our position decides
           whether it pays.
```

The first rung is description, and most decks stop there. The second is
analysis. The third is where the reader's decision changes. Never leave a
significant number uninterpreted: a chart with no stated implication asks the
room to do your work.

## Four claim types

You may restructure source material aggressively. You may not invent. Keep
four kinds of claim distinct, because readers treat them differently:

- **Fact:** supplied or verifiable, with a source.
- **Inference:** a reasonable reading of the facts, labelled as such.
- **Hypothesis:** plausible, needs validation, and the slide says so.
- **Recommendation:** a proposed action that rests on the three above.

Where a number is needed and does not exist, write `DATA REQUIRED: <what>`.
Where a claim needs checking, write `TO BE VALIDATED: <what>`. A visible gap is
normal in a draft. A fabricated statistic, citation, quote, customer, or result
is not recoverable: it discredits every true number around it.

## Frameworks are tools, not the storyline

SWOT, value chain, 2x2 matrices, segmentation, PEST: reach for one when it
organizes the evidence, and drop it when it produces empty cells you feel
obliged to fill. If a quadrant has nothing real in it, the framework is wrong
for this problem. Spend the space on the two forces that matter.

## Features, capability, value

For product, platform, or program decks, never present a feature list. Walk one
capability down the chain:

```
USER NEED      "<a real question a user asks>"
CAPABILITY     what the product or program can do about it
SYSTEM ACTION  what actually happens
OUTPUT         what the user gets back
USER VALUE     what changes for them, in their terms
```

One capability walked down this chain beats twelve feature bullets. When
several need covering, run each through the chain, then pull them together in
one value table (capability, how, value).

## Choosing the visual form

| Relationship | Form |
|--------------|------|
| change over time | column for few periods, line for many |
| comparison across categories | bar, sorted by value |
| part of a whole | stacked bar, or donut with six slices or fewer |
| position on two axes | 2x2 matrix |
| sequence | left to right flow |
| plan over time | timeline |
| system structure | architecture diagram (use `diagram`) |

A chart must answer "what should I notice?" in about three seconds, usually
with one highlighted bar, a callout, or a labelled delta. If nothing stands
out, put the number in the text instead. `world-class-charts` applies these
rules in detail.

## Executive summary

For executive and business review audiences, put a summary slide near the
front, written last. Three to five findings, the recommendation, and the
expected impact. A reader who sees only that slide should understand the
argument and the ask. Skip it for a research readout that is meant to build to
its conclusion.

## Review gates

Run all three before delivery. They catch different failures.

**Title-only read.** Read every slide title, in order, as continuous prose.

- Fails: "Market. Customers. Technology. Competition. Conclusion."
- Passes: "Demand keeps growing. Core buyers now choose on price for
  performance. Digital channels carry most purchases. That opens a mid-tier
  position. Our program fills it. The pilot shows it works."

**Per-slide logic.** For each slide: what question does it answer, what is the
answer, what supports it, is that enough, what does it imply, and why does the
next slide follow? Any unclear answer means revise or cut.

**Red team.** Which claim is weakest? Which conclusion outruns its evidence?
Which slide is redundant? Where is correlation read as cause, or an assumption
shown as fact? Where would an executive ask "so what?", finance ask "prove
it", a partner ask "how?", or an engineer ask "is this built?" Fix those
before the meeting, not after.

## Machine-made signatures

Decks built carelessly by a model look alike. Check for:

- every slide built from four cards, each with an icon
- the same layout many slides in a row
- short generic bullets that restate the title
- icon walls and decorative dashboards with no analytical job
- gradients, glow, or 3D that serve no reading purpose
- false precision, such as a two-decimal percentage from a rough estimate
- buzzwords standing in for specifics
- the same point made three times in different words
- conclusions with no visible evidence

Change layout because the information changed, never for variety. The deck
should look designed, not decorated.

## What the deck must leave behind

The room should leave knowing what is happening, why it matters, and what to do
next. Data without interpretation is research; interpretation without evidence
is opinion; a recommendation without reasoning is an assertion. The job is to
connect evidence to insight to implication to decision.

---

Adapted from https://github.com/BotTony329/consulting-deck-skill

MIT License. Copyright (c) 2026 BotTony329. Permission is hereby granted, free
of charge, to any person obtaining a copy of this software and associated
documentation files (the "Software"), to deal in the Software without
restriction, including without limitation the rights to use, copy, modify,
merge, publish, distribute, sublicense, and/or sell copies of the Software, and
to permit persons to whom the Software is furnished to do so, subject to the
following conditions: The above copyright notice and this permission notice
shall be included in all copies or substantial portions of the Software. THE
SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED,
INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A
PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
