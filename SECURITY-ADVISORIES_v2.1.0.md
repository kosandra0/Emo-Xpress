# Emo-Xpress 2.1.0 — dependency security advisories

This document lists the dependency advisories found for Emo-Xpress 2.1.0 by `cargo audit` 0.23.0 on 2026-11-12. **No advisory listed here is marked as resolved.**

## Summary

| ID | Crate (version in lock) | Severity | In the shipped Windows build? | Status in 2.1.0 |
|---|---|---|---|---|
| RUSTSEC-2026-0459 | `libsqlite3-sys` 0.30.1 (bundles SQLite **3.46.0**) | medium (6.8) | **Yes** | **OPEN.** Not fixed. Remediation planned for a future maintenance release (see below). |
| RUSTSEC-2023-0071 | `rsa` 0.9.10 | medium (5.9) | **No** (lock file only) | Not compiled into the Windows release. Kept in `Cargo.lock`. |

`cargo audit` also reports unmaintained and unsound warnings (`proc-macro-error`, `zbus_names`, `zvariant`, `zvariant_derive`, `glib`) and 5 allowed warnings. These were not reviewed further in this release.

## 1. RUSTSEC-2026-0459 — `libsqlite3-sys` (C SQLite CVE-2026-119375)

**Advisory:** `libsqlite3-sys` 0.30.1 via C SQLite CVE-2026-119375. Patched in `libsqlite3-sys` 0.39.0 or later, per the advisory. Published 2026-10-30.

**Dependency path (from `cargo tree`, Windows normal build):**

```
libsqlite3-sys v0.30.1
└── sqlx-sqlite v0.8.6
    └── sqlx-macros-core v0.8.6
        └── sqlx-macros v0.8.6 (proc-macro)
            └── sqlx v0.8.6
                └── tauri-plugin-sql v2.6.0
                    └── emo-xpress v2.1.0
```

**Bundled SQLite version (verified):** the bundled `libsqlite3-sys` 0.30.1 header reports SQLite `3.46.0`. The fixed `libsqlite3-sys` 0.39.0 bundles SQLite 3.54.0.

**Upstream options checked (no change made to the project):**
- `sqlx` 0.9.0 (latest stable) → `sqlx-sqlite` 0.9.0 requires `libsqlite3-sys` `>=0.30.1, <0.38.0`. So sqlx 0.9.0 cannot take the fixed version (0.39 or later).
- `tauri-plugin-sql` 2.6.0 (latest 2.x) pins `sqlx` `0.8`. Its newest release is `3.0.0-alpha.3`, an alpha that was not adopted for this release.
- Conclusion: no stable upstream release available on 2026-11-12 removes this advisory from the Tauri SQL plugin path. It stays open until a stable plugin or sqlx release allows `libsqlite3-sys` 0.39 or later, or the project moves to a different SQLite binding.

**Attack surface analysis (from the source tree, 2026-11-12):**
1. **No external database is opened.** The only database is `sqlite:emoxpress.db`, a fixed name, resolved inside the app data folder.
2. **No import or file-selection feature.** No code path takes a database path or file name from the user or from another source.
3. **WAL and journal files** are created by SQLite next to `emoxpress.db`, and only the local user (or a process running as that user) can write there. Exploiting a tampered WAL requires code already running as the same user, which is outside this app's trust boundary.
4. **The web view can run SQL.** The main window and the Quick Picker window both have `sql:allow-execute`. The web view is the app's own bundled code, under a strict Content Security Policy with no network access, so only that code issues SQL. The SQL plugin does not block statements such as `ATTACH DATABASE`. The app does not issue `ATTACH`, `PRAGMA` or `load_extension` (a search of the source found none). This is a hardening point (see remediation).
5. **Exposure:** no network access through this path. The app does not parse untrusted data with SQLite; the catalogue and settings are bundled or written by the app itself.

**Risk judgement (an assessment, not a test result):** low for typical use, because an attacker would need local write access to the user's profile, and the SQLite flaw is in a path the app does not use with untrusted input. It is still a real finding in the shipped binary and is **not** marked resolved.

**Remediation plan (future maintenance release, not in 2.1.0):**
1. Track upstream: move to a `tauri-plugin-sql` or `sqlx` release that allows `libsqlite3-sys` 0.39 or later. Re-run `cargo audit` after each update.
2. Before any migration: back up the database, run the migration tests, and verify upgrade and rollback in an isolated environment.
3. Hardening candidate: restrict SQL execution from the web view (for example, an allow-list of statement shapes or a scoped permission) so that `ATTACH` and `PRAGMA` cannot be issued. This needs a separate design review.
4. Alternative: a different SQLite binding under Rust control, which removes the dependency on the plugin's pinned `sqlx`. This needs its own project decision.

## 2. RUSTSEC-2023-0071 — `rsa` 0.9.10 (Marvin timing attack)

**Why it is not compiled into the Windows release:**
- `cargo tree` for all targets, and for the Windows normal build, shows no path to `rsa`.
- `Cargo.lock` lists `rsa` only as a dependency of `sqlx-mysql` 0.8.6. `sqlx-mysql` is an optional `sqlx` feature (`mysql`) that Emo-Xpress does not enable. `cargo tree` for the Windows normal build shows no path to `sqlx-mysql`.
- So `rsa` is recorded in the lock file but is not compiled into the app. The advisory is therefore not exposed in the shipped binary.

**Action:** keep the lock entry. Removing it would need a dependency change, which is out of scope for this release. Re-check after any `sqlx` update.
