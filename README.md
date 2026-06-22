# gridline-releases

Public download host for the **[Gridline for Revit](https://github.com/gridlineos/gridline-revit)** plugin.

This repo holds **only the per-version `Gridline-Revit2025-dlls.zip` /
`Gridline-Revit2026-dlls.zip` artifacts**, attached to a GitHub Release
for each plugin version. The in-plugin update flow downloads from these
release URLs.

## Why this repo exists

The plugin source + the hosted plugin API + the knowledge-base data live in a
private monorepo (`gridlineos/gridline-revit`). The in-plugin updater needs
to fetch DLL zips without HTTP auth, so the artifacts are mirrored here
where they can be served over public release URLs.

There is **no source code** here — only release assets pushed by the
monorepo's CI on every `VERSION` bump.

## How a release happens

1. A maintainer bumps `VERSION` in the private monorepo.
2. The monorepo's `.github/workflows/release.yml` builds Revit 2025 +
   Revit 2026 DLL zips.
3. CI calls `gh release create v<VERSION>` against THIS repo with both
   zips attached, then rewrites `plugin-api/api/version.ts` `MANIFEST` in the
   monorepo so the plugin can discover the new version.
4. Vercel redeploys the plugin API with the new MANIFEST; the plugin's
   `X-Latest-Version` header surfaces the release on the next user request.

No issues, no PRs — file those on the monorepo (private; ping the
maintainer).

## License

MIT (release artifacts only).
