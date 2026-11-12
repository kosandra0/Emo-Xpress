# Emo-Xpress 2.1.1 — release notes

Windows 10/11 desktop app. Everything stays on your PC. There is no account, no analytics and no network request unless you switch on the optional AI assistance and press its button. Version 2.1.1 adds no network use.

## What changed

- **The Quick Picker stays open.** Choosing an emoji no longer closes it, in any tab. Close it with Escape or a click outside.
- **The Quick Picker remembers its tab.** Reopen it with the shortcut and the tab you used last (for example Travel) is shown.
- **Insert into the previous app keeps the picker open.** Several emojis can be typed in a row. If focus cannot be returned to the picker, it closes.
- **New Settings switch: "Also copy to the clipboard"** (Settings → Quick Picker, shown with "Insert into the previous app"). Off by default. When on, the chosen emoji is copied as well as typed.
- **Settings reach the Quick Picker straight away.** Before, a change to the insert/copy choice or the copy switch needed a restart.
- **New application icon** ("Neon Smiling Planet") for the executable, installer, shortcuts and taskbar. The icon inside the window is unchanged.
- Update Logs entry for 2.1.1.

Full list: `CHANGELOG.md`, section 2.1.1.

## Files

| File | Size | SHA-256 |
|---|---|---|
| `Emo-Xpress_2.1.1_x64-setup.exe` (installer) | 4,730,807 bytes (4.51 MiB) | `49b659cf32e01ad1f95006ecacc6257f9c9280fea31e6a7c68342d04ba3fbefa` |
| `Emo-Xpress_2.1.1_windows-x64_standalone.exe` (no installer) | 7,874,048 bytes | `2bbfb46f3ade14964484251e8c07c7e4341037494b9338814b94f5049ad9c5c2` |

Check a download with PowerShell: `Get-FileHash .\Emo-Xpress_2.1.1_x64-setup.exe`.

The standalone executable runs without installing. It is not registered with Windows (no Start Menu entry, uninstaller or upgrade path).

**Not signed.** Windows may show "Windows protected your PC". Check the SHA-256 above, then choose **More info** and **Run anyway**.

## Upgrading from 2.1.0

- No database migration (still `0001` and `0002`). Your favorites, Recently Used, collections, folders and combinations carry over.
- One setting row is added (`quick_picker_copy_also`). Version 2.1.0 ignores it.
- Install over 2.1.0 with the installer, or run the standalone file.

## Testing

- **Owner's manual test (reported):** the owner confirmed the Quick Picker fixes and the copy setting on their PC before this release.
- **Automated (this build):** `cargo test`: 22 of 22 passed. Frontend suite: see the result line in `CHANGELOG.md`.
- **Not run by the build PC:** no installer test on a second machine, and no check of icon appearance on the Start Menu or taskbar in a clean session.

## Known issues and open items

- **RUSTSEC-2026-0459** (SQLite 3.46.0 via `tauri-plugin-sql`): still open. Documented in `SECURITY-ADVISORIES_v2.1.0.md`. A database-layer upgrade is needed to fix it; it was not made in this release.
