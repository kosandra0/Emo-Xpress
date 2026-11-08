# Emo-Xpress 1.1.1 — Release Notes

**Windows x64 · NSIS installer · Local-first desktop application**

Emo-Xpress 1.1.1 refines the personal emoji workspace introduced in v1.1.0. This update focuses on responsive layouts, update history, more expressive application themes, independently customisable emoji labels and refreshed branding.

## Installer details

| Item | Value |
|---|---|
| File | `Emo-Xpress_1.1.1_x64-setup.exe` |
| Architecture | Windows x64 |
| Size | 4,494,821 bytes (4.29 MiB) |
| SHA-256 | `ca1a7e72fbc31f99bf37b872630c942f4e564da22942c1ef0e20eb8ab3d79457` |
| Code signing | Unsigned |

The installer is not code-signed. Windows SmartScreen may display a warning. Verify the SHA-256 before running the downloaded installer. The interactive SmartScreen prompt was not observed during the silent Sandbox installation checks.

## What's new

### Responsive Settings and About
Settings and About now adapt to the available content width when the window is resized or maximised. Cards, theme previews, information sections, text and controls rearrange at narrower widths instead of remaining constrained to a narrow fixed column.

### Developer attribution
The About page now includes **kosandra0 (musafir)** and a link to [https://github.com/kosandra0](https://github.com/kosandra0), with a copy-link fallback.

### Update Logs
A new sidebar destination below About provides offline update history. Users can browse dates with recorded entries, move between dates and read detailed chronological release and development updates. Historical timestamps are shown only where recorded; missing times are not invented.

### Eighteen application themes
The eight original themes remain available: Default, Aurora, Cyberpunk, Ocean, Emerald, Sunset, Rose and Violet Dreams.

Ten new palettes are added:
- Sakura Mist
- Tranquil Sky
- Lavender Haze
- Forest Sanctuary
- Arctic Serenity
- Desert Dusk
- Moonlit Pearl
- Coastal Breeze
- Peach Blossom
- Amethyst Calm

The palette system now influences the wider application surface system, including backgrounds, sidebar, headers, cards, borders, controls and feedback surfaces. Dark, Light and System remain independent of palette choice.

### Ten Emoji Name Styles
Users can independently customise the names displayed beneath emoji cards:
1. Monochrome
2. Violet Mist
3. Glacier
4. Mint Leaf
5. Rose Petal
6. Coral Peach
7. Amber Gold
8. Deep Ocean
9. Pistachio Pastel
10. Bold Focus

These styles affect emoji-card labels only. They do not change emoji glyphs, Unicode sequences, search data, collection names or general interface typography.

### Updated branding
The application now uses the supplied v1.1.1 logo artwork in the relevant application and Windows icon assets. The version badge remains separate from the artwork.

## Preserved functionality

The release retains the 3,963-entry Unicode Emoji 18.0 catalogue, CLDR 49 annotations, nine categories, search, Favorites, Recently Used, exact Unicode clipboard copying, personal collections, folders, custom combinations, Saved Combinations, custom interface fonts, sidebar behaviour, system tray, close behaviour, window controls and corner-radius preference.

## Upgrade notes

The v1.1.1 Sandbox upgrade from v1.1.0 did not apply a new database migration. Existing data and preferences were preserved in the disposable upgrade test.

Before installing on your own PC:
1. Quit Emo-Xpress completely, including its system-tray instance.
2. Create a fresh backup of `%APPDATA%\com.emoxpress.desktop\emoxpress.db`.
3. Keep matching `emoxpress.db-wal` and `emoxpress.db-shm` files with the backup if present.
4. Install v1.1.1 over the existing installation.
5. Launch the app and verify your collections, folders, combinations, Favorites, Recently Used and preferences.

Do not open a database already migrated to v1.1.0 with v1.0.1. Version 1.0.1 cannot open the v1.1.0 database schema.

## Verification results

The final development report records:
- 2,815 frontend tests passed across 35 files.
- 4 Rust tests passed.
- TypeScript typecheck and ESLint passed.
- Unicode catalogue validation passed.
- Production build passed.
- Rust formatting and compilation checks passed.
- Production dependency audit reported 0 vulnerabilities.
- 126/126 Windows Sandbox checks passed, covering fresh installation, upgrade, restart/persistence, uninstall/reinstall, downgrade and restoration.
- Native Windows checks covered responsive layouts, themes, Emoji Name Styles, Update Logs, developer attribution, clipboard copying and branding.

These results are from the recorded test sessions; they are not a claim that every Windows version, hardware scaling factor or accessibility technology was tested.

## Known limitations

- Installer is unsigned and may trigger SmartScreen.
- Windows 11, screen readers, a real Windows High Contrast session and display scaling above 100% were not tested.
- The installer WebView2 download step was not tested online; the Sandbox was offline and supplied with the runtime.
- Interactive SmartScreen behaviour was not observed during silent tests.
- Some OS-level title-bar and tray interactions were not re-run for this release.
- The original logo artwork is 226 × 226, so larger generated renditions may appear slightly soft.

## Publication status

This document is prepared for the owner's v1.1.1 GitHub Release. The installer binary is not stored in the Git repository; the owner will upload it as the release asset.
