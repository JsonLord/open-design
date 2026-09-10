# Adapting dashboard references

Use references to learn composition and analytical storytelling. The goal is a new dashboard that fits the user's evidence, brand, and decision—not a pixel copy.

## Reference set used for this skill

| Reference | What to study | Reuse policy |
|---|---|---|
| [Microsoft Stock dashboard](https://github.com/luisosorio3214/Power-BI-Dashboards/tree/main/Microsoft%20Stock) | Annotated price history, event-led narrative, disciplined dark composition, overview-to-detail flow | Inspiration only. The repository did not expose a root license when this skill was authored; do not redistribute its PBIX, imagery, logos, text, or data unless rights are confirmed. |
| [Power BI Design Files](https://github.com/Dashboard-Design/Power-BI-Design-Files) | Broad catalogue of layout patterns, report-page hierarchy, panel treatment, filters, navigation, and domain-specific arrangements | Repository content is MIT-licensed at the referenced revision, but linked Figma Community resources can carry separate terms. Preserve attribution and verify each external asset's license before reuse. |

Reference snapshots reviewed while authoring this package:

- Microsoft Stock repository commit: `56b91d4e214b752a8e8c000a61808d2199aa47d9`
- Power BI Design Files repository commit: `3349447cae531b706dcfab2e2c1caef8c4dbac6c`

Re-check the current repository and license before importing any asset; revisions and terms may change.

## Adaptation workflow

1. **Inventory the current company dashboard first.** Look for `.pbix`, `.pbip`, `.pbir`, Power BI theme JSON, exported PDF/PNG, screenshots, or existing web code supplied in the workspace. Record its company colors, surface opacity, type scale, radii, spacing, number treatments, chart styling, page names, and interaction conventions. Current company language takes precedence over external inspiration.
2. **Inventory the inspiration.** Record the URL, revision, visible pages, stated license, asset origins, and any logos or proprietary data.
3. **Extract the analytical skeleton.** Write down the audience, decision, primary question, reading order, chart types, comparison frames, and interaction model.
4. **Reduce it to a layout fingerprint.** Capture proportions and relationships in words, for example: “narrow context rail; wide annotated series; event explanation on the right; ranked drivers below.” Do not trace exact coordinates.
5. **Map to the user's evidence.** Replace the topic, measures, grain, comparisons, annotations, and detail with the user's data model. If data is missing, mark a demo rather than fabricating facts.
6. **Blend, do not reskin.** Retain the company's recognizable neutrals and component behavior; borrow better hierarchy, annotation, and spacing from the inspiration. Limit company-color accents to selected series, totals, and decisive result numbers.
7. **Improve the interaction.** Implement filters, cross-highlighting, tooltips, drill-down, or export only where they help the decision. A static Power BI screenshot is not an interaction specification.
8. **Run a similarity check.** The result should share principles, not a unique arrangement of branded graphics or a pixel-identical skin. Change the visual language and ensure the hierarchy follows the new question.
9. **Record attribution.** In project notes or source comments, cite material references and licenses. Keep attribution out of the main UI unless the license or user requires it there.

## Working with PBIX files

PBIX files can contain structured report/page metadata, but their internal format varies by Power BI version. Treat extraction as research, not as a production dependency.

- Work on a copy and preserve the original.
- Inspect report pages, visual types, positions, groupings, theme tokens, filters, bookmarks, and navigation.
- If the binary cannot be inspected reliably, request an exported PDF or representative screenshots plus the Power BI theme JSON. Do not infer the visual system from the filename.
- Summarize reusable patterns as prose or neutral layout data.
- Do not publish embedded data, credentials, customer names, custom visuals, fonts, or images without permission.
- Do not bundle large PBIX files into this skill. Keep the runtime package small and self-contained.

## Safe-to-reuse abstraction levels

Usually safe and useful:

- analytical question and page hierarchy;
- generic grid proportions;
- chart-type choice;
- comparison and annotation patterns;
- interaction concepts;
- independently recreated semantic tokens.

Require explicit license review:

- logos, product marks, photography, illustrations, icons, and fonts;
- copied copywriting or commentary;
- embedded datasets;
- custom visual packages;
- a distinctive pixel-level composition.

When license status is unclear, link to the inspiration and recreate only general ideas from scratch.
