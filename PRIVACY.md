# Privacy

**Emo-Xpress 1.0.1 is designed as a local-first Windows application.**

## What stays on your device

The following information is stored locally by the application:

- Favorites.
- Recently Used emoji history (up to 100 unique entries).
- Appearance preference (System, Light, or Dark).
- Close behaviour (minimize to system tray or exit application).
- Window corner-radius preference.
- Sidebar expanded or collapsed preference.
- Traffic-light window-control position (left or right).
- Selected interface font preference.

The application uses a local SQLite database in its Tauri application data location. On Windows, the data directory is associated with the application identifier `com.emoxpress.desktop`.

The v1.0.1 update retained the existing application identifier and database location. The development verification report records a database backup whose SHA-256 matched before and after the update. The NSIS uninstaller is intended to keep user data when removing the program.

## Fonts

The typography selector uses fonts installed on the Windows computer. Emo-Xpress does not download fonts from remote services. A font that is not installed is shown as unavailable and is not silently applied. The selected font preference is stored locally.

The interface font preference does not change the Unicode emoji sequence or the emoji font fallback used to render emoji.

## Clipboard

Emo-Xpress writes the selected emoji sequence to the Windows clipboard when you choose to copy it.

Version 1.0.1 does **not** read clipboard contents, monitor clipboard changes, maintain a system-wide clipboard history, or automatically paste into other applications.

## Network, accounts, and tracking

The v1.0.1 core features do not require:

- An account or sign-in.
- A cloud service or synchronization.
- An AI provider.
- Telemetry or analytics.
- Advertising.
- Remote font downloads.
- Background network requests for normal app use.

The Unicode/CLDR catalogue and Noto emoji font needed by the application are bundled with the app.

## Removing local data

Uninstalling Emo-Xpress is intended not to remove the saved application data. If you choose to remove it yourself, close the application first and back up anything you want to keep. The data is stored under the Windows application data location for `com.emoxpress.desktop`.
