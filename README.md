# IACT100 Digital Checklist

A digital version of IAC's **T100 Pre-Test / Inspection checklist** (document
QAP07_04_17) for the test department. One HTML file, no installation, no
server, works offline — open it in any browser and it behaves like the paper
form, minus the pen.

## Using it

**Open `index.html` in a browser.** That's it. Put a copy on the shared drive,
a USB stick, or a bench PC desktop. It also works served from GitHub Pages if
you want a URL instead of a file.

1. Fill in the **job header**: customer, contract number, items covered,
   date, tester name and initials. Your initials are stamped automatically
   against every item you mark — no more writing them 120 times.
2. Work through the four parts (tabs at the top, mirroring the paper form):
   - **Part 1** — Pre-Test / Inspection (1.1 – 1.10)
   - **Part 2** — Routine Tests EN60204 / EN61439 (2.0 – 2.7)
   - **Part 3** — Functional Test / Validation (3.1 – 3.9)
   - **Part 4** — Final Inspection (4.1 – 4.13)
3. Each item has three states — **✓ checked**, **N/A**, **✗ snag** — plus a
   comment box that can be used whether the item passed or not (test values,
   document references, "Items: 1, 2", etc.). Marking an item stamps your
   initials and the date; clicking the same state again clears it.
4. Rows 3.7.1 – 3.7.5 are write-in rows for the equipment operation list,
   and 4.13 (early release) takes a Director name, approval and comments.
5. **Sign off each part** at the bottom of its tab — it warns you if items
   are still unmarked, exactly the check a senior engineer would do before
   signing the paper sheet.

### Buttons

| Button | What it does |
|---|---|
| **Export Excel** | Generates a real `.xlsx` workbook: a *Test Record* sheet mirroring the full form (colour-coded statuses, initials, dates, comments, sign-offs) and a *Summary* sheet with per-part counts and a snag list. |
| **Print** | Browser print view laid out like the paper form — use "Save as PDF" for a non-editable copy for the job file. |
| **Backup** | Saves the raw checklist state as a `.json` file (archive it with the job, or move a half-finished checklist to another PC). |
| **Open** | Loads a `.json` backup. |
| **New** | Clears the current checklist and starts fresh. |

Progress is **saved automatically in the browser** (localStorage), so a
half-finished inspection survives closing the laptop. It is per-browser,
per-machine — use Backup/Open to move between machines, and always Export or
Backup before clearing.

## Maintenance

- All checklist content lives in the `CHECKLIST` array near the top of the
  `<script>` block in `index.html`, transcribed 1:1 from QAP07_04_17
  (including original wording). If the controlled document is revised, edit
  the array and update `DOC_REF`.
- The Excel exporter is self-contained (no libraries) — it writes a minimal
  Open XML workbook directly, so the file has no dependencies to break.

## Ideas for later

- A master log: append one summary row per completed checklist to a shared
  workbook, to spot recurring snags across contracts.
- Central storage (shared folder or a small server) instead of per-browser
  saving, so any bench PC can pick up any job.
- Generated PDF test certificates, photo attachments against snag items,
  and per-panel history.
