# Changelog

All notable public changes to Emo-Xpress are documented here.

## [1.1.0] — 2026-11-08

### Added
- Personal collections: create, rename, reorder, delete; per-collection search; *Add to collection* from All Emojis, categories, Favorites and Recently Used.
- Folders for collections (create, rename, delete, move, ordering); deleting a folder keeps its collections.
- Custom combinations: builder (1–32 emojis), Saved Combinations hub, edit, delete, exact copy to the clipboard, placement in collections. Copying a combination does not touch Recently Used.
- Eight colour themes (Settings → Theme) applied with `data-palette`, independent of Dark / Light (`data-theme`); startup hold prevents a flash of the default theme.
- Database migration `0002_collections.sql` (new tables only; v1.0.1 tables are not modified).

### Changed
- Window controls (red / yellow / green) are now 24 × 24 CSS px click targets (WCAG 2.2 AA 2.5.8); the visible dots stay 13 px; the title bar's side padding is 10 px so the first dot stays in place.
- Version 1.0.1 → 1.1.0 in `package.json`, `package-lock.json`, `src-tauri/Cargo.toml`, `src-tauri/Cargo.lock` and `src-tauri/tauri.conf.json`.

### Compatibility
- The upgrade is one-way: 1.0.1 cannot open a database migrated by 1.1.0 (it shows a storage notice and leaves the file unchanged). See `RELEASE_NOTES_v1.1.0.md` for the backup and rollback procedure.
- No dependency, permission, CSP or capability change.

### Verification
- 1,144 Vitest tests, 3 Rust tests, typecheck, lint, catalogue validation, production build and production dependency audit pass; installer, upgrade, uninstall, reinstall and downgrade/restore verified in Windows Sandbox (85/85 checks).

## [1.0.1] - 2026-11-07

Desktop interface, window customization, typography, and branding refinement. The application version remains 1.0.1; the Unicode catalogue and core emoji data are unchanged.

### Added
- Full collapsible sidebar with a 264 px expanded layout and an 80 px icon-only rail.
- Navigation icons for all destinations in compact mode, including all nine categories, Settings, and About.
- Hover tooltips for compact navigation.
- Cursor-following translucent violet ambient glow, with reduced-motion, high-contrast, and forced-colors handling.
- Animated category navigation with a sliding active indicator, soft selection glow, and restrained hover movement.
- Version badge beside the Emo-Xpress name.
- Dedicated About page with application, Unicode/CLDR, and catalogue information.
- Left/right positioning preference for the macOS-style traffic-light window controls.
- Typography settings with a searchable selector, live preview, font availability detection, and Reset to Default.
- Updated Neon Emoji Hub branding in the sidebar and generated Windows application, executable, taskbar, and installer icon assets.

### Updated
- Sidebar collapse behaviour now applies to the entire sidebar rather than only the Categories list.
- Below approximately 940 px window width, the compact icon rail is forced and the manual toggle is hidden.
- Main content area grows when the sidebar is collapsed.
- Title remains centred when traffic lights are positioned on either side.
- Local settings now include sidebar state, traffic-light position, and selected font family.
- Interface typography remains separate from emoji glyph rendering and Unicode clipboard data.

### Preserved
- 3,963 fully-qualified Unicode Emoji 18.0 entries and CLDR 49 English annotations.
- Nine categories, search, Favorites, Recently Used, and exact Unicode clipboard copying.
- Application identifier, SQLite database location, migration, existing user data, and existing appearance/window preferences.
- Offline-first operation, content security policy, and least-privilege Tauri permissions.
- No database schema migration was required; the three new preferences use additive keys in the existing app_settings table.

### Verification
- Frontend tests: 293/293 passed across 17 files.
- Catalogue validation: 27/27 passed.
- TypeScript typecheck, ESLint, and production build passed.
- Rust formatting and compilation checks passed; 2 Rust tests passed.
- Production dependency audit (npm audit --omit=dev): 0 vulnerabilities.
- Native Windows mouse checks covered both traffic-light orientations, Close/Minimize/Maximize, and title-bar dragging.
- On an isolated test identifier, sidebar collapse, hover tooltip, font choice, and control-position settings were exercised in the native app and survived an application restart.
- Cursor glow was checked with real mouse movement. Reduced-motion, contrast-more, and forced-colors behaviour was checked using WebView2 preference emulation.
- System-tray and corner-radius behaviour were verified on an isolated build.
- The final installer was installed over the existing v1.0.1 installation on the owner's PC. The real database was backed up and read-only checked; its SHA-256 matched before and after installation.

### Known limitations
- The installer is unsigned.
- Testing was performed on one Windows 10 Enterprise development PC. Windows 11, clean-machine installation, Windows restart, screen readers, real Windows High Contrast, and hardware display scaling above 100% were not tested.
- Native resize behaviour below 940 px with the compact rail active was not repeated in this final round.
- Keyboard-focus tooltip behaviour was tested automatically and reviewed in code, but not separately exercised with a physical keyboard in the native window.
- The owner's real database was not modified to test the new sidebar, font, or traffic-light-position setting writes; those writes were tested on an isolated identifier. The owner's production database hash and contents were preserved.
- All 49 fonts were installed on the development PC; other computers may have fewer.
- Some family and parent/child emoji render as grey silhouette tiles in Noto Color Emoji.
- WebView2 text-field context menus may still list browser-provided “Emoji” and “Import passwords” entries.
- Sidebar transition frame times were not profiled. The installer is unsigned.

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
