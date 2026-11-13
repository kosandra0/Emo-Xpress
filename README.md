# Emo-Xpress

<p align="center">
  <img src="assets/Emo-Xpress_v2.1.2_256x256.png" alt="Emo-Xpress v2.1.2 logo" width="256" height="256" />
</p>

<h2 align="center">Every emotion. One expression.</h2>
<p align="center">A local-first Windows emoji library and expression assistant.</p>
<p align="center">Windows 10/11 · x64 · Version 2.1.2</p>

<p align="center">
  <a href="https://github.com/kosandra0/Emo-Xpress/releases">Releases</a> ·
  <a href="CHANGELOG.md">Changelog</a> ·
  <a href="RELEASE_NOTES_v2.1.2.md">v2.1.2 release notes</a> ·
  <a href="RELEASE_NOTES_v2.1.1.md">v2.1.1 release notes</a> ·
  <a href="RELEASE_NOTES_v2.1.0.md">v2.1.0 release notes</a> ·
  <a href="SECURITY-ADVISORIES_v2.1.0.md">v2.1.0 security advisories</a> ·
  <a href="RELEASE_NOTES_v2.0.0.md">v2.0.0 release notes</a> ·
  <a href="PRIVACY.md">Privacy</a> ·
  <a href="THIRD_PARTY_NOTICES.md">Third-party notices</a>
</p>

---

## Version 2.1.2

Version 2.1.2 makes the Quick Picker fade in and out, closes it on Escape even after a mouse choice, and closes it on a click outside. It uses a new icon. See [RELEASE_NOTES_v2.1.2.md](RELEASE_NOTES_v2.1.2.md).

## Version 2.1.1

Version 2.1.1 keeps the Quick Picker open after each choice, remembers the tab you used, adds an optional "Also copy to the clipboard" switch, and gives Emo-Xpress a new icon. See [RELEASE_NOTES_v2.1.1.md](RELEASE_NOTES_v2.1.1.md).

## Version 2.1.0

Emo-Xpress is a Windows desktop emoji library, organiser and expression assistant. Browse the Unicode catalogue, organise collections, create reusable combinations, or describe what you want to express and receive emoji suggestions.

**New in 2.1.0:** a global hotkey (default `Ctrl+Shift+E`) opens a floating **Quick Picker** over whatever window you are using, so you can choose an emoji and have it typed into that window. Emo-Xpress runs in the system tray, and the hotkey is customisable in Settings. See [RELEASE_NOTES_v2.1.0.md](RELEASE_NOTES_v2.1.0.md) for details and for what has and has not been tested.

**The core Expression Studio works offline.** Optional Anthropic assistance is off by default and is never required for local features.

## Downloads

Release files are listed on the [Releases page](https://github.com/kosandra0/Emo-Xpress/releases).

| File | Size | SHA-256 |
|---|---:|---|
| `Emo-Xpress_2.1.1_x64-setup.exe` (recommended installer) | 4,730,807 bytes | `49b659cf32e01ad1f95006ecacc6257f9c9280fea31e6a7c68342d04ba3fbefa` |
| `Emo-Xpress_2.1.1_windows-x64_standalone.exe` (runs without installing) | 7,874,048 bytes | `2bbfb46f3ade14964484251e8c07c7e4341037494b9338814b94f5049ad9c5c2` |

Verify a downloaded file before running it:

```powershell
Get-FileHash .\Emo-Xpress_2.1.1_x64-setup.exe -Algorithm SHA256
```

Both files are **not code-signed**. Windows SmartScreen may show a warning. Compare the SHA-256 with `SHA256SUMS.txt` before choosing **More info → Run anyway**.

## What's new

### Quick Picker and Windows integration (2.1.0)

- **Global hotkey** `Ctrl+Shift+E` (default). Change it in Settings → Quick Picker and press Save; Restore default returns to `Ctrl+Shift+E`.
- **Floating picker:** search by name or meaning, arrow keys to move, Enter to choose, Escape to clear or close. The picker closes when it loses focus.
- **Insert or copy:** types the emoji into the window you were using (default), or copies it to the clipboard only. If the previous window cannot receive typing, the emoji is copied instead and the picker says so.
- **Tray:** "Open Quick Picker" and "Settings" in the tray menu. With the tray close option on, closing the main window keeps the hotkey working.
- **Favorites and Recently Used** stay current between the picker and the main window.
- **Themes:** the picker uses the app's appearance settings.

### Expression Studio

Describe a feeling or provide a sentence and get emoji suggestions in six modes:

1. Express an idea.
2. Emoji-only summary.
3. Add emoji to your text.
4. Adjust the tone.
5. Create a reply idea.
6. Explain an expression.

Choose from 12 contexts plus a custom context, five tone controls, and three strict output styles:

- **Minimal:** 1–2 emoji.
- **Balanced:** 3–4 emoji.
- **Expressive:** 5–7 emoji.

Suggestions include concise explanations and preserve exact Unicode sequences. The local engine uses a built-in English vocabulary; unknown words are identified rather than guessed.

### Contextual suggestions and semantic search

Optional suggestion panels can offer ideas in the emoji library, collections and saved combinations. They are **off by default**. “Suggest by meaning” is available from a no-results search and runs only when pressed. Existing ordinary emoji search remains unchanged.

### Personalisation

- User-controlled defaults for context, tone, result count and preferred expression length.
- Up to 20 saved presets.
- Optional expression history, off by default.
- Raw prompt text is retained only with separate consent.
- Useful / Not useful feedback, favourite patterns and reset controls.

### Optional AI assistance

AI assistance is **off by default**. When enabled, the user reviews a consent disclosure and explicitly presses “Improve with AI”. The optional provider can re-rank only candidates selected by the offline engine. Requests go to the fixed `api.anthropic.com` host over HTTPS from the Rust side. The API key is stored in Windows Credential Manager or in session memory; it is not stored in the app database, returned to JavaScript or written to logs. Provider responses are schema-checked and candidate IDs are allowlisted. Failures fall back to local suggestions.

Using your own Anthropic API key may incur charges from your provider. No API key or subscription is required for offline features. The real provider request was **not live-tested** during this release because no API key was available; mock and test-double coverage passed.

## Preserved features

- 3,963 fully-qualified Unicode Emoji 18.0 catalogue entries, with English CLDR 49 names and annotations.
- Nine categories, ranked search and a keyboard-accessible virtualised grid.
- Favorites and Recently Used.
- Exact clipboard copying, including flags, keycaps, skin tones, tag sequences and ZWJ sequences.
- Personal collections, folders and saved combinations.
- 18 application themes and 10 Emoji Name Styles.
- Update Logs, About information and Windows desktop integration.

## Installation and upgrade

Close Emo-Xpress before installing. The per-user installer installs under `%LOCALAPPDATA%\Emo-Xpress`; application data stays under `%APPDATA%\com.emoxpress.desktop`.

Upgrading from 2.0.0 to 2.1.0 is in place and adds no database migration; it adds two settings rows for the Quick Picker. Upgrading from 1.x preserves Favorites, Recently Used, collections, folders, combinations and settings. Version 2.0.0 adds no new SQLite migration; it stores bounded, versioned settings in the existing `app_settings` table. The 1.1.1 compatibility/rollback path was verified in Windows Sandbox. Version 1.0.1 cannot open a database after migration 0002 has been applied, so retain a backup when upgrading from that older version.

## Verification

### Version 2.1.0 (2026-11-12)

- **3,328 / 3,328** frontend tests passed across 59 files.
- **22 / 22** Rust tests passed. Typecheck, lint, `cargo clippy --all-targets` (no warnings) and the production build passed.
- Windows installer and standalone executable built; the supplied icon was confirmed inside both by byte comparison.
- Upgrade 2.0.0 → 2.1.0 on the maintainer's PC after a verified database backup: installer exit 0, app launched, database row counts identical before and after.
- Windows Sandbox: upgrade and rollback with synthetic data; the Quick Picker inserted emoji into Notepad (visual observation by the maintainer).
- Items not yet independently confirmed are listed in [RELEASE_NOTES_v2.1.0.md](RELEASE_NOTES_v2.1.0.md).

### Version 2.0.0 (reference)

- **3,300 / 3,300** frontend tests passed across 58 files, run sequentially.
- **19** Rust tests passed.
- TypeScript typecheck, lint, Rust formatting, Cargo check and Clippy passed; Clippy reported 0 warnings.
- Unicode catalogue validation: 27 / 27 checks, 3,963 entries.
- `npm audit --omit=dev`: 0 production vulnerabilities.
- Windows Sandbox fresh install, launch, shortcut creation, graceful close and uninstall passed.

## Known limitations

- **Quick Picker:** insertion was observed working in Notepad only. Other applications, administrator-elevated windows and the clipboard fallback in every case still need independent testing. See [RELEASE_NOTES_v2.1.0.md](RELEASE_NOTES_v2.1.0.md).
- **Dependency advisory RUSTSEC-2026-0459 is open** in 2.1.0 (SQLite 3.46.0 through `tauri-plugin-sql`). The fix needs a database-layer upgrade planned for a later release. See [SECURITY-ADVISORIES_v2.1.0.md](SECURITY-ADVISORIES_v2.1.0.md).
- The expression vocabulary is English-only and contains about 3,000 phrases.
- On an independent set of 120 prompts, the first suggestion contained an expected emoji for 75%; at least one of four suggestions did so for 87.5%. These are measured results, not a guarantee of correctness.
- The Anthropic path was not tested against the live service because no API key was available.
- The installer is unsigned.
- A real screen-reader session and a physical Windows display-scaling change were not tested; scaling was emulated.
- `cargo audit` was not run because the tool was not installed.

## Privacy

Emo-Xpress has no account, telemetry, analytics or cloud profile. Core features use the bundled catalogue and local SQLite data. The app does not read clipboard contents. Network access is used only if optional AI assistance is enabled and the user explicitly invokes it. See [PRIVACY.md](PRIVACY.md) for details.

## Technology

Tauri 2, Rust, React 19, TypeScript, Vite, SQLite, Unicode Emoji 18.0, CLDR 49 and Noto Color Emoji 2.057. See [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

## Repository contents and licence

This public repository contains public-facing release documentation, checksums and visual assets. It does **not** publish the application's full source tree. No project software licence has been selected or added yet; do not assume that the application source or original artwork is licensed for reuse. Third-party materials remain subject to their respective licences.

---

<p align="center"><strong>Emo-Xpress · Every emotion. One expression.</strong></p>
