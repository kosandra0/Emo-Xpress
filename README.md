# Emo-Xpress

<p align="center">
  <img src="assets/Emo-Xpress_v1.1.1.png" alt="Emo-Xpress v1.1.1 logo" width="192" />
</p>

<h2 align="center">Every emotion. One expression.</h2>

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

The v1.1.1 Windows x64 installer has been built and verified in a disposable Windows Sandbox. **The owner has not yet published the GitHub Release or uploaded the installer.** Check the [Releases page](https://github.com/kosandra0/Emo-Xpress/releases) for public availability.

Emo-Xpress is a local-first Windows desktop emoji library and personal organiser. Browse and search the Unicode catalogue, organise personal collections, build reusable emoji expressions, and customise the interface.

## Emoji library

- 3,963 fully-qualified Unicode Emoji 18.0 entries.
- English names and search annotations from Unicode CLDR 49.
- Nine standard categories and local ranked search.
- Persistent Favorites and Recently Used history (up to 100 unique emoji).
- Exact Unicode clipboard copying, including flags, keycaps, skin-tone modifiers, tag sequences and ZWJ sequences.

## What's new in v1.1.1

### Personalisation
- **18 application themes:** Default, Aurora, Cyberpunk, Ocean, Emerald, Sunset, Rose, Violet Dreams, Sakura Mist, Tranquil Sky, Lavender Haze, Forest Sanctuary, Arctic Serenity, Desert Dusk, Moonlit Pearl, Coastal Breeze, Peach Blossom and Amethyst Calm.
- Every palette styles the wider application surfaces, including backgrounds, ambient lighting, sidebar and header glass, cards, borders, dialogs and feedback messages. Dark, Light and System appearance modes remain independent of the selected palette. The original Default theme is preserved.
- **10 Emoji Name Styles:** Monochrome, Violet Mist, Glacier, Mint Leaf, Rose Petal, Coral Peach, Amber Gold, Deep Ocean, Pistachio Pastel and Bold Focus. These styles affect the names beneath emoji cards only; they do not recolour emoji glyphs or unrelated interface text.

### Navigation and history
- **Update Logs:** an offline history page below About, with date navigation, chronological entries, release and milestone labels, and detailed explanations. Entries without a recorded time are labelled honestly.
- **Responsive Settings and About:** their cards, sections, typography and controls adapt to the available content width, from the minimum window to maximized, with the sidebar expanded or collapsed.

### Developer and branding
- **Developer attribution:** About displays **kosandra0 (musafir)** with a GitHub profile link and a Copy Link fallback. The app opens only the fixed profile URL when the user chooses the link.
- **Updated v1.1.1 logo** in the sidebar, About page and generated Windows icon set.

### Fixes
- Settings sections with multi-word titles now have accessible names.
- The collection emoji picker's search field no longer leaves a large gap above the results.

## Preserved functionality

The v1.1.1 release retains the 3,963-entry Unicode catalogue, CLDR 49 annotations, nine categories, ranked search, Favorites, Recently Used, exact clipboard copy, personal collections, folders, custom combinations, Saved Combinations, Dark / Light / System appearance, interface font choice, sidebar collapse, system tray, close behaviour, custom window corner radius and window controls.

## v1.1.1 installer information

| Item | Value |
|---|---|
| File | `Emo-Xpress_1.1.1_x64-setup.exe` |
| Architecture | Windows x64 |
| Size | 4,494,821 bytes (4.29 MiB) |
| SHA-256 | `ca1a7e72fbc31f99bf37b872630c942f4e564da22942c1ef0e0eb8ab3d379457` |
| Install mode | Per-user, into `%LOCALAPPDATA%\Emo-Xpress` |
| Code signing | Unsigned |

The installer binary is not committed to the Git repository. The owner will attach it to the v1.1.1 GitHub Release.

### Windows SmartScreen

The installer is unsigned, so Windows may display a SmartScreen warning. Verify the downloaded file before running it:

```powershell
Get-FileHash .\Emo-Xpress_1.1.1_x64-setup.exe -Algorithm SHA256
```

Compare the result with the SHA-256 above and in [SHA256SUMS.txt](SHA256SUMS.txt). The interactive SmartScreen warning was not observed during the silent Sandbox installation checks.

## Upgrade notes

There is **no new database migration in v1.1.1**. It uses the v1.1.0 database layout; the selected theme and Emoji Name Style are stored as ordinary `app_settings` values.

Before upgrading an installation you care about:

1. Quit Emo-Xpress completely, including the system-tray instance.
2. Back up `%APPDATA%\com.emoxpress.desktop\emoxpress.db`.
3. Keep matching `emoxpress.db-wal` and `emoxpress.db-shm` files with the backup if they exist.
4. Install v1.1.1 over the existing application.
5. Launch it and verify Favorites, Recently Used, collections, folders, combinations and preferences.

**Upgrading from v1.0.1:** the first launch applies the v1.1.0 migration (`0002`), which is one-way for v1.0.1 compatibility. Version 1.0.1 cannot open a database after migration 0002 has been applied. Keep a pre-upgrade backup if you may need to return to v1.0.1; see the [v1.1.0 release notes](RELEASE_NOTES_v1.1.0.md) for the detailed restoration procedure.

### Returning to v1.1.0

Quit the app and keep a copy of the v1.1.1-used database files. Uninstall v1.1.1 and install v1.1.0. Version 1.1.0 can open the same database but does not recognise the new theme and name-style setting values; it uses its default appearance and leaves the unknown values in the database. Reinstalling v1.1.1 restores those preferences. To return to a database backup from before an upgrade, move the current database, WAL and SHM files aside together and restore the backup.

## Verification summary

The v1.1.1 development record reports:

| Check | Result |
|---|---:|
| Frontend tests | 2,815 passed across 35 files |
| Rust tests | 4 passed |
| TypeScript typecheck | Passed |
| ESLint | Passed |
| Unicode catalogue validation | Passed |
| Production build | Passed |
| Rust formatting and compilation | Passed |
| Production dependency audit | 0 vulnerabilities |
| Windows Sandbox installer checks | 126/126 passed |

The Sandbox tests covered a fresh install, upgrade from a disposable v1.1.0 installation, restart and persistence, uninstall/reinstall, downgrade to v1.1.0 and restoration. Tests used disposable profiles and databases, not the owner's live installation or database.

Native checks covered responsive layouts, developer attribution, Update Logs, themes, Emoji Name Styles, clipboard copying, saved preferences and the updated branding.

## Known limitations

- The installer is unsigned and may trigger SmartScreen.
- Windows 11, screen readers (Narrator/NVDA), a real Windows High Contrast session and hardware display scaling above 100% were not tested.
- The installer's WebView2 download step was not tested online; the Sandbox was offline and supplied with a WebView2 runtime.
- The interactive SmartScreen flow was not observed because Sandbox installs were silent.
- The tray menu and real-mouse title-bar dragging were not re-run for this release.
- The supplied logo artwork is 256 × 256, and the app's largest generated icon renditions may appear slightly soft.
- Some multi-part family emoji may still draw as a grey tile in the bundled emoji font.
- Contrast measurements are not a substitute for a formal accessibility audit; performance figures come from a debug build on one Windows PC.

## Privacy and local data

Emo-Xpress does not require an account, cloud sync, telemetry, analytics or advertising. Favorites, Recently Used, collections, folders, combinations and preferences are stored locally in SQLite. Update Logs are bundled static content. The app writes to the clipboard only when the user chooses to copy and does not read clipboard contents. The GitHub profile link opens the user's default browser only when explicitly clicked.

See [PRIVACY.md](PRIVACY.md).

## Technology and third-party data

- React, TypeScript, Vite and Tailwind CSS 4.
- Tauri 2 and Rust.
- SQLite through the Tauri SQL plugin.
- Unicode Emoji 18.0 and CLDR 49.
- Noto Color Emoji 2.057, bundled under the SIL Open Font License 1.1.

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

<p align="center"><strong>Emo-Xpress · Every emotion. One expression.</strong></p>
