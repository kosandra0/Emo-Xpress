# Emo-Xpress 2.1.0 — release notes

Windows 10/11 desktop app. Everything stays on your PC. There is no account, no analytics and no network request unless you switch on the optional AI assistance and press its button. Version 2.1.0 adds no network use.

## Downloads

| File | Size | SHA-256 |
|---|---:|---|
| `Emo-Xpress_2.1.0_x64-setup.exe` (recommended installer) | 4,756,819 bytes | `F3FB00B27F2EE6C4F3A64D2F69C7D61E3C20B38C57E3C3F0C6A5111BAFC0084C` |
| `Emo-Xpress_2.1.0_windows-x64_standalone.exe` (runs without installing) | 7,885,824 bytes | `9AEF7C025647DE77D29200EBCB8F70ED49C91B9237349690005AAF4789F61BA6` |

Verify a download before running it:

```powershell
Get-FileHash .\Emo-Xpress_2.1.0_x64-setup.exe -Algorithm SHA256
```

Or compare every file at once with `SHA256SUMS.txt`.

Both files are **not code-signed**. Windows may show "Windows protected your PC". Check the SHA-256 above, then choose **More info** and **Run anyway**.

The standalone executable is not registered with Windows: it has no Start Menu entry, no uninstaller and no upgrade path. Use the installer for a normal installation.

## What's new in 2.1.0

- **Quick Picker, from anywhere.** Press `Ctrl+Shift+E` (the default) to open a small floating emoji picker over the window you are using. Search by name or meaning, move with the arrow keys, press Enter to choose, and press Escape to clear the search or close the picker. The picker closes when it loses focus.
- **Insert or copy.** Settings → Quick Picker chooses between "Insert into the window I was using" (the default) and "Copy to the clipboard only".
  - Insertion types the emoji into the window that was active before the picker opened, and the clipboard is left alone.
  - If that window cannot receive typing (for example, when the picker was opened while Emo-Xpress itself was active), the emoji is copied to the clipboard and the picker says so. Nothing is typed into Emo-Xpress.
- **Custom global hotkey.** Settings → Quick Picker: press a new combination, then Save. Restore default returns to `Ctrl+Shift+E`. Refused: shortcuts without Ctrl or Alt, shortcuts already used by another program, and Windows-reserved combinations (Alt+F4, Alt+Space, Ctrl+C, Ctrl+V, Ctrl+X, Ctrl+Z, Ctrl+Y, Ctrl+A). A refused change never replaces the working shortcut.
- **Background operation and system tray.** The tray menu has "Open Quick Picker" and "Settings". With the tray close option on, closing the main window keeps the hotkey working. Exit from the tray releases the hotkey and closes all windows.
- **Favorites and Recently Used stay current.** Emoji chosen in the Quick Picker are recorded in Recently Used, and the main window re-reads Favorites and Recently Used when it regains focus.
- **Emoji search and categories in the picker.** The picker uses the same 3,963-entry catalogue and categories as the main library.
- **Theme integration.** The picker uses the app's appearance settings (themes and Dark/Light).
- **Windows icon.** The Windows executable and the installer embed the supplied Emo-Xpress icon, and shortcuts use the executable's icon. The in-app logo is unchanged. The appearance of shortcuts, taskbar and Alt+Tab has not been checked on screen (see below).

## Installing or upgrading

- Close Emo-Xpress first.
- Installing 2.1.0 over 2.0.0 upgrades in place. **No database migration is added** (migrations `0001` and `0002` only). Two rows are added to the existing `app_settings` table: `quick_picker_shortcut` and `quick_picker_behavior`. Favorites, Recently Used, collections, folders, combinations and other settings are not changed.
- Application data stays in `%APPDATA%\com.emoxpress.desktop`. Make a copy of that folder before upgrading if you want an extra backup.
- The installer is per user and installs into `%LOCALAPPDATA%\Emo-Xpress`.

Uninstall: Settings → Apps → Emo-Xpress → Uninstall. Your data stays in `%APPDATA%\com.emoxpress.desktop` unless you choose to delete it.

## Testing status

Be clear about what was tested and how:

- **Upgrade on the maintainer's own Windows PC (2026-11-12):** the 2.0.0 database was backed up first (copy verified by SHA-256, read-only row counts recorded). The 2.1.0 installer ran silently over 2.0.0 and exited 0. Emo-Xpress 2.1.0 started and stayed running. The database row counts after the upgrade matched the backup exactly (favorites, Recently Used, settings, migration rows), and the main window showed the saved Favorites.
- **Windows Sandbox (2026-11-12, isolated, synthetic data):** install of 2.0.0, seeded data, upgrade to 2.1.0, and rollback to 2.0.0. Favorites, Recently Used, a setting, a folder and a collection were present after each step.
- **Quick Picker insertion (manual, maintainer):** in Windows Sandbox, the floating Quick Picker appeared and the emoji chosen in it appeared in Windows Notepad. This was a visual observation; the individual checks were not recorded one by one.
- **Automated tests:** see the verification list in `CHANGELOG.md`.

**Not yet confirmed by an independent check** (recommended before you rely on them):
- The custom hotkey on your own PC: change it, confirm the old one stops working, restart and confirm the new one persists.
- Escape, clicking outside, and immediate reopen of the picker.
- Copy-to-clipboard mode, and the clipboard fallback when Emo-Xpress itself is active.
- Tray behaviour: closing the main window with the tray option on, and tray Exit ending the process.
- Dark and Light theme appearance of the picker.
- The icon in the desktop shortcut, Start Menu, taskbar, Alt+Tab and the uninstaller. The embedded icon was verified by inspecting the executable and installer, but the appearance in those places was not checked on screen.

## Known limitations

- **Insertion into other applications** was observed working in Windows Notepad. Other applications were not tested. Windows input isolation is expected to block typing into administrator-elevated windows; in that case the emoji should be copied to the clipboard instead. This expectation has not been tested.
- **Dependency advisory RUSTSEC-2026-0459 is open.** The SQLite library inside the shipped build (SQLite 3.46.0 via `tauri-plugin-sql`) has a published advisory. The fix requires a newer `sqlx`/plugin, a database-layer upgrade, which was **not** made in 2.1.0 because it needs a separate migration test. See `SECURITY-ADVISORIES_v2.1.0.md`.
- RUSTSEC-2023-0071 (`rsa`) is recorded in the lock file but is not compiled into the Windows build.
- The emoji catalogue (about 1.27 MB, about 100 kB gzip) is loaded as one lazily loaded chunk.
- The installer and standalone executable are not code-signed.
