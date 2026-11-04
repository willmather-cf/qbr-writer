# Mapping the deck to Cloudflare slides

How each slide module becomes a layout in a `.slides.json` file, the field
rules, how charts and copy from the other skills land, and the checks to run
before saving. The layouts and field names follow the library `slides` skill;
if that skill changes, it wins.

## File shape

```json
{
  "type": "slides",
  "slides": [ { "layout": "cover", "title": "...", "subtitle": "..." } ]
}
```

Every slide has `layout` and `title`. Most accept `section` (an uppercase
label) and `pageNumber`.

## Module to layout

| Module | Layout | Fields |
|--------|--------|--------|
| Cover | `cover` | `title` = the final message or deck name; `subtitle` = audience and date, for example "<Program> \| <FYxxQx> QBR" |
| Numbered section divider | `section` | `title` = "1. <Section name>"; `subtitle` = the one-line scope statement |
| Executive summary | `twoColumn` or `content` | `title` = the recommendation as an assertion; `items` = three to five findings |
| Message, evidence, source | `content` | `section` = category label; `title` = assertion; `subtitle` = qbr-slide-writer subhead; `items` = up to five, each `title` + `description` |
| Big stat | `statCallout` | `statValue`, `statLabel`, `subtitle` = the one sentence, `source` |
| Two or three headline numbers | `stats` | `metrics` = `[{ "value", "label" }]` |
| Visible gap | `comparison` | `before.heading` + `before.items`, `after.heading` + `after.items` |
| Options compared | `comparison` or `twoColumn` | same criteria on both sides |
| Three-beat mechanism, or a plan | `timeline` | exactly three `phases`, each `label`, `title`, `items` |
| Value table | `content` | one item per capability: `title` = capability, `description` = "How: ... Value: ..." |
| Case study, slide two | `useCase` | `benefits`, optional `proof` |
| Asks and next steps | `actionPlan` | `actions` = `[{ "action", "owner", "timeline", "status" }]`; unknown owner is "[needs input]" |
| Running thesis run | `content` | identical `title` on every slide in the run; constant `section`; one component per slide |

Icons are optional on `content` and `productGrid` items and must come from
`mappings/icon-catalog.json`. Leave them off unless they carry meaning.

## Where the layered copy goes

From a `qbr-slide-writer` block:

| Block field | Slide field |
|-------------|-------------|
| Event label + Headline | `title` (the label stays in the headline, for example "Test: <claim>") |
| Subhead | `subtitle` |
| Visual | decides the layout or the chart to request |
| Recommendation | last item, titled "Recommendation", or a row in the closing `actionPlan` |
| Footnotes | `source` where the layout has one; otherwise the last item, titled "Source" |
| Flags | the notes file, never the slide |

## Where the charts go

`world-class-charts` returns a self-contained SVG at 1200x675 plus a data
table. The slides layouts above have no documented image field, so:

1. Give a chart that carries the slide its own `content` slide with the
   chart's takeaway as the `title`, the subhead as `subtitle`, and the chart's
   source as the last item. Leave room by keeping items to two or fewer.
2. Where the point is one or two numbers, use `statCallout` or `stats`
   instead and keep the SVG for the appendix or the doc version.
3. List every SVG in the notes file with its slide number. After export to
   PPTX or Google Slides, insert each SVG on its slide.

If the slides viewer gains an image layout, place the SVG directly and drop
step 3.

## Cloudflare numbers

Any Cloudflare metric on a slide is copied from `facts/company.json` or
`facts/network.json`, with the file named in the source line. The library
templates `slide-templates/cf-at-a-glance.json` and
`slide-templates/cf-network-global.json` can be loaded verbatim when a deck
needs a Cloudflare overview; most internal decks do not.

## Validation checks

Run all of these before saving:

- The first slide is `cover`.
- Every slide that accepts `section` has an uppercase label.
- `pageNumber` is sequential and skips `cover` and `section` slides.
- Every `metrics` entry has both `value` and `label`.
- Every `timeline` has exactly three `phases`.
- `productGrid` items use `title`, not `name`.
- No slide has more than five items.
- No more than three slides in a row share a layout, unless they are a
  running thesis run.
- Every slide with a number has a source.
- Every chart in the notes file maps to a real slide number.
- The file parses as JSON.
