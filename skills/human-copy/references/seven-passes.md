# The Seven Passes

The full rule set for `human-copy`. Run every pass on the content and fix
every violation. No "this one's fine" exceptions, except where a tier rule
below says a single use is allowed.

## Pass 1: Vocabulary purge (3-tier sensitivity)

Tiered flagging reduces over-correction. Tier 1 fires always. Tier 2 fires
only when 2+ words cluster in the same paragraph. Tier 3 fires only at high
density (3+ per 100 words). Also screen against the house stop list in
`voice/banned-vocabulary.md`; any match there is treated as Tier 1.

### Tier 1: always flag and replace

| AI word | Replace with |
|---------|-------------|
| delve/delving | dig into, look at, examine |
| tapestry (figurative) | DELETE - say what you mean |
| vibrant | DELETE or use a specific descriptor |
| crucial/pivotal/vital | important, or DELETE if the sentence works without it |
| foster/fostering | build, create, grow, start |
| landscape (figurative) | scene, market, space, world |
| meticulous/meticulously | careful, precise, obsessive |
| underscore (verb) | show, prove, reveal, make clear |
| showcase/showcasing | show, display, demonstrate |
| testament (figurative) | proof, evidence, sign |
| intricate/intricacies | complex, detailed, layered |
| garner | get, earn, win, attract |
| groundbreaking | new, first |
| renowned | famous, well-known, respected |
| leverage (verb) | use |
| utilize | use |
| boasts | has |
| nestled | DELETE - travel brochure language |
| Additionally (starting a sentence) | Also, And, Plus, or just start the next sentence |
| Furthermore | DELETE - just continue |
| Moreover | DELETE - just continue |
| Notably | DELETE |
| In conclusion / In summary / Overall | DELETE - just end |
| It is worth noting | DELETE |

### Tier 2: flag when 2+ cluster in the same paragraph

| AI word | Replace with |
|---------|-------------|
| bolstered | strengthened, backed, supported |
| enhance/enhancing | improve, sharpen, strengthen |
| enduring | lasting, permanent, long-running |
| interplay | relationship, connection, tension |
| align with | match, fit, support |
| encompassing | covering, including |
| navigate (figurative) | handle, deal with, manage |
| facilitate | help, enable, make possible |
| comprehensive | thorough, complete, full |
| robust | strong, solid, reliable |
| innovative | new, original, clever |
| resonate/resonating | connect, hit home, land |
| embody/embodying | represent, show, be |
| cultivate/cultivating | build, grow, develop |
| seamless/seamlessly | smooth, clean, or DELETE |
| streamline/streamlined | simplify, speed up |
| empower/empowering | enable, help, give |
| holistic | whole, full, or name the parts |
| strategic | planned, deliberate, or DELETE |
| dynamic (adj) | specific descriptor or DELETE |
| transformative | big, major, or DELETE |
| revolutionary | new, first, or DELETE |
| paradigm shift | big change |
| synergy/synergize | fit, work together |
| holistic approach | full picture |
| endeavor (noun) | effort, project, try |
| commence | start |
| ascertain | find out, check |
| myriad | many, or a specific number |
| plethora | many, or a specific number |
| quintessential | classic, typical |
| multifaceted | layered, many-sided |
| paramount | most important, top |
| imperative | must, critical |
| unwavering | steady, firm, constant |
| invaluable | very useful, rare |
| arguably | DELETE - pick a side |
| aforementioned | this, that (already named) |

Note: some Tier 2 words (robust, seamless, holistic, transformative,
revolutionary, synergy) are on the house stop list, so they fire as Tier 1.

### Tier 3: flag only at 3+ instances per 100 words

| AI word | Replace with |
|---------|-------------|
| important | specific reason, or DELETE |
| significant | specific magnitude, or DELETE |
| various | list them, or DELETE |
| many | specific number, or DELETE |
| often | specific frequency, or DELETE |
| typically | specific case, or DELETE |
| generally | specific case, or DELETE |
| particularly | DELETE or specific |
| especially | DELETE or specific |
| essentially | DELETE |
| ultimately | DELETE |
| fundamentally | DELETE |
| effectively | DELETE |
| potentially | DELETE |
| increasingly | specific trend, or DELETE |
| thereby | so, which |
| whereas | but, while |
| hence | so |
| thus | so |
| indeed | DELETE |
| nonetheless | but, still |
| consequently | so |
| accordingly | so |
| evidently | DELETE |
| certainly | DELETE |
| undoubtedly | DELETE |
| inherently | DELETE |
| profoundly | specific magnitude |
| considerably | specific magnitude |
| substantially | specific magnitude |
| relatively | DELETE |
| virtually | almost |

### Context-dependent: check each use

| Word | OK when | Kill when |
|------|---------|-----------|
| serves as | Technical description | Replacing "is" for no reason |
| stands as | Physical standing | Figurative ("stands as a symbol") |
| reflects | Literal reflection | "reflects broader trends" |
| highlights | You're literally highlighting | "highlights the importance of" |
| represents | Data or statistics | "represents a shift in" |
| commitment to | Contractual or legal | "commitment to excellence" |
| in the heart of | Geographic accuracy | Figurative ("in the heart of the community") |
| boasts, nestled | Never | Always |

## Pass 2: Structural pattern removal

**Kill the rule of three.** AI defaults to "X, Y, and Z" triads. If you see
three adjectives, three examples, or three parallel phrases, break the
pattern. Use two. Or four. Or one strong one. A genuine list of three
distinct, parallel facts is fine.

Before: "Heritage, craftsmanship, and authenticity define the brand."
After: "Craftsmanship defines the brand."

**Kill negative parallelisms.** "Not just X, but also Y" and "It's not about
X - it's about Y" are AI signatures. A clean A/B contrast that states two
positive claims ("Deploy code, not clusters.") is a house pattern and stays.

Before: "It's not just a hat - it's a statement of who you are."
After: "It's a hat that says something."

**Kill "despite" conclusions.** "Despite [challenges], [subject] continues to
[positive outcome]" is the most common AI article ending.

Before: "Despite the challenges of competing with mass-market brands, the
brand continues to grow its loyal customer base."
After: DELETE the whole paragraph. End on something specific.

**Kill superficial analysis phrases.** Present participle phrases that add
fake depth:

- "...highlighting the importance of..."
- "...underscoring the need for..."
- "...emphasizing the role of..."
- "...reflecting broader trends in..."
- "...contributing to the ongoing..."
- "...symbolizing the enduring..."
- "...marking a significant shift..."
- "...setting the stage for..."
- "...shaping the future of..."

DELETE all of these. If the point matters, make it a sentence. If it doesn't,
cut it.

**Kill legacy and significance inflation:**

- "pivotal moment in the history of"
- "indelible mark on"
- "deeply rooted in"
- "rich cultural heritage"
- "enduring legacy"
- "plays a vital role in"
- "key turning point"
- "evolving landscape"
- "focal point of"

## Pass 3: Copula restoration

AI avoids simple "is/are/has" constructions. Reverse this.

| AI construction | Human construction |
|----------------|-------------------|
| serves as | is |
| stands as | is |
| functions as | is |
| represents | is |
| marks | is |
| features | has |
| offers | has, gives |
| boasts | has |
| holds the distinction of being | is |
| remains | is (usually) |

Before: "The snapback serves as a bridge between western heritage and modern
street style."
After: "The snapback is western heritage made for the street."

## Pass 4: Sentence rhythm check

AI writes in uniform medium-length sentences. Human writing has rhythm.

- **Monotonous length.** If 5+ consecutive sentences are similar length (15
  to 25 words each), break the pattern. Add a 3-word sentence. Or a 40-word
  one.
- **Missing fragments.** Real writing uses fragments for emphasis. "Built
  different." "No shortcuts." AI almost never generates them.
- **Missing one-sentence paragraphs.** Sometimes one line is the paragraph.
- **Every sentence starts subject-verb.** Mix it up. Start with a time
  reference, a prepositional phrase, an action.

Match the register. Fragments suit marketing, social, and narrative copy.
Use them sparingly in reference docs, executive readouts, and legal text.

Before: "The hat is made from genuine suede. The brim develops a natural
patina over time. The construction uses heavyweight materials."
After: "Genuine suede. That's the brim. Over time it develops a patina and
gets softer, richer, more yours. The kind of hat that doesn't wear out. It
wears in."

## Pass 5: Specificity injection

AI generalizes. Humans specify. Every claim should pass the "like what?"
test. If a reader would ask "like what?" after your sentence, it fails.

Numbers beat adjectives. "Premium" means nothing. "1.2mm genuine split
suede" means something. "Growing" means nothing. "400 repeat buyers" means
something.

**Never invent the specific.** Use only numbers, names, and details that are
in the source text, that the operator supplied, or that come from an approved
fact file. For Cloudflare metrics, read `facts/company.json` and
`facts/network.json`. If the real figure is not available, replace the vague
claim with a visible placeholder, such as `[NEEDS SPECIFIC: repeat buyer
count]`, and list it as a flag. A made-up number is worse than a vague one.

Before: "The brand uses premium materials in all its products."
After (operator supplied the spec): "The suede on every brim is 1.2mm genuine
split, thick enough to hold shape and thin enough to curve how you want it."
After (no spec supplied): "The suede on every brim is [NEEDS SPECIFIC:
material and thickness]."

## Pass 6: Em dash and formatting purge

- **Em dashes and en dashes.** Remove every one. Prefer a period, comma,
  colon, or a restructured sentence. A spaced hyphen is the last resort, not
  the default swap. This is the single highest-signal tell.
- **Ranges.** Write "15 to 25", not "15-25" with a dash character.
- **Curly quotes.** Replace curly quotation marks and apostrophes with
  straight ones.
- **Excessive boldface.** Remove bold from body copy unless it defines a term
  for the first time.
- **Title case in headings.** Use sentence case: "How suede ages", not "How
  Suede Ages", unless the operator's template uses title case.
- **Markdown artifacts.** In copy headed for a page, email, or ad, remove any
  leaked `**bold**`, `*italic*`, `###`, or backticks.

## Pass 7: The human test

Read the final copy and check:

1. **Would a person say this out loud?** If you stumble or it sounds like a
   textbook, rewrite.
2. **Does every paragraph earn its place?** If you can delete it and nothing
   is lost, delete it.
3. **Is there an original observation?** Something specific, unexpected, or
   opinionated: a detail from the work, a customer quote, a number nobody else
   publishes. If every sentence could appear in a generic article on the same
   topic, it fails. If the source has nothing original, flag it rather than
   invent one.
4. **Does it have an opinion?** AI hedges: "Some prefer X, while others
   prefer Y." Humans pick a side.
5. **Any chatbot artifacts?** "I hope this helps", meta-commentary about the
   piece, disclaimers about limitations, sign-off language.
6. **Is there a "challenges and future outlook" section?** Delete it. Write a
   specific ending about what's next, or just end.

## Quick reference card

Search for these phrases. If found, rewrite:

```
"serves as a"
"stands as a"
"testament to"
"rich tapestry"
"vibrant community"
"plays a crucial role"
"in the heart of"
"it's important to note"
"despite these challenges"
"not just X, but also Y"
"highlighting the importance"
"underscoring the need"
"reflecting broader trends"
"commitment to excellence"
"In summary"
"In conclusion"
"Overall"
"Additionally,"  (starting a sentence)
"Furthermore,"
"Moreover,"
"Notably,"
"It is worth noting"
"In today's rapidly evolving"
```

## Pattern categories (for the Flags table)

Vocabulary (Tier 1, 2, or 3), Copula avoidance, Rule of three, Negative
parallelism, Despite-conclusion, Superficial analysis phrase, Significance
inflation, Rhythm uniformity, Missing fragments, Em dash, Formatting
artifact, Chatbot opener, Generic conclusion, Missing specific.

Severity: High (must fix), Medium (fix if easy), Low (judgment call).

## Grading (diagnostic scale)

- **A:** caught real AI patterns; the copy reads human after fixes.
- **B:** caught some patterns, missed others, or over-corrected so the copy
  reads stilted.
- **C:** missed obvious tells, or the copy still reads as AI after the pass.

## Sources

- Wikipedia, "Signs of AI writing" (community maintained).
- Kobak et al. (2024), "Delving into LLM-assisted writing in biomedical
  publications through excess vocabulary".
- Juzek and Ward (2025), "Why Does ChatGPT Delve So Much?"
- Reinhart et al. (2025), "Do LLMs write like humans?"
- Russell, Karpinska and Iyyer (2025), "People who frequently use ChatGPT for
  writing tasks are accurate detectors of AI-generated text".
- Will Mather's writing rules: no em dashes, short declarative sentences.

Original rule set: github.com/willmather95/human-copy (MIT).
