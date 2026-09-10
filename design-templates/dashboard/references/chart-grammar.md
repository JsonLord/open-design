# Chart and interaction grammar

## Choose the visual by analytical task

| Task | Prefer | Avoid |
|---|---|---|
| Trend over ordered time | Line, area, or small multiples | Bars for long, dense series |
| Compare categories | Sorted horizontal bars, dot plot | Pie/donut with many slices |
| Progress to target | Bullet chart, variance bar | Speedometer gauge |
| Part-to-whole | Stacked bar, 100% stacked bar | Multiple unrelated donuts |
| Distribution | Histogram, box plot, strip plot | Average-only KPI |
| Relationship | Scatterplot with labelled outliers | Dual-axis line chart by default |
| Additive change | Waterfall | Unsorted positive/negative bars |
| Schedule or duration | Timeline, Gantt when dependencies matter | Decorative calendar grid |
| Dense exact lookup | Table with alignment and conditional cues | Tiny chart labels for every value |

## Required chart anatomy

Include what a reader needs to interpret the mark:

- title that states the measure and grain;
- unit in the title, axis, or value label;
- axes and ticks when position encodes a numeric value;
- a visible zero baseline for bars;
- consistent time direction and date grain;
- source and freshness for external or live data;
- legend only when direct labels would be less clear;
- accessible text summary for the key pattern.

Use quiet grid lines and no more ticks than the data can support. Do not smooth a line if smoothing could imply values that were never observed.

## Semantic token contract

Map the active design system to these roles. Add them as CSS custom properties so charts and UI share one language.

```css
:root {
  --dash-canvas: var(--surface-canvas, #090b10);
  --dash-panel: var(--surface-raised, rgba(18, 21, 28, .82));
  --dash-panel-strong: var(--surface-strong, rgba(27, 31, 40, .94));
  --dash-text: var(--text-primary, #f3f3ef);
  --dash-muted: var(--text-secondary, #969aa5);
  --dash-line: var(--border-subtle, rgba(255, 255, 255, .10));
  --dash-focus: var(--accent, #8da0ff);
  --dash-positive: var(--positive, #50d8ad);
  --dash-warning: var(--warning, #f2c66d);
  --dash-negative: var(--negative, #ff8a7c);
  --dash-series-2: var(--data-series-2, #bb9af7);
  --dash-series-3: var(--data-series-3, #55bdd0);
}
```

- Use `--dash-focus` for active selection and the primary series, not every border and icon.
- Keep status colors semantically stable across the screen.
- For more than three categorical series, derive a tested palette with sufficient contrast; never alternate arbitrary brand colors.
- Ensure shape, label, or position carries status as well as color.
- Treat the dark values above as preferred fallbacks, not permission to override an existing company system. Read `visual-direction.md` before mapping a brand.

## Numeric typography

- Use tabular numerals for KPIs, axes, and tables.
- Right-align numeric table columns and align decimals where practical.
- Keep precision consistent with the decision; false precision adds noise.
- Pair a delta with its basis: “+4.2% vs plan,” not simply “+4.2%.”
- Abbreviate only when space requires it, and keep the unit visible.
- Style additions/positive values with `--dash-positive` and an explicit `+`; style deductions/negative values with `--dash-negative` and a true minus sign `−`.
- Style totals and calculated results with the company focus color or high-contrast text plus a rule. Do not reuse positive green for a neutral total.

## Inline SVG rules

- Use a stable `viewBox` and let CSS size the SVG.
- Reserve plot margins for axes and annotation.
- Draw grid, reference bands, marks, labels, and focus targets in separate groups.
- Give interactive points a hit target of roughly 24 CSS pixels even if the visible mark is smaller.
- Add a text summary adjacent to the SVG; SVG accessibility varies by reader.
- Recompute paths and labels when filters change. Do not update the title while leaving old marks behind.

## Interaction patterns

Every interaction must answer a user question.

| Control | Required behavior |
|---|---|
| Period selector | Update linked KPIs, axes, marks, annotations, and summary text |
| Legend/series toggle | Change series visibility and preserve an accessible pressed state |
| Chart point | Reveal exact value, date, and relevant annotation by pointer and keyboard |
| Table row | Coordinate highlight/detail with the corresponding chart segment when possible |
| Filter | Show the active condition and provide reset/remove behavior |
| Export | Export or copy a real, clearly labelled result; show confirmation/failure |

Avoid dead icon buttons, fake search boxes, and controls that only change color. Prefer progressive disclosure: overview first, exact detail on intent.

## State coverage

Design these states before polishing the happy path:

- loading or refreshing;
- empty because no records match;
- disconnected or permission denied;
- partial coverage;
- stale data;
- error with recovery action;
- selected/filter-active state;
- keyboard focus and reduced motion.

Never display zero when the value is unknown. Use an em dash and explain the missingness.
