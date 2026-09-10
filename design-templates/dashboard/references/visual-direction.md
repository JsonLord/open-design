# Visual direction: modern dark financial dashboard

Use this as the preferred fallback when the current company dashboard does not define a stronger system. When a Power BI report, theme JSON, screenshot, or active `DESIGN.md` is supplied, preserve its identity and adapt this direction slightly to the company colors.

## Design character

- Modern, precise, restrained, and information-dense without feeling cramped.
- Black canvas with charcoal and grey translucent surfaces.
- Thin low-contrast borders, crisp type, tabular numerals, and generous plot area.
- Company colors used as controlled highlights, not as large branded backgrounds.
- Depth from surface opacity and spacing; blur and shadow are subtle and functional.

## Surface recipe

| Role | Preferred fallback | Guidance |
|---|---|---|
| Canvas | `#090b10` | Near-black, never pure black unless the company system requires it |
| Main panel | `rgba(18, 21, 28, .82)` | Add `backdrop-filter: blur(16px)` only when content or texture exists behind it |
| Raised/selected panel | `rgba(27, 31, 40, .94)` | Use for tooltips, active states, and focused detail |
| Divider | `rgba(255, 255, 255, .10)` | One-pixel rules; avoid outlining every small element |
| Primary text | `#f3f3ef` | Slightly warm white reduces glare |
| Secondary text | `#969aa5` | Keep readable; do not push metadata into near-invisible grey |
| Focus/company accent | active brand accent | Reserve for selection, primary series, totals, and decisive results |

Keep roughly 85–90% of the screen neutral. A company accent should occupy about 5–10% of the visible area; semantic positive/negative/warning colors use the remainder.

## Financial number semantics

Numbers carry meaning through sign, label, weight, and color together.

| Number role | Treatment |
|---|---|
| Addition / favorable delta | Explicit `+`, positive color, medium-bold weight; include comparison basis |
| Deduction / unfavorable delta | True minus sign `−`, negative color, medium-bold weight; include comparison basis |
| Neutral movement | Primary or muted text; do not force green/red |
| Subtotal | Thin top rule, tabular numerals, slightly stronger weight |
| Final result / total | Company accent or high-contrast neutral, largest relevant numeric size, strong top rule or distinct column—not a generic status green |
| Missing / unknown | Em dash plus explanation; never substitute `0` |

For metrics where “lower is better,” do not color a negative delta red automatically. Derive favorability from the metric meaning and reinforce it with words such as “improved” or “worsened.”

## Company-color adaptation

1. Extract the current company accent, secondary accent, and semantic colors from `DESIGN.md`, Power BI theme JSON, CSS, or screenshots.
2. Keep the dark neutral surface ladder unless the existing company report clearly uses another foundation.
3. Assign the company accent to the primary series, current selection, and final result number.
4. Use a secondary company color for comparison series only when it remains distinguishable from positive, warning, and negative states.
5. Preserve established company typography, logo clear space, radius, and icon style.
6. Check contrast on every translucent layer; opacity changes can invalidate otherwise accessible brand colors.

Do not tint every panel with the brand color. Do not create rainbow KPI cards. Do not use glass effects when they reduce chart contrast or table legibility.

## Chart finish

- Plot backgrounds remain transparent or use the same charcoal surface as the panel.
- Grid lines are sparse and lower contrast than axes and labels.
- Primary series uses the company accent; comparison uses a neutral dash or secondary accent.
- Annotated events use one separate highlight color, preferably warning/amber.
- Direct labels and end values should carry more contrast than historical ticks.
- Selection can brighten a mark and dim context slightly; do not animate every redraw.

## Recognizable continuity test

Before handoff, compare the new artifact with the current company dashboard side by side. A colleague should recognize the same company through color, type, component behavior, and numeric treatment, while also seeing a clearer hierarchy, stronger narrative, and more polished composition.
