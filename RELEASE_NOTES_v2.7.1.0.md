# AnuPrayog: Tarang v2.7.1.0

A maintenance release: 22 fixes and two new features, all arising from a
round of hands-on testing.

## New

**Compare Graphs Side by Side** (*Window* menu). Graphs are tabs, so
normally you see one at a time and comparing two means clicking back and
forth and trusting your memory. Tick the graphs you want and they are
laid out together — an automatic grid, a single row, or a single column —
with the option to hide the Data Matrix and give the whole width to the
plots. Every pane stays fully live. *Window > End Comparison* puts
everything back.

**Appearance Theme** (*Window* menu). Light or Dark chrome for windows,
panels, menus and dialogs, remembered between sessions. Both themes
**darken the scroll bars**, which were so pale against a worksheet of
white cells that the handle was hard to find at all. The theme
deliberately does not touch figures: a plot has to look the same in a
paper whatever theme its author was working in.

## Fixed

### Legends
- Text set in **Edit Legend** no longer reverts when Typography or Style
  is used for something else. The wording used to live in a side table on
  the axes, keyed by the artist's identity — so replacing an artist
  (restyling an error bar, converting Line to Scatter, recalculating)
  orphaned it, and any rebuild that did not know about that table wrote
  the old name back. Edit Legend now renames the curve itself, so every
  dialog reads the same field and no rebuild can undo it.
- An entry you hide stays hidden through restyles, reloads and rebuilds.

### Windows and layout
- **Renaming a graph no longer makes it uneditable.** Every canvas
  handler had captured the old name, so after a rename double-clicks and
  the Typography / Axis Properties / Style dialogs silently did nothing.
- **Maximize / restore no longer skews the panes.** Dock layouts are now
  remembered *per window state*: a maximized window and a restored one
  are two different splits, and replaying one into the other was the
  skew. The same fix covers minimise and restore.
- **Maximize now puts the graph in the centre**, instead of only hiding
  the Data Matrix and leaving the graph where it was.
- **Double-clicking a graph's title bar floats and re-docks it** — the
  standard gesture for a dock panel, and the way to bring a floating
  graph back. It used to maximize instead. Maximize keeps its own button,
  menu item and Ctrl+Shift+M.
- **A floating graph can be resized** and has a visible border: it gets
  the operating system's own window frame back.
- **The crash-recovery prompt appears after the splash screen closes**,
  never behind it. It could previously wedge startup completely.

### Worksheet and history
- **Dragging a column edge resizes the column.** The header's
  drag-to-plot was claiming those pixels and cancelling the resize a few
  pixels in.
- **Project History's Input and Output columns are resizable** and start
  wide enough to read a dataset or column name.

### Numeric input
- **Every numeric field keeps the number you type, at any magnitude.**
  Qt rounds a spin box's *stored* value to its displayed decimals, so
  anything below that precision — `1e-9` in a window bound, a small
  thickness, a tight tolerance — was destroyed on entry and read back as
  zero. Storage and display are now separate: boxes keep their tidy
  appearance and hold 1e-300 to 1e300 exactly.
- Ten inputs that hold values *from your data* had ranges that clamped
  real measurements (a t-test population mean capped at 99.99; a peak
  threshold floored at 0.01, unusable on nanoamp data). Controls that
  govern appearance keep their sensible limits.
- Data Matrix cells, free-text fields and Axis Properties tables were
  audited the same way.

### FFT
- **A windowed transform now reads the same amplitude as an un-windowed
  one.** No window correction was applied at all, so a Hann window
  halved the answer. (On a tone that falls between frequency bins the two
  still differ — there the *un-windowed* value is the misleading one.)
- **The window tapers smoothly to zero at both ends of its extent**, in
  every centring mode. Off-centre placement used to start at 90% of full
  height and drop straight to zero — a step in the signal, which spreads
  leakage across the whole spectrum.
- The **Advanced FFT** plugin gained a live preview of the window drawn
  over the data, and inputs for Gaussian sigma, Kaiser beta and
  exponential decay, which previously could not be reached at all.

### Plots
- **Tick labels thin out when they would collide** as a pane is made
  smaller, and come back when there is room. Ticks and values are
  unchanged; a tick you named yourself in Special Ticks takes priority.
- **Scientific and Engineering tick labels read as n × 10ᵐ**, not
  `1.23e-05`.
- **Four identical blank entries and a one-pixel marker** were removed
  from the marker picker.

## Compatibility

Projects saved with earlier versions open unchanged; legend text stored
under the old scheme is migrated on load. The installer removes previous
2.x builds, and offers to remove v1.0 and v1.2 if present.
