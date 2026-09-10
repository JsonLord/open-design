# Dashboard archetypes

Choose the archetype from the decision and the audience. An archetype is a hierarchy, not a visual theme. Blend at most two; if every module has equal weight, the dashboard has no point of view.

## Selection table

| Question | Best starting archetype | Dominant visual | Supporting modules |
|---|---|---|---|
| Are we on plan, and where should leadership intervene? | Executive performance | Variance-to-plan or trend with target | 3–5 headline measures, drivers, exceptions |
| What needs attention right now? | Operational command center | Status queue, current load, or SLA trend | Freshness, alerts, ownership, drill-down |
| What changed, when, and around which events? | Narrative timeline | Annotated time series | Event rail, before/after measures, related drivers |
| Why did the outcome move? | Diagnostic / root cause | Contribution, decomposition, or segmented comparison | Cohorts, correlations, exception table |
| Let an analyst investigate freely | Explorer | Filterable overview with coordinated detail | Search, facets, table, saved view/export |
| Where is the pattern occurring? | Geographic | Map paired with ranked comparison | Region summary, legend, exceptions, detail |

## 1. Executive performance

Use for leaders who need the answer in under a minute.

Suggested order:

1. Title, period, scope, and freshness.
2. A clear status sentence such as “Revenue is ahead of plan; retention is the constraint.”
3. Three to five headline measures, each with a comparison.
4. One dominant trend or variance visual.
5. Driver ranking and a short exception list.
6. Exact details or methodology last.

Avoid a wall of equally weighted KPI cards. Use one hero measure or statement when one signal clearly dominates.

## 2. Operational command center

Use for time-sensitive triage and recurring monitoring.

- Put freshness, coverage, and current state near the title.
- Separate “needs action” from “healthy”; do not make users scan everything.
- Show owner and next action for exceptions.
- Prefer queues, threshold bands, sparklines, and small multiples over decorative summaries.
- Make loading, disconnected, stale, empty, and partial-data states explicit.

A left rail is appropriate only when operators switch between several persistent work areas. It is not a mandatory dashboard ingredient.

## 3. Narrative timeline

Use when milestones, releases, policy changes, incidents, or campaigns explain movement.

- Give the time series most of the canvas.
- Annotate a few consequential events directly on the plot.
- Link event selection to nearby explanation and related values.
- Use a compact event rail for chronology; keep minor events visually quiet.
- Provide an unambiguous period control and consistent date grain.

This is the closest pattern to the Microsoft Stock inspiration: an annotated history with supporting context, not merely a stock-themed skin.

## 4. Diagnostic / root cause

Use when the audience already knows the outcome and needs the cause.

- Start with the outcome and its variance.
- Rank contributions by magnitude.
- Use a waterfall for additive change, small multiples for segment patterns, or scatterplots for relationships.
- Surface counterexamples and confidence/coverage limits.
- End with the smallest useful detail table for verification.

Do not imply causality from correlation. Label inferred drivers as hypotheses unless the evidence supports a causal claim.

## 5. Explorer

Use for analysts and repeated investigation.

- Keep global filters compact and visible.
- Show active filters as removable chips.
- Coordinate selection across charts and detail rows.
- Preserve a sensible default view so the first screen still tells a story.
- Support reset, keyboard navigation, and export if those controls are shown.

An explorer may be dense, but density must come from useful information rather than smaller type and tighter padding.

## 6. Geographic

Use only when location is analytically meaningful.

- Pair the map with a sorted bar chart or table; geography is poor for precise comparison.
- Use a perceptually ordered scale and state what missing regions mean.
- Keep legends close to the map and include units.
- Provide a non-map path to the same information for accessibility.
- Avoid maps when a ranked list answers the question faster.

## Responsive transformation

Desktop composition should not dictate mobile order. Preserve this sequence on narrow screens:

1. decision headline and freshness;
2. headline measures;
3. primary visual;
4. explanation and exceptions;
5. filters and detailed lookup.

Convert dense horizontal legends to direct labels or short vertical lists. Let tables scroll within labelled regions; never make the whole page depend on horizontal scrolling.
