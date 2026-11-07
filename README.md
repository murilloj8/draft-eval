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
Three tabs at the top: **Home**, **Find player**, **All bibs**.
- **Home:** pool averages (free throws made, timed run, height, age), how many players are evaluated, and the split by Evaluation, Position and Round (tap a bar to see that group in the table). Two big buttons go to **Find a player** or the **table of all bibs**.
- **Find player:** type a bib number (or tap one from the list) to open that player's page. Bib buttons show evaluation progress: **green** = Eval, Pos and Round are all filled in; **amber outline** = started but incomplete; **plain** = not started. A counter above shows how many players are fully evaluated.
- **Player page** adapts to the screen and fits without scrolling on iPhone and iPad (the green header bar is hidden here; use Back to return). Sections, top to bottom:
  1. **Player profile:** bib, age, grade and school on the left, and an **Overall** rating badge on the right. Below are three indicators, each rated 0 to 99 (the percent of the other players this player beats). **A fuller bar is always better**, including Speed (a faster time earns a higher rating). Height and Speed are bars with a line at the pool median. **Free throws** is five segments, one per shot made. Bar colors: green 90+, blue 75 to 89, amber 50 to 74, grey below 50. Overall is the average of the three ratings and is shown only when the player has height, free throw and run data.
  2. **Player details:** every remaining spreadsheet field as text, with any registration note as a yellow flag.
  3. **Evaluation:** Eval, Position and Round buttons (tap again to clear), then your notes.
  Buttons are larger with full names on iPad. Prev/Next move through the list you came from.
- **All bibs:** one table with Evaluation, Position, Round, Grade, free throws, run time and height. Tap **P / S / D / F** to tag in one tap; tap a row to open the player. Search, filter, sort, **Clear all filters**.
- Time slots show as just the time (e.g. 10:10 AM). The **Hat Picks** checkbox adds the 6 NL Hat Pick players to every view.
- Work autosaves in the browser. Reopening offers to restore it. **Export Excel** often.

## How your columns are handled
- Evaluation: read and written in place. "Development Prospect" becomes Development, "Needs Further Evaluation" becomes Further Evaluation; 0, #N/A and blank are untagged. Export writes the new wording (untagged = empty cell).
- Position: the existing "Position " column. Round: added as a new last column. My notes: written to "Other Notes". The existing Notes column is shown but never changed.
- Separator, label and total rows stay in place in the export.

## Export limits
The export edits your original sheet, so values, times and row order are preserved. The free SheetJS build may drop some formatting (cell colors, frozen header row). The filter is re-applied across all columns.

## Test before Sunday
Import, tag a few players, export, open in Excel. Check: same row count and order; Time Slot still shows times; Notes unchanged; Evaluation has no stray 0s; Round column exists. Then turn on airplane mode and reopen from the home screen.
