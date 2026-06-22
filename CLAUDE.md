# CLAUDE.md, gridline-releases

Public GitHub-release host for the **Gridline for Revit** plugin's DLL zips
(`Gridline-Revit2025-dlls.zip` / `Gridline-Revit2026-dlls.zip`). **No source code
here** — release assets only, pushed by `gridline-revit`'s CI on every `VERSION`
bump. The in-plugin updater downloads from these public release URLs.

## Sibling repositories (Gridline topology)

Gridline is **four separate repos**, not a monorepo.

- `gridline-revit/` — the Revit plugin monorepo: C# plugin in `src/`, the live
  plugin API in `plugin-api/` (Vercel `gridline-revit-api` → api.gridlineos.com). **Its CI
  (`release.yml`) cuts the releases hosted here** and rewrites
  `gridline-revit/plugin-api/api/version.ts` `MANIFEST` with the new download URLs.
- `gridline-web/` — Next.js web product → gridline.sh.
- `gridline-design-system/` — brand/UI tokens.
- ~~`gridline-revit-proxy`~~ — **archived** standalone proxy repo (dead).

Releases are titled "Gridline for Revit v<x.y.z>" (was "ADA Copilot" through
v1.10.76; rebranded as of v1.11.0).
