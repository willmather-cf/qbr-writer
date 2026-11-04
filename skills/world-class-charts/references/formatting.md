# Number and date formatting

Adapted from the original world-class-charts formatting guide for static
charts. The same number must read the same way in the subtitle, the axis,
the labels, and the data table.

## Numbers

| Rule | Example |
|---|---|
| Group thousands | 12,840 |
| Go compact at 10,000 and up on axes and labels | 48.2K, 1.3M |
| Exact values in the data table | $48,210 |
| Money under $100 keeps cents only if not whole | $4.50, $12 |
| Percent from a ratio, one decimal unless whole | 14.2%, 40% |
| Real minus sign (U+2212), not a hyphen | −18% |
| Plus sign on rises | +12% |
| A change that rounds to zero gets no sign | 0% |
| Rate changes are points, not percent | +0.4 pts |
| Change from zero is "New", not infinity | New |
| Missing is never 0 | "No data" in the table, a gap in the line |
| Tabular figures on every number | `font-variant-numeric: tabular-nums` |

## Axes

- One decimal count per axis. Pick the fewest decimals that show every tick
  step exactly, so 2,500 steps read $2.5K, $5K, $7.5K and never round to
  "$3K".
- Zero is "0", never "$0K".
- Nice ticks: 1, 2, 2.5, or 5 times a power of ten.
- 3 to 5 gridlines. Fewer on short charts.
- Put the unit in the tick ("$10K", "40%") or in the subtitle, not on a
  rotated axis title.

## Dates

| Grain | Axis | Data table |
|---|---|---|
| day | Oct 31 | Sat, Oct 31, 2026 |
| week | Oct 26 | Week of Oct 26, 2026 |
| month | Jan, Feb (year on first tick and at each new year) | January 2026 |
| quarter | Q1 | Q1 2026 |
| fiscal quarter | FY26 Q1 | FY26 Q1 |
| year | 2026 | 2026 |

- Show the year once, under the first tick and wherever the year changes.
  Never on every tick.
- Ranges use "to": "Oct 1 to 31, 2026", "Jan to Mar". No en dashes, to match
  house copy rules.
- Never use numeric dates like 10/11/12. They read differently around the
  world.

## Words

- Units in words for small counts: "3 orders", not "3".
- Sentences, not labels, for status: "Over the limit by $600."
- Plain English. Write "vs last quarter" in labels; "Q/Q" is fine in a QBR
  where the reviewer's template already uses it.
