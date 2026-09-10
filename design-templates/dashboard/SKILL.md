---
name: dashboard
en_name: Decision Dashboard
description: |
  Create high-fidelity analytical dashboards, BI reports, scorecards, and monitoring views that turn evidence into a clear decision story. Use for executive performance, operational command centers, narrative timelines, diagnostics, explorers, and geographic analysis. Do not use for a CRUD admin shell with no analytical question.
triggers:
  - dashboard
  - analytics dashboard
  - BI report
  - business intelligence
  - executive scorecard
  - KPI dashboard
  - monitoring dashboard
  - data story
  - Power BI style dashboard
od:
  mode: prototype
  surface: web
  scenario: analytics
  category: dashboards
  preview:
    type: html
  example_prompt: "Create an executive dashboard that explains what changed, why it changed, and what needs attention."
  design_system:
    requires: true
  craft:
    requires:
      - state-coverage
      - accessibility-baseline
      - laws-of-ux
      - typography
      - color
      - anti-ai-slop
  critique:
    policy: opt-in
---

# Decision dashboard

Build a dashboard around a decision, not around a collection of charts. The result must make the most important change obvious, explain likely drivers, and expose supporting detail without forcing the reader to decode the interface.

## Workflow

1. **Establish the evidence contract.** Treat supplied files, connector results, and user-provided facts as authoritative. Never invent real-world values or imply that illustrative data is live. If no data is available, create a coherent demo dataset and keep an `Illustrative demo data` label visible in the interface.
2. **Inspect the current design before taking inspiration.** Look for supplied `.pbix`, `.pbip`, `.pbir`, theme JSON, PDF exports, screenshots, or existing dashboard code. Read `references/visual-direction.md` and `references/adaptation.md`. Preserve the company's recognizable color, typography, number semantics, density, and component language; improve hierarchy and composition without erasing identity. If the report cannot be inspected, ask for screenshots or a PDF export rather than guessing its design.
3. **Write the decision sentence.** Complete: “This dashboard helps `[audience]` decide `[decision]` by showing `[signals]` over `[time/grain]`.” Let this sentence control hierarchy and chart selection.
4. **Choose one archetype.** Read `references/archetypes.md` and select the closest analytical shape. Do not default to a permanent sidebar, four KPI cards, and a line chart unless that shape fits the decision.
5. **Start from the seed.** Copy `.od-skills/dashboard/assets/template.html` to `index.html` in the project workspace. Inspect `.od-skills/dashboard/example.html` for the visual quality bar, but adapt its composition instead of copying its content.
6. **Apply the active design system.** Map brand tokens to the semantic dashboard roles in `references/chart-grammar.md`. When company colors exist, keep most surfaces black/charcoal/grey and use those colors selectively for focus, totals, and key result numbers. Preserve positive and negative meaning even when the brand palette differs.
7. **Compose the story.** Use this reading order: context and freshness → headline signal → primary visual → explanation/drivers → supporting detail. Give the primary visual the most space. Use whitespace, alignment, annotation, and typography before adding containers.
8. **Choose and draw charts deliberately.** Read `references/chart-grammar.md`. Include axes, units, baselines, legends, labels, and source/freshness information when they are required to interpret the data. Prefer direct labels and annotated events to ornamental legends.
9. **Implement meaningful interaction.** Every visible control must change the view, reveal detail, navigate, or export something useful. Filters must update linked numbers and charts together. Support keyboard use, focus states, empty/loading/error states, and reduced motion.
10. **Adapt references responsibly.** When working from Power BI, Figma, screenshots, or another dashboard, read `references/adaptation.md`. Reuse information architecture and layout principles; do not copy unlicensed graphics, logos, proprietary data, or a source dashboard pixel-for-pixel.
11. **Verify and write.** Complete `references/checklist.md`, then save the finished artifact as `index.html`. Do not emit the full file inside an `<artifact>` block.

## Non-negotiable principles

- **One dominant question per screen.** Secondary modules support it.
- **Evidence before decoration.** No invented facts, fake live status, or decorative charts.
- **Comparison creates meaning.** Pair important values with a target, prior period, forecast, benchmark, or distribution.
- **Explain change.** Annotate inflection points and pair outcomes with likely drivers.
- **Reduce chart furniture.** Quiet grids, sparse ticks, direct labels, and restrained color.
- **Color has a job.** Reserve semantic colors for status and a single focus color for selection or emphasis.
- **Tables are for lookup.** Use them for exact values and dense detail, not as a substitute for hierarchy.
- **Responsive means reprioritized.** On narrow screens, stack the decision story and move detailed lookup content later; do not merely shrink a desktop canvas.

## Resource map

- `assets/template.html` — accessible, self-contained implementation seed.
- `example.html` — polished narrative/executive dashboard example using labelled demo data.
- `references/archetypes.md` — decision-led dashboard structures.
- `references/chart-grammar.md` — chart choice, visual encoding, tokens, and interaction rules.
- `references/visual-direction.md` — preferred dark translucent surface system and number styling.
- `references/adaptation.md` — process and licensing guidance for adapting references.
- `references/checklist.md` — final quality gate.
- `INSTALL.md` — scoped import and upgrade instructions for AI agents.

## Output contract

Write a self-contained `index.html` unless the user explicitly requests another structure. Inline CSS and small vanilla JavaScript are preferred for portability. Use inline SVG for precise charts; use a chart library only when the environment already provides it or the user explicitly approves the dependency.
