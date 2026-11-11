# AnuPrayog: Tarang v2.21.0.0

A refinement release. It adds control over tick direction on every axis, the
exact width of fitted peaks, more choice in Data Labels and in the Live Data
watch folder, and safer maths text in graph labels.

## New

- **Major and Minor Tick Direction** (Axis Properties). Choose whether ticks
  point In, Out, or In & Out, separately for major and minor ticks. Each side
  of a graph keeps its own direction, visibility and length through restyling,
  replotting, and Save and reopen; ticks on the right and top no longer flip
  to pointing outward.
- **Peak deconvolution reports the exact FWHM for each peak** (Gaussian,
  Lorentzian and pseudo-Voigt), with its uncertainty from the fit. It appears
  in the peak table, the results text, the parameters sheet and Send to
  Project.
- **Data Label: show X and Y, X only, or Y only**, with editable X and Y unit
  boxes. A unit you type is used; otherwise the column's unit is filled in.
  Existing labels are unchanged.
- **Live Data > Watch Folder for New Files: include filters.** Read only files
  matching an exact name, a keyword or an extension. Exclusions still win. The
  watch dialogs can now be resized and scroll when small.
- **Insert Symbol: Spacing group.** Insert thin, medium, thick, word, quad or
  negative-thin gaps in maths text. Symbols that end in a letter are now
  inserted with a trailing space, so the next letter you type does not run
  into the command.
- **Style dialog shows where a curve comes from.** Double-click a curve to see
  its project, dataset, columns and Live Link state in a read-only Source
  section.
- **New columns ask for a name.** The popup is prefilled with `new1`, `new2`
  and so on; Cancel or an empty name keeps the default. Adding several columns
  at once gives them consecutive default names. Every new column is a Y
  column.

## Fixed

**Graph text**
- Maths text that cannot be parsed is refused when you press OK or Apply,
  instead of breaking the graph. If such text was already saved, it is drawn as
  plain text.
- A legend entry that is purely maths now uses the graph's default font.

**Columns**
- Adding a column can be undone.

## Help

Help pages for Axis Properties, Insert Symbol, Data Labels, Live Data, Style,
peak deconvolution and the Data Matrix describe the new features.
