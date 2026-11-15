# Emo-Xpress 2.1.3

## Statistics and start at sign-in

- **Statistics page (new, in the sidebar):** see how many emojis you have used, how many different ones, your most used emoji, and a table of every emoji with how many times you used it and when you last used it.
- **Kaomojis:** the Statistics page shows "Coming soon" for kaomojis, because Emo-Xpress does not have kaomojis yet.
- **Start at sign-in (new, in Settings > Startup):** one switch, off by default. When on, Emo-Xpress starts minimised when you sign in to Windows. It applies to your Windows account only and needs no administrator rights.
- **New application icon:** used for the executable, installer, shortcuts and taskbar.

### Your data

- A new table stores the statistics. It starts from your current Recently Used history, so existing usage is counted.
- Favorites, Recently Used, collections and settings are unchanged.
- Clearing Recently Used does not clear the statistics.

### Downloads

| File | Use |
|---|---|
| `Emo-Xpress_2.1.3_x64-setup.exe` | Installer (per-user, recommended) |
| `Emo-Xpress_2.1.3_windows-x64_standalone.exe` | Portable executable, no installation |
| `SHA256SUMS.txt` | Checksums |

Not code-signed. Windows SmartScreen may show a warning for an unsigned program.

### Known limits

- The start-at-sign-in switch was added and its registry entry is written by the app, but it was not yet tested by switching it on and signing in again on the test PC.
- The static application icon is generated from the supplied image. The animated version is used only on the website.
- Downgrading to 2.1.2 after this version has been run once has not been tested.
