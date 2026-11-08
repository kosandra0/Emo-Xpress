# Emo-Xpress

<h1 align="center">Emo-Xpress</h1>
<p align="center"><strong>Every emotion. One expression.</strong></p>
<p align="center">A personal emoji hub for Windows · Unicode Emoji 18.0 · CLDR 49</p>

<p align="center">
  <a href="https://github.com/kosandra0/Emo-Xpress/releases">GitHub Releases</a> ·
  <a href="CHANGELOG.md">Changelog</a> ·
  <a href="RELEASE_NOTES_v1.1.1.md">v1.1.1 release notes</a> ·
  <a href="THIRD_PARTY_NOTICES.md">Third-party notices</a> ·
  <a href="PRIVACY.md">Privacy</a>
</p>

---

## Current version: 1.1.1

**The v1.1.1 Windows x64 installer has been built and verified in a disposable Windows Sandbox. The owner has not yet published the GitHub Release or uploaded the installer.** Check the [Releases page](https://github.com/kosandra0/Emo-Xpress/releases) for public availability.

Emo-Xpress is a local-first Windows desktop emoji library and personal organiser. Browse and search the Unicode catalogue, organise personal collections, build reusable emoji expressions, and customise the interface.

## Emoji library

- 3,963 fully-qualified Unicode Emoji 18.0 entries.
- English names and search annotations from Unicode CLDR 49.
- Nine standard categories and local ranked search.
- Persistent Favorites and Recently Used history (up to 100 unique emoji).
- Exact Unicode clipboard copying, including flags, keycaps, skin-tone modifiers, tag sequences and ZWJ sequences.

## What's included in v1.1.1

### Personal organisation
- Personal emoji collections with creation, renaming, ordering, searching and deletion.
- Folders for organising collections, with support for unfiled collections.
- Custom emoji combinations with ordered editing, naming, saving and exact one-click copying.
- A dedicated Saved Combinations hub.

### Personalisation
- **18 application colour themes:** Default, Aurora, Cyberpunk, Ocean, Emerald, Sunset, Rose, Violet Dreams, Sakura Mist, Tranquil Sky, Lavender Haze, Forest Sanctuary, Arctic Serenity, Desert Dusk, Moonlit Pearl, Coastal Breeze, Peach Blossom and Amethyst Calm.
- Independent Dark, Light and System appearance modes.
- **10 Emoji Name Styles:** Monochrome, Violet Mist, Glacier, Mint Leaf, Rose Petal, Coral Peach, Amber Gold, Deep Ocean, Pistachio Pastel and Bold Focus. These styles affect emoji card names, not the emoji glyphs or general interface text.
- Responsive Settings and About pages.
- Developer attribution in About: **kosandra0 (musafir)**, with a link to [github.com/kosandra0](https://github.com/kosandra0).

### Update history and branding
- Offline Update Logs with date navigation and detailed historical entries.
- Updated v1.1.1 application branding and Windows icon assets.
- Larger accessible window-control click targets retained from v1.1.0.

## Preserved functionality

The v1.1.1 release retains the Unicode catalogue, search, categories, Favorites, Recently Used, exact clipboard copy, collections, folders, combinations, saved-combination management, global interface font preference, sidebar collapse, cursor glow, system tray, close behaviour, custom window corner radius and traffic-light controls.

## v1.1.1 installer information

| Item | Value |
|---|---|
| File | `Emo-Xpress_1.1.1_x64-setup.exe` |
| Architecture | Windows x64 |
| Size | 4,494,821 bytes (4.29 MiB) |
| SHA-256 | `ca1a7e72fbc31f99bf37b872630c942f4e564da22942c1ef0e20eb8ab3d79457` |
| Code signing | Unsigned |

The installer binary is intentionally not committed to this repository. The owner will attach it to the v1.1.1 GitHub Release.

### Windows SmartScreen

The installer is unsigned. Windows may display a SmartScreen warning. Verify the downloaded file before running it:

```powershell
Get-FileHash .\Emo-Xpress_1.1.1_x64-setup.exe -Algorithm SHA256
```

Compare the result with the SHA-256 listed above and in [SHA256SUMS.txt](SHA256SUMS.txt). The interactive SmartScreen warning was not observed during the silent Sandbox installation tests.

## Upgrade and database compatibility

The v1.1.1 release was tested upgrading a disposable v1.1.0 installation. No new database migration was applied for v1.1.1; existing user data and settings were preserved in the Sandbox upgrade test.

Before upgrading your own installation:

1. Quit Emo-Xpress completely, including the system-tray instance.
2. Make a fresh backup of `%APPDATA%\com.emoxpress.desktop\emoxpress.db`.
3. If `emoxpress.db-wal` or `emoxpress.db-shm` exists, keep it with the database backup.
4. Install v1.1.1 over the existing application and launch it.
5. Verify your Favorites, Recently Used, collections, folders, combinations and preferences.

Do not open a database that has been migrated to v1.1.0 with the older v1.0.1 application. v1.0.1 cannot read the v1.1.0 schema. The Sandbox tests verified returning from v1.1.1 to v1.1.0, but users should still keep a fresh backup before upgrading.

## Verification summary

The final v1.1.1 development report records:

| Check | Result |
|---|---:|
| Frontend tests | 2,815 passed across 35 files |
| Rust tests | 4 passed |
| TypeScript typecheck | Passed |
| ESLint | Passed |
| Unicode catalogue validation | Passed |
| Production frontend build | Passed |
| Rust formatting and compilation | Passed |
| Production dependency audit | 0 vulnerabilities |
| Windows Sandbox checks | 126/126 passed |

The Sandbox run covered fresh installation, upgrade from a disposable v1.1.0 installation, restart/persistence, uninstall/reinstall, downgrade and restoration. The live application and database were not used for these tests.

## Known limitations

- The installer is unsigned; SmartScreen may warn.
- Windows 11, screen readers, a real Windows High Contrast session and hardware display scaling above 100% were not tested.
- The installer's WebView2 download step was not tested because the Sandbox was offline and supplied with a runtime.
- The interactive SmartScreen experience was not observed because the Sandbox installations were silent.
- Real OS-mouse title-bar dragging and some tray interactions were not re-run for this release.
- Large versions of the logo artwork may appear slightly soft because the supplied source image is 226 × 226.
- Performance observations were made on one Windows development machine and should not be treated as general benchmarks.

## Privacy and local data

Emo-Xpress does not require an account, cloud sync, telemetry or analytics for its current features. Favorites, Recently Used, collections, folders, combinations and preferences are stored locally in SQLite. The app writes to the clipboard only when the user chooses to copy and does not read clipboard contents.

See [PRIVACY.md](PRIVACY.md).

## Technology and third-party data

- React, TypeScript, Vite and Tailwind CSS 4.
- Tauri 2 and Rust.
- SQLite through the Tauri SQL plugin.
- Unicode Emoji 18.0 and CLDR 49.
- Noto Color Emoji 2.057.

See [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) for third-party licences and attribution.

## Version roadmap

| Version | Main objective |
|---|---|
| 1.0 | Emoji library, search, categories, Favorites, Recently Used and copying |
| 1.0.1 | Desktop UI, window customisation, typography and branding refinement |
| 1.1.0 | Personal collections, folders, custom combinations and initial palette themes |
| **1.1.1** | Responsive Settings/About, Update Logs, 18 application themes, 10 Emoji Name Styles and refreshed branding |
| 1.2 | Global shortcut, floating picker and clipboard manager |
| 2.0 | AI expression engine and contextual recommendations |
| 2.1 | Kaomoji, symbols, stickers and GIF collections |
| 3.0 | Advanced analytics, synchronisation and cloud backup |

## Source availability

This is a **distribution-only public repository**. It contains public-facing documentation, release information, checksums, installers when published and third-party distribution notices. Application source code and the private append-only development record are not published here.

No open-source licence is granted to the Emo-Xpress application source or original application artwork by this repository. Third-party materials remain subject to their respective licences, as described in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

---

**Emo-Xpress** · Every emotion. One expression.
