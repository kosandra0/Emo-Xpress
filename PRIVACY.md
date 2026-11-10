# Privacy

**Emo-Xpress 2.0.0 is a local-first Windows desktop application.** The offline catalogue, browsing, collections and local Expression Studio do not require an account, cloud service or AI subscription.

## Data stored locally

Emo-Xpress stores user data in its local SQLite database under the Windows application data location for `com.emoxpress.desktop`. Depending on features used, this includes Favorites, Recently Used emoji, collections, folders, saved combinations, appearance and other application preferences, expression presets, optional history and local feedback.

Expression history is **off by default**. Raw prompt text is not retained unless the user separately enables that option. History and personalisation can be cleared from the application. No account, cloud profile, analytics or telemetry is required.

## Clipboard

Emo-Xpress writes emoji or a saved combination to the Windows clipboard only when the user chooses to copy it. It does not read clipboard contents, monitor clipboard changes or automatically paste into other applications.

## Optional AI assistance and network requests

Optional Anthropic AI assistance is **off by default**. The application makes no provider request for ordinary offline use. A request occurs only after the user enables AI assistance, reviews the consent disclosure and explicitly selects **Improve with AI**.

When invoked:
- The only provider host is `api.anthropic.com`, fixed at build time and contacted over HTTPS from the Rust side.
- The request may include the prompt text for that action, selected mode, context and tone settings, and a bounded list of candidate emoji IDs and names selected locally.
- Favorites, Recently Used, collections, saved combinations, history, clipboard contents and local feedback are not sent by default.
- The provider re-ranks candidates already selected by the offline engine; it does not invent catalogue entries.
- The response is schema-validated. Returned IDs must belong to the supplied candidate list, and emoji text is rebuilt locally.
- If the request fails, the application keeps or returns to local suggestions.

Your Anthropic API key is stored in Windows Credential Manager or, if persistent credential storage is unavailable, in memory for the current session only. The key is never returned to JavaScript and is not written to the app database or logs.

Using your own provider API key may incur charges under that provider's pricing and terms. The optional provider was not live-tested during the v2.0.0 release because no API key was available; automated mock-provider tests passed.

## Database and upgrades

Version 2.0.0 adds no SQLite migration beyond the existing migrations `0001` and `0002`. New expression preferences are stored as bounded, versioned values in the existing `app_settings` table. Back up the database before upgrading. The v2.0.0 upgrade and 1.1.1 rollback compatibility path were checked in Windows Sandbox.

## Removing local data and credentials

Uninstalling the program and deleting its user data are separate actions. User data is stored outside the installation directory under `%APPDATA%\com.emoxpress.desktop`. Back up the database before manually removing it.

To remove a saved AI key, use the application's **Remove key** control in AI assistance settings, or remove the `Emo-Xpress/anthropic-api-key` entry from Windows Credential Manager.
