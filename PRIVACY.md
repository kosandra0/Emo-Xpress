# Privacy

**Emo-Xpress 1.0.0 is designed as a local-first Windows application.**

## What stays on your device

The following information is stored locally by the application:

- Favorites.
- Recently Used emoji history (up to 100 unique entries).
- Appearance preference (System, Light, or Dark).

The application uses a local SQLite database in its Tauri application data location. On Windows, the data directory is associated with the application identifier `com.emoxpress.desktop`.

The NSIS uninstaller was tested to keep the user's application data when removing the program.

## Clipboard

Emo-Xpress writes the selected emoji sequence to the Windows clipboard when you choose to copy it.

Version 1.0.0 does **not** read clipboard contents, monitor clipboard changes, maintain a system-wide clipboard history, or automatically paste into other applications.

## Network, accounts, and tracking

The v1.0.0 core features do not require:

- An account or sign-in.
- A cloud service or synchronization.
- An AI provider.
- Telemetry or analytics.
- Advertising.
- Background network requests.

The Unicode/CLDR catalogue and Noto emoji font needed by the application are bundled with the app.

## Removing local data

Uninstalling Emo-Xpress does not remove the saved application data. If you choose to remove it yourself, close the application first and back up anything you want to keep. The data is stored under the Windows application data location for `com.emoxpress.desktop`.

