# Third-party notices

Emo-Xpress bundles data derived from the Unicode Consortium's emoji data and the Unicode CLDR project.
This file carries the required copyright and permission notice. The Unicode and CLDR data are not modified
in meaning: they are parsed and normalised into `src/data/emoji-catalogue.json` by the development-time
generator in `scripts/` (not at run time).

## Data in the bundled catalogue

| Data | Version | Source (pinned; SHA-256 in `scripts/sources/MANIFEST.json`) |
|---|---|---|
| Unicode Emoji data: `emoji-test.txt`, `emoji-sequences.txt`, `emoji-zwj-sequences.txt` | 18.0 | https://www.unicode.org/Public/18.0.0/emoji/ |
| Unicode Emoji count chart (used to reconcile counts only; not bundled in the app) | 18.0 | https://www.unicode.org/emoji/charts-18.0/emoji-counts.html |
| CLDR English emoji annotations (names and keywords), main and derived | 49 (release 49.0.0) | https://github.com/unicode-org/cldr-json/tree/49.0.0 |

Terms of use: https://www.unicode.org/copyright.html (Unicode License V3, reproduced below).

Emoji glyphs shown in the app are rendered using the bundled Noto Color Emoji font described below. The app does not bundle a separate raster image for each emoji; the Unicode text sequence is copied to the clipboard unchanged.

## Unicode License V3

UNICODE LICENSE V3

COPYRIGHT AND PERMISSION NOTICE

Copyright © 1991-2026 Unicode, Inc.

NOTICE TO USER: Carefully read the following legal agreement. BY
DOWNLOADING, INSTALLING, COPYING OR OTHERWISE USING DATA FILES, AND/OR
SOFTWARE, YOU UNEQUIVOCALLY ACCEPT, AND AGREE TO BE BOUND BY, ALL OF THE
TERMS AND CONDITIONS OF THIS AGREEMENT. IF YOU DO NOT AGREE, DO NOT
DOWNLOAD, INSTALL, COPY, DISTRIBUTE OR USE THE DATA FILES OR SOFTWARE.

Permission is hereby granted, free of charge, to any person obtaining a
copy of data files and any associated documentation (the "Data Files") or
software and any associated documentation (the "Software") to deal in
the Data Files or Software without restriction, including without limitation
the rights to use, copy, modify, merge, publish, distribute, and/or sell
copies of the Data Files or Software, and to permit persons to whom the
Data Files or Software are furnished to do so, provided that either (a)
this copyright and permission notice appear with all copies of the Data
Files or Software, or (b) this copyright and permission notice appear in
associated Documentation.

THE DATA FILES AND SOFTWARE ARE PROVIDED "AS IS", WITHOUT WARRANTY OF ANY
KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT OF
THIRD PARTY RIGHTS.

IN NO EVENT SHALL THE COPYRIGHT HOLDER OR HOLDERS INCLUDED IN THIS NOTICE
BE LIABLE FOR ANY CLAIM, OR ANY SPECIAL INDIRECT OR CONSEQUENTIAL DAMAGES,
OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS,
WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION,
ARISING OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THE DATA
FILES OR SOFTWARE.

Except as contained in this notice, the name of a copyright holder shall
not be used in advertising or otherwise to promote the sale, use or other
dealings in these Data Files or Software without prior written
authorization of the copyright holder.

Unicode and the Unicode Logo are registered trademarks of Unicode, Inc. in the U.S. and other countries.

## Software dependencies

Open-source npm and Cargo packages used to build and run the app (React, Tauri, Tailwind CSS, Zustand, Lucide and
others) are licensed by their authors under their own terms. This document focuses on the Unicode/CLDR data and
Noto font redistributed as part of the Emo-Xpress application; it is not a complete inventory of every transitive
software dependency.

## Emoji font: Noto Color Emoji

The emoji pictures shown in the app come from **Noto Color Emoji** (version 2.057, release `v2026-09-24-unicode18_0`,
COLRv1 build `2D/fonts/Noto-COLRv1.ttf` from <https://github.com/googlefonts/noto-emoji>), Copyright 2013 Google LLC,
licensed under the **SIL Open Font License, Version 1.1**. The font is redistributed unmodified apart from a lossless
container conversion from TrueType to WOFF2 (`src/assets/fonts/NotoColorEmoji-COLRv1.woff2`). The full licence text is in
`src/assets/fonts/NotoColorEmoji-OFL.txt`. The font is used only to draw emoji on screen; the text copied to the
clipboard is always the standard Unicode character sequence and never depends on the font.
