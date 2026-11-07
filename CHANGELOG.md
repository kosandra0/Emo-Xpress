# Changelog

All notable public changes to Emo-Xpress are documented here.

## [1.0.0] - 2026-11-07

First public Windows release.

### Added
- Bundled searchable catalogue of 3,963 fully-qualified Unicode Emoji 18.0 entries.
- CLDR 49 English names and annotation keywords.
- Nine category groups and a virtualized emoji grid.
- Deterministic local search with name and keyword matching.
- Persistent Favorites stored in local SQLite.
- Recently Used history, newest-first and capped at 100 unique entries.
- Exact Unicode clipboard copying, including multi-code-point sequences.
- Dark, Light, and System appearance modes.
- Bundled Noto Color Emoji 2.057 for broader Emoji 18.0 glyph coverage.
- Local-first, offline-capable core functionality.
- Windows x64 NSIS installer.

### Quality and verification
- 210/210 frontend tests passed.
- Unicode catalogue validation: 27/27 checks passed.
- TypeScript typecheck, lint, production build, Rust formatting and compilation checks passed.
- Production dependency audit: 0 vulnerabilities.
- Installer fresh-install, launch, same-version reinstall, and uninstall checks completed on the development PC.

### Known limitations
- The installer is unsigned.
- Clean-machine and Windows 11 installation tests were not completed.
- Screen-reader and hardware display-scaling tests above 100% remain outstanding.
- Some family/parent-child glyphs appear as grey silhouette tiles in the bundled Noto font.
- WebView2 text-field context menu retains a few browser-provided entries.

