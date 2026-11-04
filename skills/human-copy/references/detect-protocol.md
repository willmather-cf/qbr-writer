# Detect Protocol

How `human-copy` decides whether text is AI-written, and what to flag, when
the operator asks for a review without a rewrite. It also guides the Flags
table in rewrite mode. Diagnose by mechanism, not just by list: that is how
you catch tells that appear on no list.

In review-only mode, open the Flags section with a one-line verdict:
`Verdict: AI` or `Verdict: human`, then the register (audience-facing or
self-directed) and the flag count.

## Why AI text looks the way it does

LLM training produces five convergent habits. Every tell in this skill is a surface symptom of one of them. Diagnose by mechanism, not just by list - that is how you catch tells that appear on no list:

1. **Promotional inflation.** Training rewards sounding impressive, so AI puffs everything: inflated vocabulary, significance claims, "premium/comprehensive/cutting-edge" framing, benefits stacked in tidy triads. Humans writing for real stakes undersell or get specific.
2. **Both-sides hedging.** AI avoids commitment: balanced clauses, "while X, Y", qualifiers everywhere, endings that resolve into a tidy universal sentiment. Humans pick a side and leave threads hanging.
3. **Uniform fluency.** AI produces error-free, medium-length, evenly-paced sentences with parallel grammar, every paragraph the same shape. Human writing has rhythm breaks, fragments, typos, self-interruptions, abrupt jumps.
4. **Fake depth.** AI announces that things relate instead of making claims: connector sentences ("This highlights..."), trailing participles ("...underscoring the need for..."), abstractions in place of facts. A human states the causal claim and moves on.
5. **Performed warmth.** Sycophant openers, collaborative meta-commentary, corporate-therapist affirmations, neat-bow sign-offs. Humans just say the thing.

## Verdict rule (register first, then flags)

**Step 1 - classify the register.** Who is this text FOR?

- **Audience-facing prose:** marketing copy, outreach emails, blog/landing/explainer content, listicles, product descriptions, newsletters, anything written to persuade or inform strangers. Polished parallel structure, title-like headings, and benefit-shaped list items mark this register even when it looks like an outline.
- **Self-directed artifact:** voice transcripts, working notes, terminal output, logs, messages to close collaborators. Marked by disfluency, fillers, profanity, mid-thought starts, inconsistent formatting, references the writer doesn't explain because they're writing for themselves.

**Step 2 - apply the threshold for that register.**

- **0 flags to verdict: human.** Always, in both registers.
- **Audience-facing + 1 or more flags to verdict: ai.** Audience-facing prose is exactly where LLMs are used, and a genuine tell in polished copy is decisive. A human professional writing clean copy produces zero tells, not one.
- **Self-directed + 2 or more flags to verdict: ai.** Real notes and transcripts absorb the odd business word; two genuine tells in self-directed text means it was machine-drafted.
- **Self-directed + exactly 1 flag to verdict: human.**

Subtle AI is still AI: marketing copy can carry specifics, numbers, even a tuned brand voice and still be machine-written. The strongest residual signals in de-slopped AI content: every list item the same grammatical shape, every promise pitched at an imagined reader, uniform fluency with zero mess. Listy structure is not itself a tell - but a polished, parallel, audience-pitched list is audience-facing prose, not a working note, and gets the stricter threshold.

Be exhaustive. Typical AI text carries 3-8 distinct tells, and under-flagging is the dominant failure mode. One flag per distinct substring; the same word appearing twice is two flags. Each flag is a verbatim substring, 8 words max. Never invent a substring that is not in the text.

## Scan order (one deliberate pass per family)

Do not rely on a single read - tells hide in fluent text. Scan the full text six times, once per family, and collect flags from each pass:

1. **Vocabulary** - Tier 1 words anywhere. Tier 2 words: every occurrence in audience-facing prose; only 2+ clusters in self-directed text. Tier 3 hedge/emphasis words only at 3+ per 100 words.
2. **Structural patterns** - rule-of-three triads; negative parallelisms ("not just X, but Y"); despite-conclusions; trailing participles of fake depth ("...highlighting/underscoring..."); significance inflation; empty connector sentences ("This signals/demonstrates..."); bolded-label colon bullets; staccato anaphora.
3. **Copula avoidance** - "serves as", "stands as", "functions as", "represents", "marks", "boasts" doing the job of plain is/has.
4. **Rhythm** - 5+ consecutive sentences of near-identical length and subject-verb shape (flag the most representative sentence opening, 8 words max).
5. **Formatting** - em dashes, curly quotes, deck-style boldface, leaked markdown.
6. **Openers and closers** - sycophant openings ("Great question!"), collaborative meta-commentary, corporate-therapist affirmations, neat-bow universal endings.

## What NOT to flag (human signals)

Missing a tell in AI text and flagging clean human text are equal failures. These are positive evidence of a human author - never flag them, and weigh them against an ai verdict:

- Typos, missing capitalization, profanity, slang, texting shorthand
- Filler and self-interruption: "I guess", "kind of", "you know", trailing thoughts, questions to self
- Terminal output, logs, code, file listings, raw transcripts
- Notes, outlines, and to-do fragments - listy structure alone is not a tell
- Specific names, dates, dollar amounts, and decisions with personal stakes
- Abrupt topic jumps, unresolved asides, starting mid-thought
- One ordinary business word ("leverage", "robust", "streamline") inside otherwise messy, specific text is NOT a tell - vocabulary only counts per its tier rules
- Polish alone is NOT a tell: a terse, concrete, error-free professional email with real particulars (dates, rates, section numbers) is human. Competence is not AI.
