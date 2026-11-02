# Drill playlists, weekly recaps and csTimer import

The shared frontend provides **Drill playlists** (`/drills`), **Weekly recap** (`/recap`) and **Import csTimer** (`/import`). Shortcuts appear on Dashboard, the app home, Practice, Timer and Training goals. Account access requires the existing sign-in/verification rules; installed apps provide these tools in their local workspace too.

## Drill playlists

Choose cases from the puzzle and case-set filters, reorder them, and set repetitions and an execution target for each case. Routines have at most 30 distinct cases and 60 initial rounds. Each difficult round returns once at the end, keeping the maximum session to 120 rounds.

Show the inverse case to start recognition timing, reveal its algorithm, set up the physical puzzle, and start/stop execution timing. Self-rate the result as recognized and accurate, needed a hint, or an execution mistake. Recognition and execution are stored separately. Accurate executions, including those needing a recognition hint, also appear in algorithm practice history. Execution mistakes remain in the drill record without becoming successful practice attempts. Timings and ratings are self-assessed; they do not verify hardware or certify mastery.

Source-specific notation links to its source diagram instead of showing an incompatible puzzle animation. Changing connection mode waits during a routine. Unfinished results have a device-session draft; reload resumes at the current round, restarting its timing. Failed saves can be retried without duplicate records. Ending early can save completed rounds or discard the session. Playlists can be edited or removed; removed playlist records remain as tombstones so sync does not resurrect them.

## Weekly recap

Choose an event. The report compares six complete local calendar days plus today with the preceding seven days. It shows solve volume, active days, median, best single, DNF rate and variation relative to mean time. Median changes require five valid solves in each period. +2 penalties affect times; DNFs count toward the DNF rate and are excluded from valid-time metrics. Today is a partial day.

Learning totals cover all puzzles and courses, and are labeled separately from the event-specific solve statistics. Recommendations use recorded accuracy/variation and practice volume; total times do not establish a weak solving-method stage. Recaps are computed from saved records and do not call a model or send a weekly notification.

Older offline lesson records without a completion timestamp are omitted from date-based lesson counts. Imported csTimer solves are counted on their original dates. Sync preserves drill and algorithm-attempt timestamps.

## csTimer import

Export csTimer's full session backup to a `.txt` or `.json` file, then choose it in CubeHub. The local preview shows sessions, counts, sample results and detected events. Unknown/custom scramble types require an explicit event choice or **Skip session**. Review the selected events before importing.

Supported backups contain `sessionN` arrays and optional `properties.sessionData` metadata. The importer retains session names, raw elapsed milliseconds, +2/DNF flags, scrambles, dates and comments. It accepts at most 50,000 solves / 20 MB per file and uploads bounded batches. Rows without valid dates or supported values are skipped with a warning. csTimer phase splits are not relabeled as method-stage splits. A DNF without an elapsed time uses a 1 ms storage placeholder and stays excluded from valid-time statistics.

Imports create separate csTimer sessions and do not award XP. Stable per-account receipts protect retries and repeated backups, including identical repeated rows in one backup. Deleting a solve retains its receipt so a repeated import does not recreate it. Changing a session's mapped event produces distinct records; keep the mapping consistent when retrying. Original comments are included in account export and retained on the solve record.

## Storage and verification

Additive tables are shared by SQLite and PostgreSQL: `drill_playlists`, `drill_runs`, `history_sessions` and `history_imports`. PostgreSQL schema migration 6 records the addition. Account deletion cascades owned data; backups and account exports include the new tables. Offline sync uploads playlists before drill results, avoids uploading derived attempts twice, and shares import receipts with direct csTimer import.

Run `npm run check`, the automated tests, `npm run apps:web`, and `npx electron scripts/smoke-toolkit.cjs`. The last command checks a bundled production frontend in a hidden window with external requests blocked. Set `CUBEHUB_SCREENSHOT_DIR` to save desktop and phone-width captures. Pass a packaged `resources/app.asar` path as an optional argument to check the actual Windows package.

Rebuild Android/Windows for new bundled offline tools, and deploy the backend and website from the same source version. Native hardware and signed iOS distribution retain their separate acceptance requirements.
