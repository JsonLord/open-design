# Scoped install and upgrade for AI agents

This document is an execution contract for agents asked to install or upgrade **only** the `dashboard` bundle. The canonical source is:

```text
https://github.com/JsonLord/open-design/tree/main/design-templates/dashboard
```

Never sync the repository root, replace the whole `skills/` or `design-templates/` tree, or delete unrelated OpenDesign files.

## 1. Detect the installation mode

Use the first applicable mode:

1. **OpenDesign CLI available:** `command -v od` succeeds and its daemon is reachable. Prefer the user-level import below; it shadows the bundled dashboard without modifying the application installation.
2. **OpenDesign source checkout:** a user-supplied or current ancestor directory contains `AGENTS.md`, `package.json`, `design-templates/AGENTS.md`, and `design-templates/dashboard/SKILL.md`. Use the source-checkout procedure.
3. **Ambiguous or absent:** if multiple roots match, the target has local changes, or OpenDesign cannot be verified, stop and ask the user to choose a root. Do not search or mutate broad system directories.

## 2. User-level import with OpenDesign CLI

Fresh import:

```sh
od skill install https://github.com/JsonLord/open-design/tree/main/design-templates/dashboard
od skills show dashboard
```

The GitHub tree URL tells OpenDesign to extract the exact folder containing this `SKILL.md`; other skills and templates in the repository are not installed.

Upgrade an existing user-level copy only after the user has explicitly requested replacement:

```sh
od skills show dashboard
od skill uninstall dashboard
od skill install https://github.com/JsonLord/open-design/tree/main/design-templates/dashboard
od skills show dashboard
```

OpenDesign intentionally refuses to overwrite an installed user skill. Uninstall/install is therefore the explicit upgrade path. If installation fails after uninstall, report the error immediately; the bundled dashboard remains available in a normal OpenDesign installation.

## 3. Update one folder in an OpenDesign source checkout

Before changing files:

```sh
test -f "$OPEN_DESIGN_ROOT/AGENTS.md"
test -f "$OPEN_DESIGN_ROOT/package.json"
test -f "$OPEN_DESIGN_ROOT/design-templates/AGENTS.md"
test -f "$OPEN_DESIGN_ROOT/design-templates/dashboard/SKILL.md"
git -C "$OPEN_DESIGN_ROOT" status --porcelain -- design-templates/dashboard
```

`OPEN_DESIGN_ROOT` is a task-specific variable supplied or resolved by the agent; do not repurpose `HOME` or another system variable. If the scoped status output is non-empty, stop and ask whether to preserve, commit, or replace those edits.

Stage only the canonical folder in a temporary checkout:

```sh
dashboard_tmp="$(mktemp -d)"
git clone --depth 1 --filter=blob:none --no-checkout \
  https://github.com/JsonLord/open-design.git "$dashboard_tmp/source"
git -C "$dashboard_tmp/source" sparse-checkout init --cone
git -C "$dashboard_tmp/source" sparse-checkout set design-templates/dashboard
git -C "$dashboard_tmp/source" checkout main
test -f "$dashboard_tmp/source/design-templates/dashboard/SKILL.md"
grep -q '^name: dashboard$' "$dashboard_tmp/source/design-templates/dashboard/SKILL.md"
```

Install with a recoverable adjacent backup. Resolve and inspect all paths before running these commands:

```sh
dashboard_target="$OPEN_DESIGN_ROOT/design-templates/dashboard"
dashboard_stamp="$(date -u +%Y%m%dT%H%M%SZ)"
dashboard_stage="$OPEN_DESIGN_ROOT/design-templates/.dashboard.install.$dashboard_stamp"
dashboard_backup="$OPEN_DESIGN_ROOT/design-templates/dashboard.backup.$dashboard_stamp"
cp -R "$dashboard_tmp/source/design-templates/dashboard" "$dashboard_stage"
mv "$dashboard_target" "$dashboard_backup"
mv "$dashboard_stage" "$dashboard_target"
git -C "$OPEN_DESIGN_ROOT" diff -- design-templates/dashboard
```

Do not remove the backup automatically. Tell the user where it is and let them delete it after review. If the checkout is expected to stay clean, prefer applying the folder on a branch and commit only paths under `design-templates/dashboard/`.

## 4. Scope and verification invariants

- The only installed identity is `name: dashboard`.
- Every changed path is under `design-templates/dashboard/` for a source checkout, or under OpenDesign's user-managed `dashboard` shadow for a CLI import.
- Never use a recursive sync with deletion against an OpenDesign root.
- Never overwrite a dirty target silently.
- Never install the repository URL without the `/tree/main/design-templates/dashboard` suffix when the intent is this bundle only.
- Verify `SKILL.md`, `assets/template.html`, `example.html`, and the referenced Markdown files are present after installation.
- Report the source URL, method, target identity, and verification result to the user.
