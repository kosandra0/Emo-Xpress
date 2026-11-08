# Emo-Xpress 1.1.0 — release notes

Windows desktop app. Everything stays on your PC: no account, no network calls, no analytics.

## Installer

| | |
|---|---|
| File | `Emo-Xpress_1.1.0_x64-setup.exe` |
| Size | 4,460,811 bytes (4.25 MiB) |
| SHA-256 | `d17e2bc1e6e1bb4008dea80551370c767bafae0cd6cfdc97c273c4717500e008` |
| Installs | per user, into `%LOCALAPPDATA%\Emo-Xpress` |
| Code signing | **not signed** |

**SmartScreen:** because the installer is not code-signed, Windows may show "Windows protected your PC". Choose **More info**, then **Run anyway**. Check the SHA-256 above first (PowerShell: `Get-FileHash .\Emo-Xpress_1.1.0_x64-setup.exe`). The warning is the expected behaviour for an unsigned file; it was not observed in testing because the test installs were silent.

## What's new

- **Personal collections.** Create, rename, reorder and delete your own collections. Add emojis from All Emojis, categories, Favorites or Recently Used with the new *Add to collection* button. Collections have their own search.
- **Folders.** Group collections into folders, move collections between folders, and see unfiled ones. Deleting a folder keeps its collections.
- **Custom combinations.** Build a sequence of up to 32 emojis, save it with a name, edit it later, and copy it exactly as built (no separators). Saved combinations can be placed in any collection.
- **Eight colour themes** (Settings → Theme), independent of Dark / Light. The chosen theme is applied before the first screen is drawn, so there is no flash of the default look.
- **Window controls are easier to hit.** The red / yellow / green controls are now 24 × 24 px click targets (WCAG 2.2 AA). The visible dots are still 13 px.
- All v1.0.1 features are unchanged: browse 3,963 emojis (Unicode 18.0), ranked search, Favorites, Recently Used (100 entries), exact copy, appearance, corner radius, controls position, fonts, sidebar, tray / close behaviour.

## Before you install (important)

The first launch of 1.1.0 upgrades your database (migration `0002`). **The upgrade is one-way:** Emo-Xpress 1.0.1 cannot open an upgraded database. It shows "Favorites are unavailable … Nothing has been deleted" and leaves the file untouched.

1. Quit Emo-Xpress completely (Tray → Exit if it is in the tray).
2. Copy `%APPDATA%\com.emoxpress.desktop\emoxpress.db` (and `emoxpress.db-wal` / `emoxpress.db-shm` if they exist) into a new, dated folder.
3. Install 1.1.0 over the old version. Your Favorites, Recently Used and settings are kept.

## Going back to 1.0.1

1. Quit Emo-Xpress. Keep the upgraded files: copy `emoxpress.db`, `-wal`, `-shm` somewhere safe (you need them to return to 1.1.0).
2. Uninstall 1.1.0. Your data folder is kept by the uninstaller.
3. Install the 1.0.1 installer.
4. Move the three `emoxpress.db*` files in `%APPDATA%\com.emoxpress.desktop` aside **together** (do not delete them), then copy your pre-upgrade backup in as `emoxpress.db`.
5. Start 1.0.1. Anything saved after upgrading (collections, folders, combinations, newer favourites) is not in the old backup; restoring the kept upgraded files brings it back under 1.1.0.

## How it was verified (actual results)

- 1,144 automated tests pass (27 test files), plus Rust tests (3), typecheck, lint, catalogue validation (27/27, 3,963 emojis), production build and `npm audit` (0 vulnerabilities). No dependency, permission or security-policy change since 1.0.1.
- Installer and upgrade tested in a disposable Windows Sandbox profile (never on the developer's own installation): fresh install; disposable 1.0.1 install, upgrade to 1.1.0 in place, restart, uninstall (data preserved), reinstall, downgrade and restore. 85 of 85 checks passed in the final run.
- Verified on the shipped binary: migration 0002, Favorites / Recently Used / settings preserved, exact clipboard copy of single emojis and of a combination, collections, folders, themes, restart persistence, window maximize / restore with mouse and keyboard.

## Known limitations

- Not code-signed (SmartScreen warning, see above).
- Not tested: screen readers (Narrator, NVDA), Windows High Contrast, Windows 11, display scaling above 100%, the WebView2 download step of the installer (the test machine had no network; the runtime was supplied instead), the tray menu and dragging the title bar with a real mouse (not re-run for this release).
- Some multi-part family emojis may still draw as a grey tile in the bundled emoji font.
- Performance figures in the development record come from a debug build on one slow PC.
