# Emo-Xpress

<p align="center">
  <img src="assets/emo-xpress-icon.png" alt="Emo-Xpress app icon" width="104" />
</p>

<h2 align="center">Every emotion. One expression.</h2>

<p align="center">
  A fast, offline-first emoji library for Windows. Find the right emoji, save favourites, revisit recent picks, and copy the exact Unicode sequence in one action.
</p>

<p align="center">
  <strong>Version 1.0.0</strong> · Windows x64 · Offline-first · 3,963 emoji entries
</p>

<p align="center">
  <a href="https://github.com/kosandra0/Emo-Xpress/releases">Download v1.0.0</a> ·
  <a href="CHANGELOG.md">Changelog</a> ·
  <a href="THIRD_PARTY_NOTICES.md">Third-party notices</a> ·
  <a href="PRIVACY.md">Privacy</a>
</p>

---

## Preview

<p align="center">
  <img src="assets/emo-xpress-preview.webp" alt="Emo-Xpress 1.0.0 showing the emoji library, category sidebar, search field, and emoji grid" width="900" />
</p>

## What it does

Emo-Xpress helps you find, save, revisit, and copy the right emoji without hunting through long lists or relying on an online service.

- **Complete catalogue:** 3,963 fully-qualified entries based on official Unicode Emoji 18.0 data.
- **Search:** Find emoji by CLDR English names and annotation keywords.
- **Nine categories:** Browse Smileys & Emotion, People & Body, Animals & Nature, Food & Drink, Travel & Places, Activities, Objects, Symbols, and Flags.
- **Favorites:** Save frequently used emoji locally and keep them after restarting the app.
- **Recently Used:** Successful copies appear in a newest-first history, capped at 100 unique entries.
- **Exact copying:** Copies the original Unicode sequence, including flags, keycaps, skin-tone modifiers, tag sequences, and ZWJ emoji.
- **Appearance:** Choose Dark, Light, or System mode.
- **Offline-first:** The catalogue is bundled with the application. Core features do not require an account, cloud service, or internet connection.

## Download and install

**Latest release:** [Emo-Xpress v1.0.0 for Windows x64](https://github.com/kosandra0/Emo-Xpress/releases)

1. Open the [Releases page](https://github.com/kosandra0/Emo-Xpress/releases).
2. Download `Emo-Xpress_1.0.0_x64-setup.exe`.
3. Optionally verify the SHA-256 checksum shown in the release assets.
4. Run the installer and follow the prompts.

### Windows SmartScreen notice

The v1.0.0 installer is **not digitally signed**. Windows may display a SmartScreen warning because the publisher identity cannot be verified. This is disclosed here rather than presented as a signed release. Only obtain the installer from this repository's Releases page, and verify its published checksum before running it.

### System compatibility

- Designed for 64-bit Windows 10 and Windows 11.
- Release installation and application behaviour were tested on **Windows 10 Enterprise, build 19045**.
- A clean-machine installation and a separate Windows 11 test have not been completed.

## Privacy and local data

Emo-Xpress is designed to work locally:

- No account or sign-in.
- No telemetry, advertising, or analytics SDK.
- No cloud synchronization.
- No background network requests for normal app use.
- Favorites, Recently Used, and appearance preference are stored on the device.
- The app writes the selected emoji to the clipboard; it does not read or monitor clipboard contents.

See [PRIVACY.md](PRIVACY.md) for the local data details.

## Unicode data and emoji rendering

The catalogue uses:

- **Unicode Emoji 18.0** for emoji sequences and qualification.
- **Unicode CLDR 49** for English names and search annotations.
- **Noto Color Emoji 2.057** for emoji rendering in the application.

The catalogue contains **3,963 fully-qualified entries**. The nine component entries are excluded from the normal browse grid. The chart subtotal of 3,960 and chart total of 3,972 are separately reconciled in the catalogue validation process; they are not substitutes for the fully-qualified entry count.

The exact copied text is the stored Unicode sequence and does not depend on the font used to draw it.

The bundled Noto font is licensed under the SIL Open Font License 1.1. Unicode/CLDR data and font attributions are provided in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

## Verification summary

The v1.0.0 release record reports:

| Check | Result |
|---|---:|
| Frontend automated tests | 210/210 passed |
| Catalogue validation | 27/27 passed |
| TypeScript typecheck | Passed |
| ESLint | Passed |
| Production frontend build | Passed |
| Rust formatting and compilation checks | Passed |
| Production dependency audit | 0 vulnerabilities |
| NSIS installer | Built successfully |
| Install, launch, same-version reinstall, and uninstall | Tested on the development PC |

These results are from the recorded release verification on the development machine. They are not a claim of testing on every Windows configuration.

## Known limitations

- The installer is unsigned; SmartScreen may show a warning.
- A clean virtual machine and a separate Windows 11 machine were not used for installation testing.
- Screen-reader testing and hardware display-scaling tests above 100% remain outstanding.
- Some family and parent/child emoji are rendered by Noto Color Emoji as a grey silhouette tile.
- WebView2's text-field context menu may still contain browser-provided entries such as “Emoji” and “Import passwords”.

## Technology

Emo-Xpress 1.0.0 is built with React, TypeScript, Vite, Tailwind CSS, Tauri 2, Rust, and SQLite. The emoji catalogue is generated from pinned Unicode and CLDR source data and bundled with the application.

## Version roadmap

The roadmap below describes planned directions; it does not mean those features are included in v1.0.0.

| Version | Main objective |
|---|---|
| **1.0** | Emoji library, search, categories, favorites, recent history, and copying |
| **1.1** | Personal collections, folders, custom combinations, and themes |
| **1.2** | Global shortcut, floating picker, and clipboard manager |
| **2.0** | AI expression engine and contextual recommendations |
| **2.1** | Kaomoji, symbols, stickers, and GIF collections |
| **3.0** | Advanced analytics, synchronization, and cloud backup |

## Source availability

This is a **distribution-only public repository**. The application source code and private development records are not published here. The repository provides release information, the compiled Windows installer, and relevant distribution notices.

No open-source licence is granted to the Emo-Xpress application source or original application assets by this repository. Third-party materials remain subject to their respective licences, as described in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

---

**Emo-Xpress** · Every emotion. One expression.
