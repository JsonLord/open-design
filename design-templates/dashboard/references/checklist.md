# Dashboard quality gate

Complete every P0 item before handoff. P1 items are expected unless the brief makes them irrelevant.

## P0 — correctness and trust

- [ ] The audience, decision, scope, grain, and time period are clear.
- [ ] Every displayed value comes from supplied evidence or is visibly labelled illustrative demo data.
- [ ] No fake live/connected state, invented citation, or unsupported causal claim appears.
- [ ] Linked filters update all affected KPIs, charts, annotations, summaries, and details.
- [ ] Units, comparison bases, signs, precision, and date grain are consistent.
- [ ] Bars use an honest baseline; axes and legends do not distort the comparison.
- [ ] Loading, empty, stale/partial, disconnected, and error states have an intentional treatment.
- [ ] The artifact is written to `index.html` and opens without external build steps.

## P1 — decision clarity

- [ ] The most important signal is identifiable in five seconds.
- [ ] One primary visual has clearly more visual weight than secondary modules.
- [ ] Important measures include a target, prior period, forecast, benchmark, or distribution.
- [ ] The dashboard explains likely drivers or relevant events, not only outcomes.
- [ ] The selected archetype matches the decision; navigation is present only when useful.
- [ ] Supplied Power BI/current dashboard designs were inspected first, or the missing visual reference was explicitly requested.
- [ ] The primary chart includes the labels, units, ticks, baseline, and annotations required to read it.
- [ ] Tables are reserved for exact lookup and exceptions.
- [ ] Copy uses concrete measure names and actions instead of generic labels such as “Overview” or “Data.”

## P1 — visual and interaction quality

- [ ] Active design-system tokens are mapped to semantic dashboard and chart roles.
- [ ] Black/charcoal translucent surfaces remain dominant; company colors appear selectively in focus, total, and key result roles.
- [ ] Positive additions, negative deductions, subtotals, and final results are visually distinct without relying on color alone.
- [ ] Status is not encoded by color alone, and text/marks meet contrast expectations.
- [ ] Color is restrained: one focus color, stable semantic colors, quiet chart furniture.
- [ ] Numeric typography uses tabular figures and consistent alignment.
- [ ] Every visible control works and has hover, active/pressed, keyboard-focus, and disabled behavior where relevant.
- [ ] Chart points or rows expose exact values by keyboard as well as pointer.
- [ ] Motion is purposeful and respects `prefers-reduced-motion`.
- [ ] The page has no accidental horizontal scroll at 1440, 1024, 768, and 375 CSS pixels.
- [ ] Mobile order preserves the decision story rather than shrinking the desktop layout.

## P2 — finish

- [ ] Source/freshness and active filters are visible where appropriate.
- [ ] The title and browser metadata describe the artifact.
- [ ] Export/copy controls produce a real result and confirm success or failure.
- [ ] Inline comments record material references and any required attribution.
- [ ] Decorative shadows, gradients, pills, icons, and borders have been removed unless they clarify structure or state.
- [ ] The result does not resemble a generic admin template or a pixel copy of the inspiration.
