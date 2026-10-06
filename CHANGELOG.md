# Changelog

Release notes for BoekSolutions.SheetSetEditor, in sync with `update.xml` and the version tags on this repo's [Releases](../../releases) page.

## v1.2.3 (2026-10-06)

- Fixed: new installations now retain their safe upgrade registration so later updates can install in place.
- Improved: the installer reports when safe upgrade registration cannot be confirmed after installation completes.

## v1.2.2 (2026-10-06)

- Improved: installation and uninstallation now consistently require administrator rights and install for all Windows users.
- Improved: uninstalling removes installed application and AutoCAD plug-in files while preserving additional personal files, app settings, and licence state.
- Improved: older per-user installations and installations with legacy folder cleanup require a one-time uninstall before upgrading. The installer explains how to protect personal files before removing the old version.
- Improved: English is the default for new installations, and dialogs, property editors, and the import wizard follow the selected interface language.
- Added: the AutoCAD 2027 ribbon now includes a BoekSolutions button to start the editor with `SSMBE`.
- Fixed: edits to empty custom properties are now saved correctly even when AutoCAD omitted their value from the sheet set.
- Fixed: relative drawing and sheet-storage paths are now resolved from the original sheet-set folder when opening a `.dst` file.

## v1.2.1 (2026-09-23)

- Improved: the Autodesk Marketplace name is now BoekSolutions Sheet Set Batch Editor, while existing executable names, settings, licences, and update links remain compatible.
- Improved: new installations request administrator rights for an all-users installation; existing per-user installations continue to update in their current mode.
- Improved: updates replace the complete AutoCAD plug-in bundle, and uninstalling removes the installed application and plug-in files while preserving user settings and licence state.
- Improved: the AutoCAD bundle now includes publisher, support, help, and upgrade metadata and targets AutoCAD 2027 only.
- Added: use `SSMBE` as the Marketplace command in AutoCAD; the existing `SSM_UI` command remains available as a compatibility alias.

## v1.2.0 (2026-09-15)

- Added: one-time licenses for one active computer, with no annual renewal or restriction to a specific AutoCAD version.
- Improved: activate and move a license through the personal link in your purchase email. A valid permanent license also works offline.
- Improved: existing registered licenses are converted automatically while keeping their original expiry date. Connect to the internet for the first start after this update; after conversion, a valid permanent license works offline.
- Security: license signatures are now checked without storing a license-creation secret in the app.

## v1.1.15 (2026-09-14)

- Fixed: changing a smart-field character limit now also shortens existing values after confirmation, including sheet-field defaults and values on sheets outside the current selection.
- Improved: before shortening values, the editor shows the affected fields and creates a backup. Saving checks the limits again, and different sheet values remain separate.
- Fixed: character limits are now also enforced when typing in sheet-set fields.
- Fixed: storage, cloud and backup errors are no longer all reported as a file being in use. That message is now reserved for actual file-lock errors.

## v1.1.14 (2026-08-31)

- Fixed: the sheet tree now keeps the same folders and sheet sets expanded or collapsed after an edit, instead of collapsing the entire tree.
- Fixed: sheets imported from DWG layouts are now saved with the complete AutoCAD sheet and layout-reference structure, preventing the sheet set from becoming unreadable after saving.
- Improved: imported layouts retain their DWG layout handle, so AutoCAD can reliably reconnect each sheet to the correct layout.
- Improved: number, date and translated status formatting now consistently follows the selected regional settings where appropriate.
- Fixed: invalid or unsupported DWG files are handled gracefully during layout inspection instead of interrupting the import flow.

## 1.1.13

- New: CSV import with the "Sheetset data only" scope now also updates sheet-field defaults
  (custom properties normally scoped per sheet, shown at the top sheet-set level) — without
  touching any individual sheet's own value.
- New: importing with the "All sheets" scope now shows a confirmation warning first, since it
  overwrites every mapped field on every targeted sheet.
- Improved: the separate "Apply" button is gone — "Save" now applies any pending property-panel
  edits and saves in one click, instead of requiring Apply first.
- Fixed: the Save button could stay disabled after a manual property edit, with no way to enable
  it now that the old Apply button (which used to do that) is gone.

## 1.1.12

- New: a button above the sheet tree collapses or expands every node in one click — useful for
  large revision-folder structures where you usually only need one subset open at a time.
- New: CSV import has a new scope option, "Sheetset data only (top level)" — updates
  sheetset-wide fields without touching any sheets, even if the same CSV file also has
  sheet-level columns filled in.
- Improved: the license window's "Buy license" button is now the primary action and links
  straight to the product page; the old e-mail request is now a small "Support" link for
  activation/purchase problems.

## 1.1.11

- Fixed: fields inside a Smart Field Group always displayed in alphabetical order, even after
  reordering them with the up/down buttons in the group editor. The order you set there is now
  respected, for both the inline-header and card layouts.

## 1.1.10

- Fixed: Smart Field Groups made up only of sheet-level fields could show up twice on the Sheet
  Set tab after first selecting a sheet, then clicking back to the sheet set (not reproducible
  by going through a subset first).
- Improved: Smart Field Group order is now set by dragging a group up/down in its list in
  Options, instead of typing a sort-order number per group.
- New: Options can now hide field rules and Smart Field Groups that don't belong to the
  currently open sheet set — useful if you work with multiple sheet sets that each use different
  custom fields. A rule only shows if every field it uses actually exists in the active sheet
  set. A toggle lets you show everything again.

## 1.1.9

- Fixed: importing a CSV/TXT file with field-link or formula rules configured could silently
  overwrite those fields on sheets that weren't even part of the import, with no warning shown.
- Fixed: a handful of actions (undoing an import, adding a sheet or subset, dropping a DWG onto
  the tree) could be started while a save was still in progress, risking a conflicting write.
- Fixed: a field-link rule could create a custom property on a sheet set that never actually
  defined it.
- Improved: several message texts that always showed in Dutch regardless of your language setting
  now respect your selected language.

## 1.1.8

- Improved: importing a CSV/TXT file now correctly detects encodings beyond Western European —
  Central European, Cyrillic, Greek and others are now read correctly instead of only ever being
  interpreted as Windows-1252.

## 1.1.7

- Fixed: importing a CSV/TXT file that wasn't UTF-8 encoded (common with exports from non-UTF-8
  systems, e.g. containing accented characters like Æ, é, ö) could fail with "No data is available
  for encoding 1252" instead of importing correctly.

## 1.1.6

- Fixed: closing the update dialog without clicking a button (the X button, Alt+F4, Escape) no
  longer silently postpones the update prompt for two days — you'll be asked again next launch.
- Security: license keys are now unique per Boek Solutions product, even on the same computer.
  If you have an existing license and it's no longer recognized after updating, this is expected —
  email info@boeksolutions.nl with your Machine ID for a replacement key, a one-time step.
- New: drag and drop a .dst or .xml file onto the main window to open it.

## 1.1.5

- Security: strengthened how license keys are generated and validated. If you have an existing
  license and it's no longer recognized after updating, this is expected — email
  info@boeksolutions.nl with your Machine ID for a replacement key, a one-time step.

## 1.1.4

- Fixed: the update download could fail with an error for anyone updating from 1.1.2 or earlier —
  the installer link had gone stale after a naming change on the release side.
- Fixed: Options > Info could claim "latest version installed" even when the update check itself
  had actually failed (for example due to a network problem) — it now says clearly that the check
  failed instead of falsely suggesting you're up to date.
- New: a "Check for updates" button in Options > Info, so you can check again right away instead of
  having to restart the app.

## 1.1.3

- New: sheet and field names with accented letters, Cyrillic, Greek, Hebrew, Arabic, CJK
  (Chinese/Japanese/Korean), Thai, Devanagari, Georgian, Armenian, and emoji now read and save
  correctly — previously these could show up as "*" or other garbled characters, and in some
  cases saving one could silently corrupt an unrelated field elsewhere in the same file.
- Fixed: renaming a sheet or subset via the right-click menu didn't immediately update the
  properties panel — clicking Apply right after could silently undo the fresh rename.
- Improved: clearer error messages — saving a file with a character that isn't supported yet now
  tells you exactly which one, instead of risking a corrupted file; opening a file AutoCAD wrote
  with such a character now explains what happened instead of suggesting the file is locked.

## 1.1.2

- Fixed: linking a sheet set's own fields (like Project Number) to each other never actually
  worked — that panel had no way to set up a field link at all until now.
- Fixed: linking a sheet set field to a sheet field (or vice versa) could silently do nothing,
  since a single sheet-set-wide value and a per-sheet value don't line up — the field-link picker
  now only offers matching fields, both inline and in Options.
- Fixed: when two fields were mirrored, only one side showed the green "linked" icon.
- New: right-click a field's link icon to clear its value directly, even without an active link —
  useful for date/choice fields that previously couldn't be emptied through the UI.
- Fixed: removing a field link left the old value behind instead of clearing it.
- Fixed: date fields were unreadable (black text) in Dark and Book theme.
- Fixed: switching themes while a date field had a value could silently clear it.
- Improved: the calendar picker for date fields now closes itself as soon as you pick a date.

## 1.1.1

- Fixed: app could crash on launch when a second instance was started while one was already
  running (single-instance detection released a lock it never owned).
- Fixed: Options window sidebar didn't pick up the Light/Book theme colors, always showing a
  plain near-white background regardless of theme.
- Improved: Options sidebar now has a subtle "book cover" shadow gradient in Light/Book themes.
- New: in-app update checking — the app can now notify you when a new version is available.

## 1.1.0 — baseline

First version tracked through this update channel. No changelog entries prior to this point are recorded here.
