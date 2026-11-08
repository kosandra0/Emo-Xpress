# Changelog

All notable changes to Emo-Xpress. Dates are in India Standard Time. Earlier entries are summarised from `MASTER_DEVELOPMENT.md`.

## [1.1.1] — 2026-11-08

### Added
- Update Logs page (below About): the application's history by date, with detailed entries, release/milestone labels and honest handling of missing times; bundled and offline.
- Ten new application themes (Sakura Mist, Tranquil Sky, Lavender Haze, Forest Sanctuary, Arctic Serenity, Desert Dusk, Moonlit Pearl, Coastal Breeze, Peach Blossom, Amethyst Calm): 18 in total, each with Dark and Light variants and previews painted with their real tokens.
- Ten Emoji Name Styles (Settings → Emoji Name Style) for the names under emoji cards, with live previews on real cards, Reset to Default, and contrast adjusted per theme and appearance (setting key `emoji_name_style`).
- Developer card in About ("kosandra0 (musafir)") with the GitHub profile link, opened by one fixed native command, and a Copy link fallback.
- New v1.1.1 logo in the sidebar, About page and the generated Windows icon set.

### Changed
- Themes now restyle the whole window (page, ambient light, glass, cards, borders, dialogs, toasts, shadows), not only the accent colours; Default is unchanged.
- Settings and About use their container width (responsive from the minimum window to maximized, sidebar expanded or collapsed).
- Version 1.1.0 → 1.1.1 in `package.json`, `package-lock.json`, `src-tauri/Cargo.toml`, `src-tauri/Cargo.lock` and `src-tauri/tauri.conf.json`.

### Fixed
- Settings sections with multi-word titles had no accessible name (invalid `aria-labelledby` ids).
- The collection emoji picker's search field left a large gap above the results (a row-sized flex basis inside a column).

### Compatibility
- No new database migration (still `0001` and `0002`); the theme and name style are ordinary `app_settings` rows. 1.1.0 opens a database used by 1.1.1 and ignores the two newer values (it shows its own default look and leaves them untouched). See `RELEASE_NOTES_v1.1.1.md`.
- No dependency, permission, CSP or capability change.

### Verification
- Installer `Emo-Xpress_1.1.1_x64-setup.exe`, 4,494,821 bytes, SHA-256 `ca1a7e72fbc31f99bf37b872630c942f4e564da22942c1ef0e0eb8ab3d379457`, not code-signed.
- 2,815 vitest tests (35 files), 4 Rust tests, typecheck, lint, catalogue validation, build and audit pass; installer, upgrade from 1.1.0, uninstall, reinstall, downgrade to 1.1.0 and restore verified in Windows Sandbox (126/126 checks).

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
- Installer `Emo-Xpress_1.1.0_x64-setup.exe`, 4,460,811 bytes, SHA-256 `d17e2bc1e6e1bb4008dea80551370c767bafae0cd6cfdc97c273c4717500e008`, not code-signed.
- 1,144 vitest tests, 3 Rust tests, typecheck, lint, catalogue validation, build and audit pass; installer, upgrade, uninstall, reinstall and downgrade/restore verified in Windows Sandbox (85/85 checks).

## [1.0.1] — 2026-11-07
- Custom title bar with macOS-style window controls, system tray and Close Behaviour, Window Corner Radius, animated and collapsible sidebar, cursor-following glow, About page, window-controls position (left / right), font choice, new logo and icons.
- Installers: `Emo-Xpress_1.0.1_x64-setup.exe`, SHA-256 `677b95a15aa8fb25a10057ac6f9863923a0229b64a7c542ff8ab63331f968798` (final build), not code-signed.

## [1.0.0] — 2026-11-07
- First release: 3,963-entry Unicode 18.0 emoji catalogue, categories, ranked search, Favorites, Recently Used (100 entries), exact copy to the clipboard, Dark / Light / System appearance, local SQLite storage.
- Installer: `Emo-Xpress_1.0.0_x64-setup.exe`, SHA-256 `45263613c649bd842ad74c73565545ab17aa76b6c1204d13adf9f113a178ba69`, not code-signed.
