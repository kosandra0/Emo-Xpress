# Changelog

All notable public changes to Emo-Xpress are documented here.

## [1.0.1] - 2026-11-07

Desktop customization and interface refinement release. The application version remains 1.0.1; the Unicode catalogue and core emoji data are unchanged.

### Added
- Collapsible full sidebar with expanded navigation and a compact icon-only rail.
- Navigation tooltips in the compact sidebar.
- Cursor-following translucent ambient glow across the application.
- Reduced-motion and high-contrast handling for the ambient glow.
- Animated category navigation with a sliding active indicator, subtle hover movement, and selection glow.
- Application version label beside the Emo-Xpress name.
- About page with application, Unicode/CLDR, and catalogue information.
- Left/right positioning preference for the macOS-style traffic-light window controls.
- Typography settings with a searchable selector, live preview, and reset-to-default action.
- Availability detection for 49 Windows system font families on the development PC. Unavailable fonts are not downloaded or silently applied.
- Updated Neon Emoji Hub artwork across the sidebar and generated Windows application, executable, and installer icon assets.

### Updated
- Sidebar collapse behaviour now applies to the entire sidebar rather than only the Categories list.
- Main content area expands when the sidebar switches to its compact icon-only rail.
- Window controls retain their native Close, Minimize, and Maximize/Restore actions in either left or right orientation.
- Local settings now cover sidebar state, window-control position, and selected font family in addition to existing preferences.
- Interface typography customization remains separate from emoji font fallback and Unicode clipboard data.
- Installer and application branding use the updated logo.

### Preserved
- 3,963 fully-qualified Unicode Emoji 18.0 entries.
- CLDR 49 English names and annotation keywords.
- Nine emoji categories, search, Favorites, Recently Used, and exact Unicode clipboard copying.
- Existing application identifier, SQLite database location, and user data.
- Offline-first operation, strict content security policy, and least-privilege Tauri permissions.

### Verification
- Frontend tests: 293/293 passed.
- Catalogue validation: 27/27 passed.
- TypeScript typecheck, ESLint, and production build passed.
- Rust formatting, compilation checks, and 2 Rust tests passed.
- Production dependency audit: 0 vulnerabilities.
- Native Windows mouse checks covered both traffic-light orientations.
- Sidebar collapse, tooltips, font choice, and control-position settings worked in the real application and survived an application restart.
- Reduced-motion and high-contrast glow fallbacks were checked in the real WebView.
- Existing user database backup hash matched before and after the update.

### Known limitations
- The installer is unsigned.
- Testing was performed on one Windows 10 Enterprise development PC; clean-machine, Windows 11, Windows restart, screen-reader, and hardware scaling above 100% tests remain outstanding.
- Keyboard-focus tooltip behaviour was checked in tests and code, not separately exercised in the actual desktop window.
- The compact sidebar is automatically used below approximately 940 px window width.
- Font availability depends on fonts installed on the user's Windows computer. All 49 choices were available on the development PC.
- Sustained pointer movement over the emoji grid showed around half a CPU core of activity on the development PC, with or without the cursor glow; the glow itself added no measurable CPU use in the reported comparison.
- Some family and parent/child emoji remain grey silhouette tiles in Noto Color Emoji.
- WebView2 text-field context menus may retain browser-provided entries.

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
