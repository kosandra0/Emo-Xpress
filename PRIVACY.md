# Privacy

**Emo-Xpress 1.1.0 is a local-first Windows desktop application.**

## Information stored locally

Emo-Xpress stores user preferences and user-created content in its local SQLite database under the Windows application data location for application identifier `com.emoxpress.desktop`. The program installation directory and the user database are separate.

Depending on the features used, locally stored information includes:

- Favorites.
- Recently Used emoji history (up to 100 unique entries).
- Personal collection names, ordering and emoji membership.
- Folder names, ordering and collection-to-folder relationships.
- Saved custom combination names and their ordered emoji sequences.
- Appearance preference (System, Light or Dark).
- Selected colour-theme palette.
- Close behaviour (minimize to system tray or exit application).
- Window corner-radius preference.
- Sidebar expanded/collapsed preference.
- Traffic-light window-control position.
- Selected interface font preference.

The application does not require an account or cloud profile to use these features.

## Database migration and backups

The first launch of v1.1.0 applies SQLite migration `0002`, which adds the data structures used for collections, folders and combinations. Existing v1.0.1 Favorites, Recently Used and settings are preserved by the tested upgrade.

**The database migration is one-way for application compatibility:** v1.0.1 cannot open a database after migration 0002 has been applied. Back up `emoxpress.db` before upgrading. Keep matching `emoxpress.db-wal` and `emoxpress.db-shm` files with the backup if they exist. The release notes document the downgrade and restore procedure.

## Clipboard

Emo-Xpress writes an emoji or saved combination to the Windows clipboard only when the user chooses to copy it. A custom combination is copied as its ordered sequence, with no inserted separators.

The application has clipboard write permission for this feature. It does **not** read clipboard contents, monitor clipboard changes, maintain a system-wide clipboard history, or automatically paste into other applications. Copying a combination does not add it to Recently Used.

## Fonts and emoji rendering

The typography selector uses fonts installed on the Windows computer. Emo-Xpress does not download selectable interface fonts. The bundled Noto Color Emoji font is used for emoji rendering; the chosen interface font does not alter the Unicode sequence copied to the clipboard.

## Network, accounts and tracking

Core application features are designed to use the bundled catalogue and local database. Emo-Xpress does not require an account, cloud synchronization, AI provider, telemetry, analytics or advertising.

The installer may need the WebView2 runtime. The v1.1.0 Sandbox verification supplied a runtime to the test environment; the installer's own WebView2 download step was not exercised in that test.

## Removing local data

The application database is stored outside the program installation directory under the Windows application data location for `com.emoxpress.desktop`. Back up the database before manually removing it. Uninstalling the application and deleting its user data are separate actions; consult the release notes before removing database files.
