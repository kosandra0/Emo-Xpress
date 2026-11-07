# Privacy

**Emo-Xpress 1.0.1 is designed as a local-first Windows application.**

## Information stored locally

The application stores the following information in its local SQLite database:

- Favorites.
- Recently Used emoji history (up to 100 unique entries).
- Appearance preference (System, Light, or Dark).
- Close behaviour (minimize to system tray or exit application).
- Window corner-radius preference.
- Sidebar expanded or collapsed preference.
- Traffic-light window-control position (left or right).
- Selected interface font preference.

The Windows application data location is associated with the application identifier `com.emoxpress.desktop`. The program installation folder and the user database are separate.

## v1.0.1 data preservation

The v1.0.1 installer was installed over the existing application in the development environment. Before installation, the existing database was backed up. The final development record reports that the database file's SHA-256 was identical before and after the installer update and subsequent read-only inspection.

The final refinement tested writes for the newly added sidebar, traffic-light-position, and font settings on an isolated test application identifier. Those settings were not written to the owner's production database during that test round. The owner's existing Favorites, Recently Used, appearance, close behaviour, and corner-radius data were left unchanged.

## Fonts

The typography selector uses fonts installed on the Windows computer. Emo-Xpress does not download fonts from remote services or bundle the selectable Windows interface fonts. A font that is not installed is shown as unavailable and is not silently applied. The selected font preference is stored locally.

The interface font preference does not change the Unicode emoji sequence or replace the emoji font used to render emoji.

## Clipboard

Emo-Xpress writes the selected emoji sequence to the Windows clipboard when the user chooses to copy it.

The application has clipboard write permission for this feature. It does **not** read clipboard contents, monitor clipboard changes, maintain a system-wide clipboard history, or automatically paste into other applications.

## Network, accounts, and tracking

Emo-Xpress does not require an account, sign-in, cloud service, synchronization service, AI provider, telemetry, analytics, or advertising for its current core features.

The Unicode/CLDR catalogue and Noto emoji font needed by the application are bundled with the app. Fonts selected in Typography settings are sourced from the local Windows installation, not downloaded.

The final production bundle was checked with its configured content security policy; the development record reports zero external requests during that production-bundle check. A separate operating-system-level test with the PC disconnected from the network was not recorded.

## Removing local data

The application database is stored outside the program installation directory under the Windows application data location for `com.emoxpress.desktop`. Back up the database before manually removing it. The v1.0.1 final refinement round did not perform an uninstall test.
