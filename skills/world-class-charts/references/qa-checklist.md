# Pre-ship QA checklist and rubric (static charts)

Adapted from the original world-class-charts checklist for static SVG. The
original's interaction, keyboard, responsive, motion, and dark-mode checks
apply only to live React builds; see the original repo for those.

## Checklist

**Choice and story**
- [ ] The chart answers one question, written as the subtitle takeaway.
- [ ] The chart type matches the question (`chart-choice.md`). One number
      is a stat, not a chart.
- [ ] Bars start at zero. Time runs left to right. Categories are sorted by
      value unless the order means something.
- [ ] One thing is highlighted. Everything else is quieter by the ghost rule.

**Numbers and labels**
- [ ] Every number follows `formatting.md`. Tabular figures. True minus sign.
- [ ] Axis ticks are nice, distinct, and use one decimal count.
- [ ] Dates show the year once, not on every tick.
- [ ] Series are labeled directly. A key only when labels cannot fit, above
      the plot, in the same order as the marks.
- [ ] Targets, forecasts, and annotations are labeled in words.
- [ ] A source line names where the numbers came from and the period.
- [ ] Every number matches the operator's data and any adjacent slide.
      Nothing estimated or invented.

**Edge cases**
- [ ] Missing values show as gaps or "No data", never as zero.
- [ ] One point, two points, and a previous value of zero render sensibly
      (zero to anything is "New").

**Access**
- [ ] `role="img"`, `<title>`, and a `<desc>` that sums up the chart.
- [ ] Text at least 4.5:1, marks at least 3:1 or directly labeled.
- [ ] Nothing relies on color alone.
- [ ] No text under 12px. No rotated text.
- [ ] A Markdown data table with the same numbers ships alongside.

**Craft**
- [ ] Colors come from the roles in `svg-and-brand.md`. No stray hex.
- [ ] 40px margins. Nothing clipped. Labels do not collide.
- [ ] The SVG renders standalone with no script or external image.

## Rubric (0 to 10)

Score each line 0, 0.5, or 1. Be honest: 1 means a design lead at the FT or
Stripe would not comment on it.

| # | Dimension | 1 point when |
|---|---|---|
| 1 | Right chart | The best type for its question. |
| 2 | Clear story | Takeaway subtitle, one highlight, nothing extra. |
| 3 | Numbers | Consistent formatting, exact where it matters, clean axes. |
| 4 | Labels | Direct labels, annotations, and reference lines in words. |
| 5 | Edge cases | Missing, sparse, and zero values handled honestly. |
| 6 | Truth | Zero baselines for bars, no dual axes, no truncation without saying so. |
| 7 | Accessibility | Contrast, no color-only meaning, title, desc, and data table. |
| 8 | Fit | Reads at slide size from the back of the room, and at doc size. |
| 9 | Brand | Color roles only; on-brand type and spacing. |
| 10 | Craft | Spacing, alignment, and type feel finished. |

- 9 to 10: ship it.
- 7 to 8: ship after fixing the lowest line.
- Under 7: do not ship.
