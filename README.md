# Emo-Xpress

<p align="center">
  <img src="assets/emo-xpress-neon-icon.webp" alt="Emo-Xpress Neon Emoji Hub app icon" width="104" />
</p>

<h2 align="center">Every emotion. One expression.</h2>

<p align="center">
  A fast, offline-first emoji library for Windows. Find the right emoji, save favourites, revisit recent picks, and copy the exact Unicode sequence in one action.
</p>

<p align="center">
  <strong>Verified build 1.0.1</strong> · Windows x64 · Unicode Emoji 18.0 · CLDR 49 · 3,963 fully-qualified entries
</p>

<p align="center">
  <a href="https://github.com/kosandra0/Emo-Xpress/releases">GitHub Releases</a> ·
  <a href="CHANGELOG.md">Changelog</a> ·
  <a href="THIRD_PARTY_NOTICES.md">Third-party notices</a> ·
  <a href="PRIVACY.md">Privacy</a>
</p>

---

## What Emo-Xpress does

Emo-Xpress helps you find, save, revisit, and copy emoji without relying on an online service.

- **Catalogue:** 3,963 fully-qualified entries from official Unicode Emoji 18.0 data.
- **Names and search keywords:** English CLDR 49 annotations, with local search by name and keyword.
- **Nine categories:** Smileys & Emotion, People & Body, Animals & Nature, Food & Drink, Travel & Places, Activities, Objects, Symbols, and Flags.
- **Favorites:** Save emoji locally and keep them after restarting the application.
- **Recently Used:** Successful copies appear newest-first, with a maximum of 100 unique entries.
- **Exact copying:** Copies the stored Unicode sequence, including flags, keycaps, skin-tone modifiers, subdivision tag sequences, and ZWJ emoji.
- **Appearance:** Dark, Light, or System mode.
- **Local-first operation:** The catalogue is bundled with the application; normal core features do not require an account or cloud service.

## What's new in 1.0.1

Version 1.0.1 refines the desktop experience without changing the Unicode catalogue or the existing database schema.

### Interface and navigation
- **Full collapsible sidebar:** The expanded sidebar is 264 px wide. The compact icon rail is 80 px wide and retains navigation icons for every destination, including all nine categories, Settings, and About.
- **Navigation tooltips:** The compact rail shows destination names on hover. Keyboard-focus tooltip behaviour was covered by automated tests and code review, but was not separately exercised with a physical keyboard in the native desktop window.
- **Animated navigation:** Category selection uses a sliding active indicator, restrained hover movement, and a soft accent glow.
- **Cursor-following ambient glow:** A subtle translucent violet light follows mouse movement. It is disabled or simplified for reduced-motion, high-contrast, and forced-colors preferences.
- **Responsive behaviour:** Below approximately 940 px window width, the compact rail is forced and the manual sidebar toggle is hidden.

### Window customization
- **macOS-style traffic lights:** Red Close, yellow Minimize, and green Maximize/Restore controls use native window actions.
- **Control placement:** Choose left or right placement. The title remains centred in either orientation.
- **Close behaviour:** Choose to minimize to the system tray or exit the application.
- **Rounded corners:** Adjust the real application window corner radius from 0 to 24 px, with a live preview.

### Typography and application identity
- **Typography settings:** Search and preview 49 Windows font-family choices, with a Reset to Default option.
- **Font availability:** The application detects whether a font is installed. Unavailable fonts are disabled rather than downloaded or silently applied. All 49 listed fonts were installed on the development PC; another PC may have fewer.
- **Emoji rendering:** Interface font selection does not replace the emoji font. Emoji remain rendered with the bundled Noto Color Emoji font.
- **Updated branding:** The Neon Emoji Hub artwork is used for the sidebar and the generated Windows application, executable, taskbar, and installer icons.
- **About page:** Displays the application version, description, Unicode/CLDR information, catalogue count, and acknowledgements.

### Data and implementation
- The existing Favorites, Recently Used, appearance, close-behaviour, and corner-radius data are retained.
- The sidebar, traffic-light position, and selected-font preferences use additional keys in the existing SQLite settings table. No database migration was required.
- The final refinement added no runtime dependencies for these settings or visual features.
- The application remains local-first. No telemetry, cloud synchronization, or remote font downloads were added.

## Download and install

Use the [GitHub Releases page](https://github.com/kosandra0/Emo-Xpress/releases) for published installers. That page identifies which version is currently published as the latest release.

The verified v1.0.1 Windows x64 NSIS installer is named **Emo-Xpress_1.0.1_x64-setup.exe**. Its final recorded size is **4,433,226 bytes (4.23 MiB)**.

### v1.0.1 installer SHA-256

**677b95a15aa8fb25a10057ac6f9863923a0229b64a7c542ff8ab63331f968798**

This value is also recorded in [SHA256SUMS.txt](SHA256SUMS.txt). Compare the checksum of the file you downloaded with this value before running it.

### Windows SmartScreen notice

The v1.0.1 installer is **not digitally signed**. Windows may display a SmartScreen warning because the installer has no code-signing certificate. Obtain installers only from this repository's Releases page and verify the checksum.

### Tested environment

- Windows 10 Enterprise, build 19045.
- The final v1.0.1 installer and installed application were checked on the development PC.
- Windows 11, a clean second machine, and a Windows restart test were not completed.

## Privacy and local data

Emo-Xpress stores Favorites, Recently Used, appearance, close behaviour, corner radius, sidebar state, traffic-light position, and selected font preference locally in SQLite.

The application writes a selected emoji to the Windows clipboard when the user chooses to copy it. It does not read or monitor clipboard contents.

Fonts are selected from those installed on the computer. Emo-Xpress does not download fonts. The Unicode/CLDR catalogue and Noto emoji font are bundled with the application.

See [PRIVACY.md](PRIVACY.md) for further details.

## Unicode data and emoji rendering

The catalogue uses:
- **Unicode Emoji 18.0** for emoji sequences and qualification.
- **Unicode CLDR 49** for English names and search annotations.
- **Noto Color Emoji 2.057** for on-screen emoji rendering.

The catalogue contains **3,963 fully-qualified entries**. The nine component entries are excluded from the browse catalogue. The official chart's subtotal of 3,960 and total of 3,972 are separately reconciled by the validation process; neither replaces the fully-qualified catalogue count.

The exact copied text is the stored Unicode sequence and does not depend on the font used to draw it.

The bundled Noto Color Emoji font is licensed under the SIL Open Font License 1.1. Unicode/CLDR data and font attributions are described in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

## Verification summary

The final v1.0.1 development record reports these automated checks:

| Check | Result |
|---|---:|
| Frontend tests | 293/293 passed |
| Unicode catalogue validation | 27/27 passed |
| TypeScript typecheck | Passed |
| ESLint | Passed |
| Production frontend build | Passed |
| Rust formatting check | Passed |
| Rust compilation check | Passed |
| Rust tests | 2 passed |
| Production dependency audit (`npm audit --omit=dev`) | 0 vulnerabilities |

### Native Windows checks

Native mouse and window tests were performed against the real Tauri application using an isolated test application identifier, so test settings writes did not touch the owner's production database. The recorded checks include:

- Close, Minimize, Maximize/Restore, title-bar dragging, and both traffic-light positions.
- Sidebar collapse to the 80 px icon rail, navigation, tooltip on hover, and persistence across an application restart.
- Font selection and persistence across an application restart.
- Traffic-light position selection and persistence across an application restart.
- Cursor-follow glow with a real mouse, and reduced-motion / contrast preference emulation in WebView2.
- System-tray and corner-radius behaviour on an isolated build.

The final installer was also installed over the existing v1.0.1 installation on the owner's PC. The real user database was backed up and checked read-only; its SHA-256 matched before and after the update. The installed application opened with the stored Dark appearance and 24 px corner radius, and showed the existing 2 Favorites and 10 Recently Used entries. The final refinement did **not** write the new sidebar, font, or traffic-light-position settings to the owner's real database; those setting writes were tested on the isolated identifier instead.

These results describe the recorded development-machine tests, not universal compatibility with every Windows configuration.

## Known limitations

- The installer is unsigned.
- Testing was performed on one Windows 10 Enterprise development PC. Windows 11, a clean second machine, Windows restart, screen readers, real Windows High Contrast, and hardware display scaling above 100% were not tested.
- Native mouse resizing below 940 px while the compact rail is active was not repeated in this final round; rail layout measurements were checked in the browser test environment.
- Keyboard-focus tooltips were verified in automated tests and by code review, not with a physical keyboard in the actual desktop window.
- All 49 listed fonts were installed on the development PC. Other PCs may show some choices as unavailable.
- Some family and parent/child emoji are rendered by Noto Color Emoji as a grey silhouette tile.
- The WebView2 text-field context menu may still include browser-provided entries such as “Emoji” and “Import passwords”.
- Sidebar width transitions were not frame-time profiled. A continuous mouse sweep over the emoji grid used around 50–58% of one CPU core on the development PC, with or without the glow; the glow itself added no measurable CPU use in that comparison.
- A production dependency audit found 0 vulnerabilities. An earlier full development-dependency audit reported 10 moderate advisories in the ESLint/typescript-eslint toolchain; those development dependencies are not included in the production dependency audit.

## Technology

Emo-Xpress is built with React, TypeScript, Vite, Tailwind CSS 4, Tauri 2, Rust, and SQLite. The emoji catalogue is generated at development time from pinned Unicode and CLDR source files and bundled with the application.

## Version roadmap

The roadmap below is the project's planned feature sequence. Items are future objectives, not claims about features included in the current build.

| Version | Main objective |
|---|---|
| **1.0** | Emoji library, search, categories, favorites, recent history and copying |
| **1.1** | Personal collections, folders, custom combinations and themes |
| **1.2** | Global shortcut, floating picker and clipboard manager |
| **2.0** | AI expression engine and contextual recommendations |
| **2.1** | Kaomoji, symbols, stickers and GIF collections |
| **3.0** | Advanced analytics, synchronization and cloud backup |

The next planned feature milestone is **v1.1.0**. Development of that milestone has not started.

## Source availability

This is a **distribution-only public repository**. Application source code and private development records are not published here. The repository contains public-facing documentation, release information, compiled Windows installers when released, checksums, and third-party distribution notices.

No open-source licence is granted to the Emo-Xpress application source or original application artwork by this repository. Third-party materials remain subject to their respective licences, as described in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

---

**Emo-Xpress** · Every emotion. One expression.
