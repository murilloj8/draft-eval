# 10U Draft Evaluator

Phone-friendly app for tagging players during the skills assessment. Load your draft pool spreadsheet, tag players, export an updated .xlsx. All data stays on your device; nothing is uploaded anywhere.

## Before you upload (one required step)
Download SheetJS and save it as `lib/xlsx.full.min.js`:
https://cdn.sheetjs.com/xlsx-0.20.3/package/dist/xlsx.full.min.js
(Right-click, Save As.) You can delete the `PUT_xlsx...txt` placeholder. Without this file the app cannot read spreadsheets.

## Put it on GitHub Pages
1. Sign in at github.com, click **+** > **New repository**, name it (e.g. `draft-eval`), keep it Public, click **Create repository**.
2. Click **uploading an existing file**, drag in everything from this folder (index.html, manifest.webmanifest, service-worker.js, the `icons` and `lib` folders), then **Commit changes**. (If folders won't drag in, upload the files inside each folder via Add file > Upload files after creating the folder path by typing `lib/` in the name box.)
3. **Settings** > **Pages** > Source: **Deploy from a branch**, Branch: **main**, folder **/ (root)** > **Save**.
4. After a minute your site is at `https://YOUR-USERNAME.github.io/draft-eval/`.

## Install on your phone (do this once, with signal)
- **iPhone (Safari):** open the link, tap Share, **Add to Home Screen**.
- **Android (Chrome):** open the link, menu (three dots), **Install app** / **Add to Home screen**.
Open it once from the home screen so it caches for offline use.

## Using it
- **Load spreadsheet**, pick your .xlsx. The Draft Pool shows first; change the Status filter to see NL Hat Picks.
- In the list, tap **P / S / D / F** (Priority, Strong, Development, Further) to tag instantly; tap again to clear.
- Tap the rest of a row for details: Position, Round, Evaluation, your notes, every spreadsheet column, plus Prev/Next.
- **Now slot** filters to the current time slot. Search by bib number or any text.
- Work autosaves in the browser (see "saved" time). Reopening offers to restore it. **Export Excel** often.

## How your columns are handled
- Evaluation: read and written in place. "Development Prospect" becomes Development, "Needs Further Evaluation" becomes Further Evaluation; 0, #N/A and blank are untagged. Export writes the new wording (untagged = empty cell).
- Position: the existing "Position " column. Round: added as a new last column. My notes: written to "Other Notes". The existing Notes column is shown but never changed.
- Separator, label and total rows stay in place in the export.

## Export limits
The export edits your original sheet, so values, times and row order are preserved. The free SheetJS build may drop some formatting (cell colors, frozen header row). The filter is re-applied across all columns.

## Test before Sunday
Import, tag a few players, export, open in Excel. Check: same row count and order; Time Slot still shows times; Notes unchanged; Evaluation has no stray 0s; Round column exists. Then turn on airplane mode and reopen from the home screen.
