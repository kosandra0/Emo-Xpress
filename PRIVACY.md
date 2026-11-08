# Privacy

**Emo-Xpress 1.1.1 is a local-first Windows desktop application.**

## Information stored locally

Emo-Xpress stores user preferences and user-created content in its local SQLite database under the Windows application data location for application identifier `com.emoxpress.desktop`. The program installation directory and the user database are separate.

Depending on the features used, locally stored information includes:

- Favorites.
- Recently Used emoji history (up to 100 unique entries).
- Personal collection names, ordering and emoji membership.
- Folder names, ordering and collection-to-folder relationships.
- Saved custom combination names and their ordered emoji sequences.
- Appearance preference (System, Light or Dark).
- Selected application colour-theme palette.
- Selected Emoji Name Style (`emoji_name_style` setting).
- Close behaviour (minimize to system tray or exit application).
- Window corner-radius preference.
- Sidebar expanded/collapsed preference.
- Traffic-light window-control position.
- Selected interface font preference.

Update Logs are bundled static content. They are not personal data and do not require a database or network connection.

The application does not require an account or cloud profile to use these features.

## Database migration and backups

Version 1.1.1 introduces no new SQLite migration. It continues to use migrations `0001` and `0002`; the selected application theme and Emoji Name Style are saved as ordinary `app_settings` values.

The first launch of v1.1.0 applies migration `0002`, which adds the data structures used for collections, folders and combinations. **Version 1.0.1 cannot open a database after migration 0002 has been applied.** Back up `emoxpress.db` before upgrading from v1.0.1, and keep matching `emoxpress.db-wal` and `emoxpress.db-shm` files with the backup if they exist.

Version 1.1.0 can open a database used by v1.1.1, but it does not recognise the newer theme and Emoji Name Style values. It uses its own default appearance and leaves those setting rows untouched. See the release notes for the upgrade and rollback procedure.

## Clipboard

Emo-Xpress writes an emoji or saved combination to the Windows clipboard only when the user chooses to copy it. A custom combination is copied as its ordered sequence, with no inserted separators.

The application has clipboard write permission for this feature. It does **not** read clipboard contents, monitor clipboard changes, maintain a system-wide clipboard history, or automatically paste into other applications. Copying a combination does not add it to Recently Used.

## Fonts and emoji rendering

The typography selector uses fonts installed on the Windows computer. Emo-Xpress does not download selectable interface fonts. The bundled Noto Color Emoji font is used for emoji rendering; the chosen interface font and Emoji Name Style do not alter the Unicode sequence copied to the clipboard.

## Network, accounts and tracking

Core application features use the bundled catalogue and local database. Update Logs are bundled. Emo-Xpress does not require an account, cloud synchronization, an AI provider, telemetry, analytics or advertising, and the app makes no background network requests for its core features.

The About page includes an optional GitHub profile link. Only when the user chooses that link does Emo-Xpress open the fixed `https://github.com/kosandra0` address in the default browser. The browser may then access GitHub according to the user's browser and network settings. The Copy Link action writes the URL to the clipboard; it does not open a page.

The installer may need the WebView2 runtime. The v1.1.1 Sandbox verification supplied a runtime to the test environment; the installer's own online WebView2 download step was not exercised.

## Removing local data

The application database is stored outside the program installation directory under the Windows application data location for `com.emoxpress.desktop`. Back up the database before manually removing it. Uninstalling the application and deleting its user data are separate actions; consult the release notes before removing database files.
