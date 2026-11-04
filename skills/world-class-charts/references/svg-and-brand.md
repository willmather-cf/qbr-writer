# SVG canvas, brand, and access

How to draw a world-class chart as one static, self-contained SVG that drops
into a slide, a doc, or an email, on Cloudflare brand.

## Canvas

| Use | viewBox |
|---|---|
| Slide (default) | `0 0 1200 675` (16:9) |
| Doc or email | `0 0 800 450` |
| Half-slide or KPI strip | `0 0 600 338` |

- At least 40px margin on every side. Title block at the top left.
- Layout from top to bottom: title (the measure), subtitle (the takeaway),
  the plot, then a source line at the bottom left.
- Fonts: `font-family="'Kunst Grotesk', Inter, -apple-system,
  BlinkMacSystemFont, 'Segoe UI', sans-serif"`. Inter may be imported from
  Google Fonts inside `<defs><style>`; that is the only allowed external
  reference.
- Sizes: title 28px medium, subtitle 18px regular, labels and ticks 14px,
  source line 12px. Nothing under 12px.
- `font-variant-numeric: tabular-nums` on every number.
- No `<script>`, no `on*` handlers, no external images.

## Color roles

Map every color to a role, using `brand/design-system.md`. Never pick hex
values by eye.

| Role | Token | Hex | Use |
|---|---|---|---|
| Highlight | `--color-cf-orange` | `#FF6633` | The one mark that matters |
| Text | `--color-cf-text` | `#521000` | Title, labels, values |
| Muted text | warm brown at 70% | `#521000` at 0.7 opacity on text only | Subtitle, ticks, source line |
| Background | white or `--color-cf-bg-page` | `#FFFFFF` or `#F5F1EB` | Canvas |
| Gridlines and axes | `--color-cf-border` | `#EBD5C1` | Hairlines, 1px |
| Context marks | soft brown tint | `#521000` at 0.18 fill with a 1px `#521000` edge at 0.5 | Everything that is not the highlight |
| Categorical | `--color-cf-accent-blue`, `-purple`, `-green` | from the design system | Only when parts must be told apart |
| Status | `kumo-success`, `kumo-danger`, `kumo-warning` | from the design system | Above or below target |

Rules:
- Five colors at most. Group the rest as "Other (n)" in the context color.
- Ghost rule: context marks keep a visible edge and a soft fill. Never just
  lower opacity on the whole mark.
- Orange is an accent. Never fill the background with it.
- Brand orange on white is just under 3:1, so an orange highlight always
  carries a direct label, and its meaning never rests on color alone.

## Access in a static file

- The root `<svg>` has `role="img"` and `aria-labelledby` pointing at a
  `<title>` (the chart title) and a `<desc>` (one sentence that sums up the
  chart and names its top item, for example "Campaign A drove most of the
  spend; click-through fell on last quarter").
- Text contrast at least 4.5:1 on its background. Marks at least 3:1, or
  paired with a label.
- Nothing by color alone: use signs (+ and −), arrows, dashes for targets
  and forecasts, and words.
- Every chart ships with a data table in Markdown alongside the SVG, with
  the same numbers, so anyone who cannot read the image still gets them.

## Mark details

- Bars: 2px corner radius at most, gaps at least 30% of bar width.
- Lines: 2.5px for the highlight, 1.5px for compare lines. Straight
  segments or monotone curves that never overshoot the data.
- Targets and goals: thin dashed line (`stroke-dasharray="4 4"`), labeled
  at its left end with the word and the value ("Goal $5 CPQV").
- Forecasts: dashed line inside a shaded range, labeled once ("Forecast").
- Annotations: one or two, a few words each, above the mark with a short
  leader line. Never cover data.
