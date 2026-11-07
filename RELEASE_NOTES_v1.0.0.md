# Emo-Xpress 1.0.0

**Every emotion. One expression.**

The first stable Windows release of Emo-Xpress: an offline-first desktop emoji library for finding, browsing, saving, and copying the right emoji.

## Download

**Asset:** `Emo-Xpress_1.0.0_x64-setup.exe`  
**Platform:** Windows x64  
**Installer:** NSIS, per-user installation  
**Size:** 4,066,729 bytes (3.88 MiB)  
**SHA-256:** `45263613c649bd842ad74c73565545ab17aa76b6c1204d13adf9f113a178ba69`

The installer is unsigned. Windows SmartScreen may display a warning because no code-signing certificate was used.

## Highlights

- 3,963 fully-qualified emoji entries based on Unicode Emoji 18.0.
- CLDR 49 English names and annotation keywords.
- Nine category groups and a virtualized browsing grid.
- Local search by emoji name and keyword.
- Persistent Favorites and Recently Used history (up to 100 unique entries).
- Exact Unicode clipboard copying for flags, keycaps, skin-tone variants, tag sequences, and ZWJ emoji.
- Dark, Light, and System appearance modes.
- Bundled Noto Color Emoji 2.057 for broader offline emoji glyph coverage.
- No account, telemetry, advertising, cloud dependency, or background network requests for core use.

## Verification

The recorded v1.0.0 verification included:

- 210/210 frontend tests passed.
- Catalogue validation: 27/27 checks passed.
- TypeScript typecheck and ESLint passed.
- Production frontend build passed.
- Rust formatting and compilation checks passed.
- Production dependency audit: 0 vulnerabilities.
- NSIS release build completed.
- Fresh install, launch, same-version reinstall, and uninstall were tested on the development PC.
- Favorites, Recently Used, appearance preference, and local data preservation were checked during installation lifecycle testing.

## Known limitations

- The installer is not digitally signed.
- Installation was tested on the development PC (Windows 10 Enterprise, build 19045); a clean-machine test and a separate Windows 11 test were not completed.
- Screen-reader testing and hardware display-scaling tests above 100% remain outstanding.
- Some family and parent/child emoji are rendered as grey silhouette tiles by the bundled Noto font.
- WebView2's text-field context menu retains a few browser-provided entries.

## Privacy

Favorites, Recently Used, and appearance settings are stored locally. Version 1.0.0 writes selected emoji to the clipboard but does not read or monitor clipboard contents. See [PRIVACY.md](https://github.com/kosandra0/Emo-Xpress/blob/main/PRIVACY.md).

## Notices

Unicode/CLDR data and Noto Color Emoji notices are included in [THIRD_PARTY_NOTICES.md](https://github.com/kosandra0/Emo-Xpress/blob/main/THIRD_PARTY_NOTICES.md).

The public repository is distribution-only; application source code and private development records are not published.
