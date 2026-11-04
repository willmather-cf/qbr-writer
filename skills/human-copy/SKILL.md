---
name: human-copy
description: Strip detectable AI writing patterns from any draft before it ships, returning a flagged audit and a cleaned rewrite, or the audit alone when asked to review without rewriting.
owner: Will Mather
group: Generic
context:
  - voice/writing-guidelines.md
  - voice/banned-vocabulary.md
  - facts/company.json
  - facts/network.json
---

# Human Copy

Every piece of written content passes this gate before it goes live: blog
posts, emails, landing pages, social posts, ad scripts, slide copy. The goal
is not to make copy "sound human" in the abstract. It is to remove the
specific, documented patterns that trained readers and detection tools use to
spot machine-written text: tell-tale vocabulary, rule-of-three triads,
inflated copulas, uniform rhythm, vague claims, and em dashes. Seven passes
catch them. The output is a scannable audit plus the cleaned copy.

## When To Use

Use this after drafting any content, after repurposing or splitting long
content into smaller pieces (the pieces inherit the parent's patterns), and
before publishing anything live. It also runs on its own on any pasted text.

Trigger phrases:

- "Does this sound AI?"
- "Human check this."
- "AI slop check."
- "Clean the copy."
- "Make this sound human."
- "Remove the AI tells."

Review only, no rewrite:

- "Flag without rewriting."
- "Audit this for AI tells."
- "Scan this but don't change it."

Or the operator runs `/human-copy`.

Run it as the last step after any content skill and before the copy is
shared: content skill, then `human-copy`, then publish. For a broader
pre-send review of facts and claims, use `challenger`; for executive
messaging coaching, use `messaging-coach`.

## Inputs

Collect conversationally. If the operator pastes the text with the request,
start immediately. Do not ask which mode to use; infer it from their words.

- Required:
  - The text to check, pasted or as a file in the workspace.
- Optional:
  - Whether to rewrite or only review. Default is rewrite. Phrases like "flag
    without rewriting", "audit only", or "don't change it" mean review only.
  - The channel and audience (for example LinkedIn post for CISOs, product
    page, internal email), which calibrates how far the rhythm pass goes.
    Without it, infer from the text.
  - Real specifics the operator can supply (numbers, names, quotes), so vague
    claims can be made concrete without guessing.
  - A project or brand voice guide to apply on top of the cleaned copy.

If a vague claim needs a specific that is not in the text or supplied by the
operator, leave a visible placeholder and flag it. Never invent a number,
name, or quote.

## Context

- `voice/writing-guidelines.md` is the house voice: short sentences carry the
  point, clean A/B contrasts, plain words, specifics over superlatives, and
  closers that resolve instead of summarizing. Apply it on top of the seven
  passes. Its contrast pattern ("Deploy code, not clusters.") is allowed even
  though Pass 2 removes "not just X, but also Y".
- `voice/banned-vocabulary.md` is the house stop list. Every entry is treated
  as a Tier 1 word in Pass 1.
- `facts/company.json` and `facts/network.json` are the approved sources for
  Cloudflare metrics. Read them only when the copy makes a Cloudflare claim
  that Pass 5 needs to make specific. If the figure is not there, flag it.

The seven passes, word tables, and quick reference card live in
`references/seven-passes.md`, bundled with this skill.

## Workflow

The operator pastes the text; the steps below happen on their behalf.

1. **Read the request and set the mode.** Decide rewrite (default) or review
   only from the operator's words. Note the channel and audience if given.
   State both back in one line, for example "Rewriting a LinkedIn post for
   security leaders."
2. **Load the rules.** Read `references/seven-passes.md`,
   `voice/writing-guidelines.md`, and `voice/banned-vocabulary.md`.
3. **Run Passes 1 to 3.** Vocabulary purge using the tier rules and the house
   stop list, structural pattern removal, and copula restoration. Log every
   hit with the quoted text, category, tier, and severity.
4. **Run Pass 4.** Check sentence rhythm and match it to the channel:
   fragments for marketing and social, a lighter touch for executive and
   reference copy.
5. **Run Pass 5.** Make vague claims specific using only the source text, the
   operator's details, or the approved fact files. Otherwise insert
   `[NEEDS SPECIFIC: ...]` and flag it.
6. **Run Pass 6.** Remove every em dash, en dash, and curly quote, extra
   bold, title-case headings, and leaked formatting.
7. **Run Pass 7.** Read the copy as a person would say it. Cut padding,
   chatbot artifacts, and generic conclusions. Check that it has an opinion
   and at least one original observation; flag it if the source has none.
8. **Apply the voice overlay.** If the operator supplied a voice guide, apply
   it now on top of the clean copy.
9. **Second pass.** Re-scan the rewrite (or the original in review-only mode)
   for anything that survived: recycled transitions, lingering inflation,
   copula swaps such as "remains" or "holds". Then write the artifact.

## Output

One Markdown artifact saved to the shared outputs folder as
`human-copy-<topic>.md`, where `<topic>` is a short slug for the piece. It
holds four sections, in order:

1. **Flags.** A table with one row per hit: #, Quoted text, Pattern
   category, Tier, Severity (High, Medium, Low).
2. **Rewrite.** The full cleaned copy. Skipped in review-only mode.
3. **Change summary.** Bullets on what was cut, swapped, and restructured,
   the placeholders left for the operator, and the word count before and
   after. Skipped in review-only mode.
4. **Second-pass audit.** Anything that survived, or "Second pass clean." In
   review-only mode this is the main signal: it separates hard problems from
   judgment calls.

Also show the rewrite (or the flags, in review-only mode) in the chat reply
so the operator can copy it straight away.

## Quality Bar

- Every Tier 1 word and every house stop-list word is gone from the rewrite.
  Tier 2 and Tier 3 words are fixed only when they hit their density rule.
- Zero em dashes, en dashes, or curly quotes in the rewrite.
- Structural tells (rule of three, negative parallelism, "despite"
  conclusions, superficial analysis phrases, significance inflation) are
  fixed. A clean house A/B contrast is kept.
- No run of 5+ sentences of similar length.
- No invented specifics. Every new number, name, or detail comes from the
  source, the operator, or an approved fact file. Gaps are placeholders and
  flags.
- The meaning is kept. The rewrite says the same thing, tighter; it does not
  add claims the source did not make.
- No over-correction. If the rewrite reads stilted, that is a B, not an A.
- Review-only mode changes nothing in the operator's text.
- Grade A is the bar: real patterns caught, and a trained reader would not
  flag the result as AI-written.

## References

| File | Purpose |
|------|---------|
| `references/seven-passes.md` | The full seven passes: tiered word tables, structural patterns, copula swaps, rhythm, specificity, formatting, the human test, the quick reference card, grading, and sources. Read before every run. |
| `references/eval-checklist.md` | Pass/fail criteria and test inputs for checking the skill after any change. |
