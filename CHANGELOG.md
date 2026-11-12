## [2.1.1] — 2026-11-12

### Changed
- **Quick Picker stays open:** choosing an emoji no longer closes the picker, in any tab. It closes on Escape (which clears the search first) or on a click outside.
- **Quick Picker remembers its tab:** reopening with the shortcut shows the tab used last; only the search text is cleared.
- **Insert into the previous app:** the picker keeps focus after the emoji is typed, so several emojis can be chosen in a row. If focus cannot be returned, the picker closes.
- **New application icon:** "Neon Smiling Planet" (`icons/Emo-Xpress_version_icons_PNGs/Neon Smiling Planet v2.1.1.png`) for the executable, installer, shortcuts and taskbar. The icon inside the window is unchanged.
- Version 2.1.0 → 2.1.1 in `package.json`, `package-lock.json`, `src-tauri/tauri.conf.json`, `src-tauri/Cargo.toml` and `src-tauri/Cargo.lock`.

### Added
- **Settings → Quick Picker → "Also copy to the clipboard"** (shown with "Insert into the previous app"; off by default). When on, the chosen emoji is copied as well as typed.
- Update Logs entry for 2.1.1.

### Fixed
- Settings changes (insert/copy choice and the copy switch) reach the Quick Picker when it opens. Previously the picker kept the values from its start-up until Emo-Xpress was restarted.

### Compatibility
- **No database migration** (still `0001` and `0002`). One row is added to `app_settings`: `quick_picker_copy_also` (`on` / `off`). Version 2.1.0 ignores it.

### Security
- No new permission, network access, shell access or content-security change. The capability files are unchanged.

### Verification (2026-11-12, build PC)
- `npx vitest run` (full frontend suite): **3,328 of 3,328 passed** (59 of 59 files), exit 0. Four first-run failures were version expectations hard-coded as 2.1.0; updated to 2.1.1 and re-run.
- `npm run typecheck`: exit 0. `npm run lint`: exit 0.
- `cargo test` (src-tauri): 22 of 22 passed.
- `npm run tauri:build`: exit 0; installer `Emo-Xpress_2.1.1_x64-setup.exe` and the executable built. The icon bytes of all six sizes are present in the executable and the installer.

## [2.1.0] — 2026-11-12

### Added
- **Quick Picker:** a global hotkey (default `Ctrl+Shift+E`) opens a small floating emoji picker over the active window, with search by name or meaning, the same catalogue and categories, arrow-key navigation, Enter to choose and Escape to clear or close. The picker closes when it loses focus.
- **Insert or copy:** after a choice, the emoji is typed into the window that was active before the picker opened (default), or copied to the clipboard only (Settings → Quick Picker). If the previous window cannot receive typing, the emoji is copied and the picker says so.
- **Custom global hotkey:** Settings → Quick Picker. Press a new combination and Save; Restore default returns to `Ctrl+Shift+E`. Refused: shortcuts without Ctrl or Alt, shortcuts used by another program, and Windows-reserved combinations. A refused change never replaces the working shortcut.
- **Tray:** "Open Quick Picker" and "Settings" in the tray menu. Exit from the tray releases the hotkey and closes all windows.
- **Windows icon:** the supplied Emo-Xpress icon is embedded in the executable and installer. The in-app logo is unchanged.

### Changed
- Emoji chosen in the Quick Picker are recorded in Recently Used. Favorites and Recently Used are re-read when the main window regains focus.
- Version 2.0.0 → 2.1.0 in the package and Tauri metadata.

### Compatibility
- **No new database migration** (still `0001` and `0002`). Two rows are added to the existing `app_settings` table: `quick_picker_shortcut` and `quick_picker_behavior`. No existing row is changed.
- New Rust dependency: `tauri-plugin-global-shortcut` 2.4.x. No npm dependency was added.

### Security
- The Quick Picker window has its own capability file with minimum permissions: SQL read, clipboard write and event listening.
- The main window's capability gains only event listen and unlisten permissions. No network, shell, filesystem or process permission was added. The Content Security Policy is unchanged.
- Dependency advisory RUSTSEC-2026-0459 (SQLite 3.46.0 through `tauri-plugin-sql`) is **open** in this release. See `SECURITY-ADVISORIES_v2.1.0.md`.

### Verification
- Frontend: 3,328 of 3,328 tests passed across 59 files. Typecheck and lint passed.
- Rust: 22 of 22 tests passed. `cargo clippy --all-targets` reported no warnings. Production build passed.
- Installer and standalone executable built; the supplied icon was confirmed inside both (byte comparison).
- Upgrade 2.0.0 → 2.1.0 run on the maintainer's PC after a verified database backup; row counts matched exactly afterwards.
- Windows Sandbox: upgrade and rollback with synthetic data passed; the Quick Picker appeared and inserted emoji into Notepad (visual observation).
- Still open: the independent on-PC checks listed in `RELEASE_NOTES_v2.1.0.md`.

## [2.0.0] — 2026-11-10

### Added
- **Expression Studio:** six modes for expressing an idea, creating an emoji-only summary, decorating text, adjusting tone, drafting a reply idea and explaining an expression. Includes 12 contexts plus a custom context, five tone controls, strict Minimal (1–2), Balanced (3–4) and Expressive (5–7) styles, explanations, copy, save and collection actions. The deterministic local engine works offline.
- **Contextual suggestions:** optional Ideas panels for the library, collections and saved combinations, plus “Suggest by meaning” from a no-results search. Suggestions are off by default; ordinary search ranking is unchanged.
- **Personalisation:** local defaults, up to 20 presets, optional history (off by default), separately consented raw-prompt retention, Useful / Not useful feedback, favourite patterns and reset controls.
- **Optional Anthropic assistance:** off by default, explicit consent and user action required. Requests use a fixed HTTPS host through Rust; keys are kept in Windows Credential Manager or session memory, never in app storage or logs. Provider output is schema-checked and falls back to local suggestions.
- **v2.0.0 branding:** owner-supplied logo used in the sidebar, About page, Windows executable, installer and shortcuts.

### Changed
- Version 1.1.1 → 2.0.0 across package and Tauri metadata.
- About privacy wording now describes the optional AI network path accurately.

### Fixed
- Reply ideas now respond appropriately to good news, thanks and bereavement-related messages.
- Closed Ideas panels no longer expose an invalid `aria-controls` target.

### Compatibility
- No new SQLite migration. Expression settings are bounded, versioned values in the existing `app_settings` table. Upgrade 1.1.1 → 2.0.0 and rollback compatibility were verified in Windows Sandbox.
- Content Security Policy and window capabilities are unchanged.

### Verification
- 3,300 frontend tests passed across 58 files; 19 Rust tests passed.
- Typecheck, lint, formatting, Cargo check, Clippy (0 warnings), catalogue validation (27/27) and production dependency audit (0 vulnerabilities) passed.
- Windows Sandbox install, launch, shortcut, close and uninstall checks passed.
- Installer is unsigned. No real Anthropic request was made because no API key was available. A real screen-reader session, physical display-scaling change and `cargo audit` were not completed.

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
