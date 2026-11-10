# Emo-Xpress 2.0.0 — release notes

Windows 10/11 desktop app. Core features run locally and offline. There is no account, analytics or telemetry.

## Installer

| Item | Value |
|---|---|
| File | `Emo-Xpress_2.0.0_x64-setup.exe` |
| Size | 4,719,856 bytes |
| SHA-256 | `09bad3c988b0763f971f0172c0d453582925920cacebb66c99851952ed8eb972f` |
| Architecture | Windows x64 |
| Code signing | Unsigned |

The installer is not code-signed. Verify its SHA-256 before running; Windows SmartScreen may show a warning.

## What's new

- **Expression Studio:** six modes, 12 contexts plus custom context, five tone controls and three strict output styles: Minimal (1–2 emoji), Balanced (3–4) and Expressive (5–7). Each suggestion explains why it fits and preserves exact Unicode.
- **Contextual suggestions:** optional Ideas panels for the library, collections and saved combinations, and “Suggest by meaning” from a no-results search. Suggestions are off by default.
- **Personalisation:** local defaults, up to 20 presets, optional history (off by default), separately consented raw-prompt retention, feedback, favourite patterns and reset.
- **Optional Anthropic assistance:** off by default; requires explicit consent, a user action and the user's own API key. It can re-rank candidates selected by the offline engine. Failure falls back to local suggestions.
- **New v2.0.0 branding** across the application and Windows icon set.

## Compatibility

Upgrading from 1.x preserves Favorites, Recently Used, collections, folders, combinations and settings. Version 2.0.0 adds no SQLite migration; new settings are stored as bounded versioned values in the existing `app_settings` table. Upgrade and 1.1.1 rollback compatibility were checked in Windows Sandbox.

## Verification

- 3,300 frontend tests passed across 58 files; 19 Rust tests passed.
- Typecheck, lint, Rust format, Cargo check and Clippy passed; Clippy reported zero warnings.
- Unicode catalogue validation: 27/27 checks, 3,963 entries.
- `npm audit --omit=dev`: zero vulnerabilities.
- Windows Sandbox install, launch, shortcut creation, graceful close and uninstall checks passed.

## Known limitations

- English-only expression vocabulary (about 3,000 phrases). On an independent set of 120 prompts, the first suggestion contained an expected emoji for 75%; at least one of four suggestions did so for 87.5%.
- The live Anthropic path was not tested because no API key was available. Automated mock-provider tests passed.
- Installer is unsigned.
- A real screen-reader session and physical display-scaling change were not tested; scaling was emulated.
- `cargo audit` was not run.
