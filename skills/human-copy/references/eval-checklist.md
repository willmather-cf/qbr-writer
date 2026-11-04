# human-copy eval checklist

Use these to test the skill after any change. Run each test input and score
the output against every criterion.

## Criteria

1. **Vocabulary.** The output identifies and replaces at least 3 specific
   Tier 1 words (delve, tapestry, vibrant, crucial, foster, landscape,
   meticulous, underscore, showcase, testament, and so on). It cites each word
   found and its replacement. Fails if banned words survive, or if it flags
   words that are not on any list.
2. **Structure.** The output catches and fixes structural patterns: rule of
   three, "not just X, but also Y", and "despite [challenges], [subject]
   continues to [positive]". It flags at least one if present.
3. **Dashes and quotes.** Every em dash, en dash, and curly quote is gone.
   Zero tolerance.
4. **Copulas.** Inflated constructions are restored ("serves as" to "is",
   "boasts" to "has", "features" to "has"). At least one fix if present.
5. **Rhythm.** No 5+ consecutive sentences of similar length (15 to 25
   words). At least one fragment or short sentence if the input was
   monotonous.
6. **Specificity, honestly.** Every vague claim is either made specific with
   a detail from the source or the operator, or replaced with a
   `[NEEDS SPECIFIC: ...]` placeholder and flagged. Fails if any number,
   name, or detail is invented.
7. **Human test.** The copy passes "would a person say this out loud": no
   textbook phrasing, no meta-commentary, no "I hope this helps", no
   "challenges and future outlook" section.
8. **Audit shape.** The output has the four sections in order: Flags,
   Rewrite, Change Summary, Second-Pass Audit. Review-only requests skip
   Rewrite and Change Summary.

## Test inputs

- "Clean this product description: 'Heritage Brand Hats delves into the rich
  tapestry of western culture, showcasing vibrant designs that serve as a
  testament to meticulous craftsmanship. Additionally, the brand fosters a
  community of hat enthusiasts who navigate the evolving landscape of western
  fashion. It's not just a hat - it's a statement of who you are. Despite the
  challenges of competing with mass-market brands, HBH continues to grow its
  loyal customer base through innovative approaches and robust quality
  standards.'"
  - Expected: Pass 5 produces placeholders, not invented figures, because the
    input gives no specs or counts.
- "Human-check this blog intro: 'In today's rapidly evolving digital
  landscape, businesses must leverage cutting-edge AI tools to enhance their
  online presence. Furthermore, understanding the intricate interplay between
  search engine optimization and artificial intelligence is crucial for
  maintaining a competitive edge. This comprehensive guide delves into the
  pivotal role that AI-powered answer engines play in shaping the future of
  digital marketing, underscoring the need for a robust strategy that
  encompasses both traditional and innovative approaches.'"
- "Flag without rewriting this email opener: 'We are thrilled to welcome you
  to our vibrant community of forward-thinking entrepreneurs! Your decision to
  join showcases your commitment to fostering growth and navigating the
  challenges of building a business. Moreover, our meticulously crafted
  resources will help you cultivate the skills needed to garner success in
  today's competitive landscape. We look forward to embarking on this journey
  with you.'"
  - Expected: review only. Flags and Second-Pass Audit, no rewrite.
