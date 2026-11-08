# Emo-Xpress 1.1.1 — release notes

Windows 10/11 desktop app. Everything stays on your PC: no account, no network calls, no analytics.

## Installer

| | |
|---|---|
| File | `Emo-Xpress_1.1.1_x64-setup.exe` |
| Size | 4,494,821 bytes (4.29 MiB) |
| SHA-256 | `ca1a7e72fbc31f99bf37b872630c942f4e564da22942c1ef0e0eb8ab3d379457` |
| Architecture | Windows x64 |
| Installs | per user, into `%LOCALAPPDATA%\Emo-Xpress` |
| Code signing | **not signed** |

**SmartScreen:** because the installer is not code-signed, Windows may show "Windows protected your PC". Choose **More info**, then **Run anyway**. Check the SHA-256 above first (PowerShell: `Get-FileHash .\Emo-Xpress_1.1.1_x64-setup.exe`). The warning is the expected behaviour for an unsigned file; it was not observed in testing because the test installs were silent.

## What's new

- **Update Logs.** A new page directly below About shows the history of Emo-Xpress by date: pick a day, step to the older or newer day, and open detailed explanations for each update. Releases are marked apart from development milestones, an entry without a recorded time says so, and everything is built in (works offline).
- **Eighteen colour themes.** Ten new calm themes (Sakura Mist, Tranquil Sky, Lavender Haze, Forest Sanctuary, Arctic Serenity, Desert Dusk, Moonlit Pearl, Coastal Breeze, Peach Blossom, Amethyst Calm) join the original eight. A theme now restyles the whole window — background and ambient light, sidebar and header glass, cards, borders, dialogs and messages — in both Dark and Light. Default keeps its original look. Settings previews are painted with each theme's real colours.
- **Ten Emoji Name Styles.** Choose the colour of the names printed under emoji cards: Monochrome (the original look), Violet Mist, Glacier, Mint Leaf, Rose Petal, Coral Peach, Amber Gold, Deep Ocean, Pistachio Pastel and Bold Focus. Previews use real emoji cards, and *Reset to Default* returns to the original look. Only the emoji names change — not the emoji themselves, collection, folder or combination names, or other text. Each style adapts to your theme so names stay readable.
- **Developer credit.** About shows "Developed by kosandra0 (musafir)" with the GitHub profile link. The link opens in your default browser only when you choose it; *Copy link* is a fallback. The app can open only that one fixed address.
- **Responsive Settings and About.** Both pages adapt to the window width, from the smallest window to maximized, with the sidebar expanded or collapsed.
- **New logo** in the sidebar, About page, window, taskbar, program file and installer. The version badge next to the name is still drawn by the app.
- **Fixes:** Settings sections with several-word titles now have accessible names for screen readers; the search field in the collection emoji picker no longer leaves a large gap above the results.
- Everything from 1.1.0 is unchanged: 3,963 emojis (Unicode 18.0), ranked search, Favorites, Recently Used (100), exact copy, collections, folders, combinations, appearance, fonts, tray and close behaviour, corner radius, window controls.

## Before you install

**There is no new database migration in 1.1.1.** Your database keeps the 1.1.0 layout; the theme and name style are saved as ordinary settings. Even so, take a backup before upgrading an installation you care about:

1. Quit Emo-Xpress completely (Tray → Exit if it is in the tray).
2. Copy `%APPDATA%\com.emoxpress.desktop\emoxpress.db` (and `emoxpress.db-wal` / `emoxpress.db-shm` if they exist) into a new, dated folder.
3. Install 1.1.1 over the old version. Your Favorites, Recently Used, collections, folders, combinations and settings are kept.

**Upgrading from 1.0.1:** the first launch applies the 1.1.0 migration (`0002`), which is one-way — 1.0.1 cannot open a migrated database (it shows a storage notice and changes nothing). The backup above is what lets you go back; see the 1.1.0 release notes for the exact steps.

## Going back to 1.1.0

1. Quit Emo-Xpress. Copy `emoxpress.db` (and `-wal` / `-shm`) somewhere safe.
2. Uninstall 1.1.1 (your data folder is kept) and install the 1.1.0 installer.
3. 1.1.0 opens the same database. It does not know the new theme or name style, so it shows its own default look; the two saved settings stay in the database and take effect again if you reinstall 1.1.1. To return to a database from before the upgrade, move the three `emoxpress.db*` files aside together and copy your backup in as `emoxpress.db`.

## How it was verified (actual results)

- 2,815 automated tests pass (35 test files), plus Rust tests (4), typecheck, lint, catalogue validation (3,963 emojis), production build and `npm audit` (0 vulnerabilities). No dependency, permission, capability or security-policy change since 1.1.0, and no new database migration.
- The real application was tested on an isolated test identifier with a disposable database: layouts at nine window sizes plus maximized with the sidebar expanded and collapsed (265 checks), the developer card (27), Update Logs (42), all 18 themes in Dark and Light (54), all ten name styles (61), clipboard copy, window-control sizes, link legibility in all 36 theme and appearance pairs, and no console errors.
- Contrast: every theme (1,811 checks) and all 360 theme × appearance × name-style combinations pass the 4.5:1 text minimum. Measured on rendered pixels, the worst case was 5.15:1 for name text and 6.27:1 for the About link.
- The installer was tested in a disposable Windows Sandbox profile (never on the developer's own installation): a fresh 1.1.1 install (42 checks) and a disposable 1.1.0 install, in-place upgrade to 1.1.1, restart, uninstall (data preserved), reinstall, downgrade to 1.1.0, re-upgrade and restore of the pre-upgrade backup (84 checks). **126 of 126 checks passed** in the final run.
- Verified on the installed program: no new migration (still migrations 1 and 2), all 1.1.0 data preserved through the upgrade, exact clipboard copy, Copy link, Update Logs offline, 18 themes and 10 name styles offered, the saved theme and name style restored after restart, the new logo and version 1.1.1 in the window, and the new icon on the installed executable and the installer.

## Known limitations

- Not code-signed (SmartScreen warning, see above).
- Not tested: screen readers (Narrator, NVDA), a real Windows High Contrast session (forced-colours, reduced-motion, reduced-transparency and increased-contrast were checked only through browser-engine emulation), Windows 11, display scaling above 100%, the installer's WebView2 download step (the test sandbox had no network; the runtime was supplied instead), the tray menu and dragging the title bar with a real mouse.
- The new logo's source artwork is 226 pixels wide, so the largest icon sizes are enlarged from it and can look slightly soft when shown very large.
- Some multi-part family emojis may still draw as a grey tile in the bundled emoji font.
- Contrast figures are measured on colour values and on rendered pixels, not certified by an accessibility audit. Performance figures come from a debug build on one slow PC.
