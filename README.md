# Emo-Xpress

<p align="center">
  <img src="assets/emo-xpress-icon.png" alt="Emo-Xpress app icon" width="104" />
</p>

<h2 align="center">Every emotion. One expression.</h2>

<p align="center">
  A fast, offline-first emoji library for Windows. Find the right emoji, save favourites, revisit recent picks, and copy the exact Unicode sequence in one action.
</p>

<p align="center">
  <strong>Verified build 1.0.1</strong> · Windows x64 · Offline-first · 3,963 emoji entries
</p>

<p align="center">
  <a href="https://github.com/kosandra0/Emo-Xpress/releases">Download the latest published release</a> ·
  <a href="CHANGELOG.md">Changelog</a> ·
  <a href="THIRD_PARTY_NOTICES.md">Third-party notices</a> ·
  <a href="PRIVACY.md">Privacy</a>
</p>

---

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

## What's new in 1.0.1

Version 1.0.1 adds a more customizable macOS-inspired desktop experience while preserving the existing emoji catalogue and local data.

### Interface and navigation
- **Collapsible icon-rail sidebar:** Switch between the full sidebar and a compact icon-only rail. Navigation remains available in both modes, with tooltips for compact navigation.
- **Cursor-following ambient glow:** A subtle translucent light follows the pointer across the interface. The effect is disabled or simplified for reduced-motion and high-contrast settings.
- **Animated navigation:** Category selection uses a sliding active indicator, soft glow, and restrained hover transitions.
- **Responsive sidebar:** The content area expands when the sidebar is collapsed. Narrow windows can automatically use the compact rail.

### Window customization
- **macOS-style traffic lights:** Red Close, yellow Minimize, and green Maximize/Restore controls use native window actions.
- **Control placement:** Choose left or right positioning for the traffic-light group.
- **Close behaviour:** Choose to minimize to the system tray or exit the application.
- **Rounded corners:** Adjust the application window corner radius from 0 to 24 px, with a live preview.

### Typography and identity
- **System font selection:** Choose from 49 Windows font families detected on the development PC, search the list, preview a choice, and reset to the default.
- **Font availability handling:** Fonts not installed on a computer are shown as unavailable and are not silently applied. Fonts are not downloaded remotely or bundled by Emo-Xpress.
- **Emoji rendering remains separate:** Interface font preferences do not replace the emoji font fallback or alter Unicode sequences.
- **Updated Neon Emoji Hub branding:** The new artwork is used in the sidebar and generated Windows application, executable, and installer icon assets.
- **About page:** Shows application information, version, Unicode/CLDR information, and catalogue details.

### Existing data and core behaviour
- The 3,963-entry Unicode Emoji 18.0 catalogue and CLDR 49 annotations are unchanged.
- Favorites, Recently Used, and appearance data remain local.
- The new sidebar and window-control preferences use the existing settings storage; no database schema migration was required.
- No telemetry, cloud synchronization, or remote font downloads were added.

## Download and install

**Verified build:** Emo-Xpress 1.0.1 for Windows x64.

Open the [Releases page](https://github.com/kosandra0/Emo-Xpress/releases) to download the latest published installer. The Releases page is the source of truth for which build is publicly available.

1. Open the [Releases page](https://github.com/kosandra0/Emo-Xpress/releases).
2. Download the Windows x64 NSIS installer attached to the release you want.
3. Optionally verify the installer's SHA-256 against the checksum in the release and [SHA256SUMS.txt](SHA256SUMS.txt).
4. Run the installer and follow the prompts.

### v1.0.1 installer checksum

The verified v1.0.1 installer is named `Emo-Xpress_1.0.1_x64-setup.exe`.

```text
SHA-256  677b95a15aa8fb25a10057ac6f986923a0229b64a7c542ff8ab63331f9698798
```

The checksum is also recorded in [SHA256SUMS.txt](SHA256SUMS.txt). Always compare the hash of the file you downloaded with the published value.

### Windows SmartScreen notice

The v1.0.1 installer is **not digitally signed**. Windows may display a SmartScreen warning because the publisher identity cannot be verified. Only obtain the installer from this repository's Releases page, and verify its published checksum before running it.

### System compatibility

- Designed for 64-bit Windows 10 and Windows 11.
- The v1.0.1 installation and native desktop checks were performed on **Windows 10 Enterprise, build 19045**.
- A clean-machine installation, a separate Windows 11 test, and a Windows restart test were not completed.
- Hardware display-scaling tests above 100% and screen-reader testing remain outstanding.

## Privacy and local data

Emo-Xpress is designed to work locally:

- No account or sign-in.
- No telemetry, advertising, or analytics SDK.
- No cloud synchronization.
- No background network requests for normal app use.
- Favorites, Recently Used, appearance, sidebar, window-control position, close behaviour, corner radius, and selected font preference are stored locally.
- Fonts are selected from those installed on the computer; the app does not download fonts.
- The app writes the selected emoji to the clipboard; it does not read or monitor clipboard contents.

See [PRIVACY.md](PRIVACY.md) for local data details.

## Unicode data and emoji rendering

The catalogue uses:

- **Unicode Emoji 18.0** for emoji sequences and qualification.
- **Unicode CLDR 49** for English names and search annotations.
- **Noto Color Emoji 2.057** for emoji rendering in the application.

The catalogue contains **3,963 fully-qualified entries**. The nine component entries are excluded from the normal browse grid. The chart subtotal of 3,960 and chart total of 3,972 are separately reconciled in the catalogue validation process; they are not substitutes for the fully-qualified entry count.

The exact copied text is the stored Unicode sequence and does not depend on the font used to draw it.

The bundled Noto font is licensed under the SIL Open Font License 1.1. Unicode/CLDR data and font attributions are provided in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

## Verification summary

The v1.0.1 build report records the following checks:

| Check | Result |
|---|---:|
| Frontend automated tests | 293/293 passed |
| Catalogue validation | 27/27 passed |
| TypeScript typecheck | Passed |
| ESLint | Passed |
| Production frontend build | Passed |
| Rust formatting and compilation checks | Passed |
| Rust tests | 2 passed |
| Production dependency audit | 0 vulnerabilities |
| Native traffic-light checks | Both control positions tested with native mouse input |
| Sidebar, font and control-position settings | Worked in the real app and survived an app restart |
| Reduced-motion and high-contrast glow fallbacks | Checked in the real WebView |
| Database preservation | Backup hash matched before and after the update |

The installed v1.0.1 application was checked on the development PC. These results are not a claim of testing on every Windows configuration.

## Known limitations

- The installer is unsigned; Windows SmartScreen may show a warning.
- Installation was tested on one Windows 10 Enterprise development PC. A clean-machine test, separate Windows 11 test, and Windows restart test were not completed.
- Screen-reader testing, keyboard-focus tooltip behaviour in the actual window, and hardware display-scaling tests above 100% remain outstanding.
- The compact sidebar is automatically used for windows narrower than approximately 940 px.
- Font availability depends on the fonts installed on each Windows computer. The 49 choices were all available on the development PC; unavailable fonts are identified rather than downloaded.
- During sustained pointer movement over the emoji grid, the development PC showed around half a CPU core of activity, with or without the cursor glow. The glow itself added no measurable CPU use in the reported comparison.
- Some family and parent/child emoji are rendered by Noto Color Emoji as a grey silhouette tile.
- WebView2's text-field context menu may still contain browser-provided entries such as “Emoji” and “Import passwords”.
- The new settings were exercised using isolated test data for persistence checks; the existing user database was backed up and its hash remained unchanged during the upgrade.

## Technology

Emo-Xpress is built with React, TypeScript, Vite, Tailwind CSS, Tauri 2, Rust, and SQLite. The emoji catalogue is generated from pinned Unicode and CLDR source data and bundled with the application.

## Version roadmap

The roadmap below describes planned directions; it does not mean those features are included in the current build.

| Version | Main objective |
|---|---|
| **1.0** | Emoji library, search, categories, favorites, recent history, and copying |
| **1.0.1** | Desktop UI refinement, window customization, collapsible sidebar, ambient glow, typography, and About page |
| **1.1** | Personal collections, folders, custom combinations, and themes |
| **1.2** | Global shortcut, floating picker, and clipboard manager |
| **2.0** | AI expression engine and contextual recommendations |
| **2.1** | Kaomoji, symbols, stickers, and GIF collections |
| **3.0** | Advanced analytics, synchronization, and cloud backup |

## Source availability

This is a **distribution-only public repository**. The application source code and private development records are not published here. The repository provides release information, compiled Windows installers, checksums, and relevant distribution notices.

No open-source licence is granted to the Emo-Xpress application source or original application assets by this repository. Third-party materials remain subject to their respective licences, as described in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

---

**Emo-Xpress** · Every emotion. One expression.
