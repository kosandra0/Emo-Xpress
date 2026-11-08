# Emo-Xpress

<p align="center">
  <img src="assets/emo-xpress-v1.1.0-banner.webp" alt="Emo-Xpress · Your Personal Emoji Hub" width="820" />
</p>

<h2 align="center">Every emotion. One expression.</h2>

<p align="center">
  A personal emoji hub for Windows. Discover 3,963 Unicode emoji, organise your own collections, build custom expressions, and copy exact sequences in one action.
</p>

<p align="center">
  <strong>Build 1.1.0 prepared · Owner publication pending</strong> · Windows x64 · Unicode Emoji 18.0 · CLDR 49
</p>

<p align="center">
  <a href="https://github.com/kosandra0/Emo-Xpress/releases">GitHub Releases</a> ·
  <a href="CHANGELOG.md">Changelog</a> ·
  <a href="RELEASE_NOTES_v1.1.0.md">v1.1.0 release notes</a> ·
  <a href="THIRD_PARTY_NOTICES.md">Third-party notices</a> ·
  <a href="PRIVACY.md">Privacy</a>
</p>

---

## What Emo-Xpress does

Emo-Xpress is a local-first Windows emoji library and personal organiser. It combines the official Unicode catalogue with personal collections, reusable expressions and interface customisation.

### Core emoji library

- **3,963 fully-qualified entries** from Unicode Emoji 18.0.
- English names and search annotations from Unicode CLDR 49.
- Nine standard categories and ranked local search.
- Persistent Favorites.
- Recently Used history, capped at 100 unique emoji.
- Exact clipboard copying, including flags, keycaps, skin-tone modifiers, tag sequences and ZWJ emoji.

### New in v1.1.0

- **Personal collections:** Create, rename, reorder and delete collections. Add emoji from All Emojis, categories, Favorites or Recently Used. Each collection has its own search.
- **Folders:** Group collections, move them between folders, reorder them, and keep unfiled collections. Deleting a folder keeps the collections it contains.
- **Custom combinations:** Build and save named sequences of 1–32 emoji, edit or delete them later, and copy the exact sequence with no added separators.
- **Saved Combinations hub:** Find and manage saved expressions independently; combinations can also be placed in collections.
- **Eight colour themes:** Choose a palette in Settings → Theme. The palette is independent of Dark / Light / System appearance and is applied before the first screen is drawn.
- **Larger window-control targets:** Close, Minimize and Maximize/Restore controls have 24 × 24 CSS-pixel click targets while the visible traffic-light dots remain 13 px.

### Preserved from v1.0.1

The v1.1.0 build retains the existing catalogue, search, categories, Favorites, Recently Used, exact emoji copying, Dark / Light / System appearance, custom window corner radius, left/right window-control placement, font selection, collapsible sidebar, cursor glow, system tray and close behaviour.

## Build and publication status

The v1.1.0 Windows x64 installer has been built and verified in a disposable Windows Sandbox profile. It has **not yet been published as a GitHub Release**. The repository's Releases page remains the place to check which installer is publicly available; the owner will publish the v1.1.0 release separately.

### v1.1.0 installer details

| Item | Value |
|---|---|
| File | `Emo-Xpress_1.1.0_x64-setup.exe` |
| Size | 4,460,811 bytes (4.25 MiB) |
| SHA-256 | `d17e2bc1e6e1bb4008dea80551370c767bafae0cd6cfdc97c273c4717500e008` |
| Architecture | Windows x64 |
| Code signing | Unsigned |

The installer binary is intentionally not stored in the Git repository. It is intended to be attached to the v1.1.0 GitHub Release by the owner.

### Windows SmartScreen

The installer is not code-signed. Windows may display a “Windows protected your PC” SmartScreen warning. Before running an installer, verify its SHA-256 against [SHA256SUMS.txt](SHA256SUMS.txt) and the published release information. The v1.1.0 sandbox installs were silent, so the interactive SmartScreen flow was not observed during testing.

## Before upgrading from v1.0.1

The first launch of v1.1.0 applies SQLite migration `0002`. **This database upgrade is one-way:** v1.0.1 cannot open a database after migration 0002 has been applied. It displays a storage-unavailable notice and leaves the migrated database untouched.

1. Quit Emo-Xpress completely. If it is in the system tray, choose **Exit** from the tray menu.
2. Back up `%APPDATA%\com.emoxpress.desktop\emoxpress.db`. If `emoxpress.db-wal` or `emoxpress.db-shm` exists, keep those files with the database backup.
3. Install v1.1.0 over v1.0.1.
4. Launch v1.1.0 and allow the migration to complete.

Favorites, Recently Used and existing settings are preserved by the migration. Read [RELEASE_NOTES_v1.1.0.md](RELEASE_NOTES_v1.1.0.md) before upgrading.

### Returning to v1.0.1

Keep a copy of the migrated v1.1.0 database files before restoring the pre-upgrade backup. Uninstall v1.1.0, install v1.0.1, move the migrated `emoxpress.db`, `emoxpress.db-wal` and `emoxpress.db-shm` files aside together, then restore the pre-upgrade `emoxpress.db` backup. Do not delete the migrated files: data created in v1.1.0 is not present in the older backup and can only be recovered by returning to the saved v1.1.0 database files.

## Verification summary

The v1.1.0 development record and release notes report:

| Check | Result |
|---|---:|
| Frontend tests | 1,144 passed across 27 test files |
| Rust tests | 3 passed |
| Unicode catalogue validation | 27/27 passed (3,963 entries) |
| TypeScript typecheck | Passed |
| ESLint | Passed |
| Production frontend build | Passed |
| Rust formatting and compilation | Passed |
| Production dependency audit | 0 vulnerabilities |
| Windows Sandbox installer checks | 85/85 passed |

The Sandbox checks covered a fresh install, an upgrade from a disposable v1.0.1 profile, restart persistence, uninstall/reinstall, downgrade and database restoration. They used disposable profiles and did not modify the owner's live installation or database.

## Known limitations

- The installer is unsigned.
- Screen readers (Narrator/NVDA), real Windows High Contrast, Windows 11 and hardware display scaling above 100% were not tested.
- The installer's WebView2 download step was not exercised; the test Sandbox was supplied with a WebView2 runtime.
- The tray menu and title-bar dragging with a physical OS mouse were not re-run for this release.
- Some multi-part family emoji may render as a grey tile in the bundled emoji font.
- Performance figures in the development record come from a debug build on one slow Windows PC and are not a general benchmark.

## Privacy and local data

Favorites, Recently Used, collections, folders, saved combinations, appearance, theme palette and window preferences are stored locally in SQLite under the Windows application data location for `com.emoxpress.desktop`. Emo-Xpress does not require an account, cloud sync, telemetry or analytics for its current features. The app writes to the clipboard only when the user chooses to copy; it does not read clipboard contents.

See [PRIVACY.md](PRIVACY.md) for details.

## Unicode data and technology

- **Unicode Emoji 18.0:** emoji sequences and qualification.
- **Unicode CLDR 49:** English names and search annotations.
- **Noto Color Emoji 2.057:** bundled emoji rendering font.
- **Application stack:** React, TypeScript, Vite, Tailwind CSS 4, Tauri 2, Rust and SQLite.

The catalogue is generated at development time from version-pinned Unicode and CLDR source files and bundled with the application. Third-party attributions and licences are in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

## Version roadmap

| Version | Main objective |
|---|---|
| **1.0** | Emoji library, search, categories, Favorites, Recently Used and copying |
| **1.0.1** | Desktop UI, window customisation, typography and branding refinement |
| **1.1.0** | Personal collections, folders, custom combinations and themes |
| **1.2** | Global shortcut, floating picker and clipboard manager |
| **2.0** | AI expression engine and contextual recommendations |
| **2.1** | Kaomoji, symbols, stickers and GIF collections |
| **3.0** | Advanced analytics, synchronization and cloud backup |

## Source availability

This is a **distribution-only public repository**. It contains public-facing documentation, release information, checksums, installers when published, and third-party distribution notices. Application source code and the private append-only development record are not published here.

No open-source licence is granted to the Emo-Xpress application source or original application artwork by this repository. Third-party materials remain subject to their respective licences, as described in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

---

**Emo-Xpress** · Every emotion. One expression.
